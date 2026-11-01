# 4000 YEARS LTD — Company (SIWES) Repositories & Technical Environment

> File: `02-Organization/company-repositories.md`
> Status: Initial evidence-based review (performed 2026-09-07 by the documentation agent,
> browsing the public Bitbucket pages). This file is **context/evidence only** — it does
> NOT by itself attribute work to the student. See "Attribution rules" below.

## Purpose & security

These Bitbucket repositories belong to the **SIWES / company-work context** — separate from
the student's pre-SIWES personal projects (see `01-Student-Information/student-profile.md`
and `AGENTS.md` §9). They help reconstruct the real SIWES technical environment: languages,
frameworks, project structure, WhatsApp integration, backend architecture, database usage,
configuration, and progression.

**Security:** No credentials are embedded in any clone command. If authenticated access is
ever needed, request the *connection/access type* needed rather than asking for passwords,
access tokens or private credentials to be pasted into documentation.

> **Note on access method:** The sandbox's git/curl clients could not reach Bitbucket's git
> endpoint (network/TLS blocked), but the public web pages were browsable and confirmed each
> repo's access level is **Read** (public). Findings below come from those public pages.

## Repository catalog

### 1. wole.api.services
- URL: https://bitbucket.org/4000-years-ltd/wole.api.services.git
- Web: https://bitbucket.org/4000-years-ltd/wole.api.services/
- Default branch: `master` · Branches: 15 · Open PRs: 2 · Watchers: 2 · Forks: 0 · Access: Read
- Repo "Last updated": 2026-05-20
- Observed structure (root, branch `master`): a **multi-project .NET solution**
  (`Wole.Api.services.sln`, `global.json`) with projects: `Wole.Api.services`,
  `Wole.Commons`, `Wole.DTOs`, `Wole.Datastore`, `Wole.Models`, `Wole.Services`,
  `Wole.Utilities`, `Wole.WalletServer`, `Wole.WalletServices`; plus `Dockerfile`,
  `.dockerignore`, `.gitignore`, `.gitattributes`, `qodana.yaml`,
  `PULL_REQUEST_TEMPLATE.md`, `global.json`, `_logs-uifile.txt`.
- **Observed commit author on `master`:** EMMANUEL HARRY (e.g. merge `a8d1faa`, 2024-05-25).
- **Attribution:** **Pre-existing organizational code** authored by other developers
  (master history shows commits by EMMANUEL HARRY dated 2024, before this SIWES). The
  student read and studied this codebase as part of training (Weeks 4, 10–11); the student
  did not author it.
- Interpretation for Log Book (only if later confirmed): .NET/C# backend + wallet/services
  API environment, containerized (Docker), multi-project architecture.

### 2. whatsapptestbot
- URL: https://bitbucket.org/4000-years-ltd/whatsapptestbot.git
- Web: https://bitbucket.org/4000-years-ltd/whatsapptestbot/
- Default branch: `main` · Branches: 1 · Open PRs: 0 · Watchers: 2 · Forks: 0 · Access: Read
- "Last updated": 2026-01-26
- Observed content: effectively **empty** — only a `.gitignore` (Initial commit `453f0f4`,
  2026-01-26). No source files, no README, no pipelines configured.
- **Attribution:** N/A — no substantive content to attribute; the initial commit
  (2026-01-26) precedes SIWES.
- Interpretation: provides essentially **no technical content**; do not use it to support
  Log Book activity claims.

### 3. advanced_wa_bot
- URL: https://bitbucket.org/4000-years-ltd/advanced_wa_bot.git
- Web: https://bitbucket.org/4000-years-ltd/advanced_wa_bot/
- Default branch: `main` · Branches: 1 · Open PRs: 0 · Watchers: 2 · Forks: 0 · Access: Read
- Language: **C#** · "Last updated": 2026-04-16 (repo header also showed "2 hours ago",
  i.e. active)
- README: "Airline Scraping WhatsApp Bot — A C# WhatsApp bot for airline scraping and
  flight information." Features: WhatsApp integration, flight price scraping, Azure OpenAI
  integration, product catalog management. Technologies (README): .NET/C#, Azure OpenAI,
  WhatsApp Business API, Entity Framework Core.
- Root files/dirs: `WhatsAppBot/` (app project), `WhatsAppBot.sln`, `.env.example`,
  `.gitignore`, `.dockerignore`, `README.md`.
- Commit history observed (authored by the student — see attribution below):
  - `6489fc0` 2026-04-10 "Initial commit - WhatsApp Bot"
  - `1e8f5b4` 2026-04-10 "Add README"
  - `f56b3fe` / `f52164c` 2026-04-16 "feat: Master update - Full enterprise travel bot with
    RAG AI, bookings, cancellations"
  - The 2026-04-16 diff shows a `WhatsAppWebhookController`, airline scrapers
    (`ScrapingOptions`, per-airline targets), session handling, plus a newly added media
    layer: `IImageGenerationService` / `ImageGenerationService` using **Azure OpenAI
    `gpt-image-1` (fallback `dall-e-2`)**, and image/voice/vision services registered in
    `Program.cs`; `/image` and `/generate` commands.
- **Attribution:** branch `main` updated by **KERIPE OLUFEMI BENUA** (the student),
  2026-04-16 (commit `f52164c`); gravatar initials KB. Commits dated 2026-04-10 to
  2026-04-16 fall **within** the SIWES period (started 2 March 2026).
- **Status:** **CONFIRMED** — the student authored and developed `advanced_wa_bot` during
  SIWES (Weeks 6–8+); features documented in the Log Book (WhatsApp webhook handling, Azure
  OpenAI/RAG integration, image generation, airline scraping, session handling) correspond
  to the committed code.

### 4. Organization Bitbucket workspace
- URL: https://bitbucket.org/4000-years-ltd/workspace/overview/
- Role: the 4000 YEARS LTD Bitbucket workspace containing the three repositories above.
- Status: **Verified** via per-repository public pages.

## Summary of observed attribution (as of 2026-09-07)

| Repo | Observed author(s) / dates | Attribution status |
|---|---|---|
| wole.api.services | EMMANUEL HARRY, 2024 (master) | `[UNCONFIRMED — pre-existing org code; student contribution not established]` |
| whatsapptestbot | Initial commit, 2026-01-26 | `[No substantive content; pre-SIWES]` |
| advanced_wa_bot | **KERIPE OLUFEMI BENUA**, 2026-04-10 → 2026-04-16 | **CONFIRMED AUTHOR** — student authored/developed the project; dated commits under their name are supporting evidence |

## Attribution rules (apply before any Log Book writing)

Distinguish carefully (per AGENTS.md §9): (1) work confirmed as the student's own;
(2) work contributed to; (3) work tested; (4) work being learned from; (5) existing
organizational code; (6) code written by other people; (7) things that cannot be attributed
to the student without confirmation.

**Do NOT generate Log Book entries from these repositories until the student confirms what
can be attributed.** The repositories support the SIWES technical narrative; they do not
override the student's actual first-hand account.

## Status markers used
- `[CONFIRMED ...]` — supported by observed evidence + student confirmation where required.
- `[UNCONFIRMED ...]` — present in the repo but student attribution not yet established.
- `[N/A ...]` — no content/attribution relevant.
