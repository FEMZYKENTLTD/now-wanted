# Final Project — Database Schema (KLC Exam Portal)

> File: `08-Final-Project/database/schema-plan.md`
> Status: **IMPLEMENTED.** This documents the database of the **Knowledge Land College (KLC)
> CBT Suite** (repo `FEMZYKENTLTD/klc-exam-portal`). The authoritative per-table inventory
> (33 application tables with primary keys, foreign keys and constraints) is
> `docs/SCHEMA-INVENTORY.md` in that repository. This file summarises the schema for the
> SIWES Log Book's database diagram.

## Two engines, one design

- **Cloud:** Supabase **PostgreSQL**, applied through a 5-file idempotent migration chain
  (`klc_supabase_schema.sql` → `v6_2` → `v6_3_final` → `v1_0_social` →
  `v1_1_security_and_features.sql`).
- **Offline:** an **H2** cache (PostgreSQL compatibility mode) initialised by the
  application so exams continue without internet; answers replay to the cloud via the sync
  queue when connectivity returns.
- **Total:** 33 application tables — 28 created by the desktop application and 5 cloud-only
  tables (`announcement_reads`, `id_cards`, `question_attachments`, `question_versions`,
  `teacher_imports`).

## Tables by domain

| Domain | Tables |
|---|---|
| Identity & roles | `users`, `student_profiles`, `parent_profiles`, `teacher_subjects`, `user_profiles` |
| Academic structure | `school_profile`, `school_classes`, `subjects`, `formula_sheets` |
| Question bank | `questions`, `question_options`, `question_attachments` ☁️, `question_versions` ☁️, `teacher_imports` ☁️ |
| Exam engine | `exams`, `exam_questions`, `exam_attempts`, `attempt_answers` |
| Results & assessment | `results`, `ca_scores`, `result_pins`, `result_appeals`, `fees_ledger`, `id_cards` ☁️ |
| Community & communication | `announcements`, `announcement_reads` ☁️, `study_materials`, `messages`, `friendships`, `notification_queue` |
| Operations, audit & sync | `audit_logs`, `backup_logs`, `sync_queue` |

> ☁️ = cloud (Supabase) only.

## Key relationships

- `users` 1—N `student_profiles` / `parent_profiles` / `teacher_subjects` (role-specific
  identity, ward linking and teacher subject ownership).
- `subjects` 1—N `questions` 1—N `question_options` (the question bank and its A–E answer
  options with the correct-answer flag).
- `exams` (subject/class/arm/term/session) N—N `questions` via `exam_questions`.
- `exam_attempts` (student + exam) 1—N `attempt_answers` (per-question selections).
- `results` links `exam_attempts`, `students` and `exams`; `ca_scores` links students and
  subjects for continuous assessment.
- `school_classes` references a class teacher; `messages`/`friendships` connect users.

## Business rules enforced in the database

- UNIQUE keys on `email`, `admission_no`, `result_pin`, `subject_code`, question options and
  exam-question pairings.
- A role CHECK constraint on `users.role` (SUPER_ADMIN, PRINCIPAL_ADMIN, EXAM_OFFICER,
  TEACHER, STUDENT, PARENT).
- Practice and mock attempts are excluded from official results through query filters and
  the `v_official_exams` view, so they never count toward positions or report cards.
- `audit_logs` is append-only (WORM trigger in the cloud) and Row Level Security restricts
  web (anon) access.

## Diagram guidance (Log Book)

The Week 26 sketch should show the core tables and their relationships:
**users → student_profiles / teacher_subjects → subjects → questions → question_options,
and exams → exam_questions ↔ questions, with exam_attempts → attempt_answers → results.**
