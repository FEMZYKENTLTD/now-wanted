# 4000 YEARS LTD — Workflow & Technical Environment

> File: `02-Organization/workflow-evidence.md`
> Status: **Verified (2026-10-09).** Technologies and workflow described below are
> consistent with the public Bitbucket repositories and with the student's verified
> Log Book entries.

## Technical environment (verified from repositories and placement)

- **Languages / frameworks:** C# / .NET for backend services and WhatsApp integrations;
  Java 17 / JavaFX for desktop applications developed by the student.
- **Architecture:** Multi-project .NET solutions; REST API controllers; webhook-based
  message handling; layered structure (controllers / services / data access).
- **APIs / integrations:** WhatsApp Business API; Azure OpenAI (chat completions,
  embeddings/RAG, `gpt-image-1` / `dall-e-2` image generation, voice/vision services);
  external airline/flight information via API calls and scraping.
- **Data:** Entity Framework Core; relational databases (PostgreSQL for cloud; H2 / SQLite
  for offline/embedded contexts).
- **AI-assisted workflow:** Azure OpenAI used for coding assistance, research and
  RAG-grounded replies; all AI output reviewed by the developer before being committed.
- **Version control:** Git with Bitbucket for organizational repositories and GitHub for
  the student's personal projects; branches, commits and pull requests.
- **Containerization:** Docker used for service deployment in the organization's
  `wole.api.services` solution.
- **Tools:** Visual Studio / VS Code; Postman for API testing; Swagger/OpenAPI for API
  documentation; Maven for Java builds; GitHub Actions for CI.

## Workflow (verified from the student's training experience)

1. Project briefs are received and requirements discussed with the supervisor.
2. Tasks are broken down into technical work items.
3. Development takes place in feature branches, with regular commits.
4. Code is built, run and tested locally; errors are diagnosed from compiler output and
   logs.
5. Corrections are made, related files are re-checked and the project is rebuilt to
   confirm clean builds.
6. AI tools (Azure OpenAI) are used to assist research and drafting; output is reviewed
   and corrected by the developer.
7. Completed work is committed with descriptive messages and prepared for review.
8. Final review/integration happens before delivery.

## Items not included (non-public business information)

Client names, revenue, project pricing, internal team sizes, proprietary deployment
targets and internal policies are private business details and are not claimed in the
Log Book. The Log Book describes the student's own work, learning and technical
observations, which are fully supported by the repository evidence.
