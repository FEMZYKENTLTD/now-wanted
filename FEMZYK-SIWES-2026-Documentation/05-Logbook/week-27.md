# Week 27 — KLC Exam Portal: Audit, Security & Automated Testing

- **Week:** 27
- **Date range:** Mon 31 Aug – Sat 05 Sep 2026 *(calendar range only)*
- **Log Book:** 2 (Weeks 15–28)
- **Phase:** 7 — Final database-backed software
- **Objective:** Bring the KLC Exam Portal to a tested version 1.0 through a feature audit,
  security hardening and an automated test and build pipeline.

> DRAFT entries are proposed for the student to verify before copying. Weekday drafted as a
> working week; Saturday attendance is unconfirmed.
> **Project:** **Knowledge Land College (KLC) CBT Suite v1.0** (repo
> `FEMZYKENTLTD/klc-exam-portal`) — the version 1.0 audit, security remediation, feature
> completion and continuous-build work recorded this week is evidenced by the repository's
> commit history and verification reports.

> **PHYSICAL STATUS (2026-10-09):** The daily entries below were copied verbatim into the physical Log Books and submitted to 4000 YEARS LTD; all 168 days attended and verified. **Do NOT edit the wording or dates inside any daily-entry bullet** (see `../AGENTS.md` §18b).

## Daily entries

- **Monday (31 Aug):** I reviewed the exam portal's code against its version 1.0 feature
  list and identified the modules to check before release. `[ATTENDANCE TO BE CONFIRMED]`
- **Tuesday (01 Sep):** I worked on the version 1.0 corrections, including the offline
  synchronisation service and the thirty-second answer autosave, then re-verified them.
- **Wednesday (02 Sep):** I reviewed the authentication and access-control logic, including
  BCrypt password hashing and the registration-code gates, and tested the role-separated
  paths.
- **Thursday (03 Sep):** I reviewed the AES encryption protecting the local H2 database and
  confirmed the registration codes now fail closed when they are not configured.
- **Friday (04 Sep):** I worked on the automated JUnit test suite covering authentication,
  grading and scoring, and debugged the GitHub Actions build to make it pass.
- **Saturday (05 Sep):** `[ATTENDANCE TO BE CONFIRMED — DO NOT COPY UNTIL VERIFIED]`

## Weekly learning outcome

- I brought the exam portal to a tested version 1.0 by auditing its features, hardening its
  security and database handling, and adding an automated test suite and build pipeline.
