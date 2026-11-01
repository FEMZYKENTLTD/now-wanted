# Final Project — Knowledge Land College (KLC) Exam Portal

> File: `08-Final-Project/README.md`
> Status: **IMPLEMENTED.** The final database-backed software project is the **Knowledge
> Land College (KLC) CBT Suite v1.0** (the "KLC Exam Portal"), developed in the repository
> `FEMZYKENTLTD/klc-exam-portal`. Technical claims below are grounded in that repository's
> source code, build configuration, documentation and commit history. This document replaces
> the earlier *"Database-Backed WhatsApp AI Service Management System"* planning direction;
> that direction was a placeholder and is no longer treated as the final project.

## Purpose

The school expects that by the end of SIWES the student is capable of building a
**full-scale software application that solves a real problem and includes a database**. The
KLC Exam Portal is that project: a computer-based testing (CBT) suite for Nigerian secondary
schools that replaces paper examinations with a digital examination-management system backed
by a relational database.

## Problem statement

Paper examinations are expensive to print, easy to leak and slow to mark; exam malpractice
(copying, impersonation, phone cheating) undermines results; and manual marking delays
report cards. The portal addresses this by digitising question management, examination
delivery, proctoring, automatic grading and result processing, with data persisted in a
database and accessible offline.

## Users and roles (implemented)

- **Super Admin** — full override; seeded securely from configuration on first boot.
- **Principal Admin / Exam Officer** — school settings, exam scheduling, question approval.
- **Teacher** — uploads and manages questions for their assigned subjects.
- **Student** — registers, takes scheduled exams and views results.
- **Parent** — registers with a family code and views a ward's published results read-only.

## Objectives (implemented)

- Store and manage users, subjects, classes, questions, exams, attempts and results in a
  relational database.
- Deliver scheduled examinations with a question navigator, timer, autosave and auto-submit.
- Detect malpractice (focus-loss strikes, copy/paste blocking) and log it.
- Grade examinations automatically and generate results, report cards and analytics.
- Work offline (H2 cache) and synchronise to the cloud (Supabase PostgreSQL) when online.
- Protect access with role-based controls, BCrypt password hashing, registration-code gates
  and encrypted local storage.

## Architecture

- **Application:** Java 17 desktop application with a JavaFX 21 user interface (42 FXML
  screens), built with Maven and packaged as a runnable JAR plus a zero-JDK Windows bundle.
- **Database:** Supabase **PostgreSQL** (cloud) with an **H2** local cache as the offline
  fallback; a 33-table schema initialised by the application and a 5-file SQL migration
  chain (see `database/schema-plan.md`).
- **Access layer:** JDBC with prepared statements throughout.
- **Web tools:** a static `klc-web-admin` portal (parent result checker, invigilator live
  room, teacher question upload) over Supabase REST (PostgREST) functions.
- **Synchronisation:** an offline→cloud sync service replays queued answers when the network
  returns.

## Technology stack (from the repository)

Java 17 · JavaFX 21 · Maven · Supabase PostgreSQL · H2 · JDBC · BCrypt · TOTP (2FA) ·
AES-encrypted H2 cache · PDFBox · Apache POI · iText · ZXing (QR) · JUnit 5 (66 test
methods across 12 test classes) · GitHub Actions CI.

## Functional scope (implemented — representative)

- Question bank: MCQ (A–E), True/False, image and LaTeX items; PDF/DOCX/TXT/CSV import;
  topic/difficulty tagging; an approval workflow before questions go live.
- Exam engine: scheduling, attempt limits, variant shuffling, negative marking, 30-second
  autosave, timer warnings and auto-submit; practice and mock modes that are never recorded
  officially.
- Proctoring: 3-strike focus-loss detection with auto-submit and lockout, copy/paste and
  right-click blocking, and malpractice logging.
- Results: automatic grading with per-topic breakdown, CA aggregation, class positions,
  report cards, broadsheets, transcripts and QR-verified result slips.
- Security: BCrypt hashing, 5-strike/15-minute lockout, role-based access, registration-code
  gates that fail closed, AES encryption at rest for the local cache, and an append-only
  (WORM) audit trail in the cloud.

## Testing and verification

- A JUnit 5 automated test suite (60+ test methods) covers authentication, grading, exam
  scoring, schema integrity, AES cache encryption, arm balancing, the exam calendar and
  backup/restore.
- A GitHub Actions workflow compiles the project, runs the tests and applies the database
  migration chain on every push; version tags build the zero-JDK Windows bundle.

## Documented progression (Weeks 25–28)

| Phase | Content |
|---|---|
| Week 25 | Problem definition and requirements for a database-backed software project (logbook). |
| Week 26 | KLC architecture, database (Supabase PostgreSQL + H2) and core examination functionality. |
| Week 27 | Feature audit, security hardening, automated tests and continuous build (version 1.0). |
| Week 28 | Final testing, documentation, feature verification and SIWES close. |

## Evidence

- Repository source, build configuration and migrations: `FEMZYKENTLTD/klc-exam-portal`.
- Commit history (including the student's own commits as `OLUFEMI BENUA KERIPE`).
- Engineering reports: `AUDIT_REPORT.md`, `docs/FEATURE-MATRIX.md`,
  `docs/SCHEMA-INVENTORY.md`, `docs/VERIFICATION-REPORT-*.md`, `ACCEPTANCE-STATUS.md`.
- Interface/code screenshots to be included in the final submission bundle (optional
  supporting evidence; the public repository is itself the primary evidence).

## Honest boundaries (not overclaimed)

- Desktop visual flows (e.g. dark theme rendering) are compiled and wired; a pixel-level
  check requires a Windows desktop run.
- Windows 7/8 and x86 builds require an external legacy build environment (documented in the
  repository), not the shipped Windows 10/11 x64 bundle.
- The cloud migration job in CI was externally blocked by placeholder database secrets; the
  schema itself was validated by a local PostgreSQL CI gate.

## Status

- Implemented and versioned at **v1.0.0** in the KLC repository; further refinement is
  possible but the application is complete for the purposes of this SIWES project.
