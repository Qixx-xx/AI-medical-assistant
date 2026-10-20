# Project Brief

## Product

- One-line vision: Reduce clinical documentation effort by converting clinician voice notes into structured draft records for outpatient review and export.
- Target users: Clinical doctors in outpatient settings. The product currently references both neurology and colorectal surgery and requires one final specialty decision.
- Primary user outcome: Produce a structured, clinician-reviewable draft SOAP note or clinic summary in seconds, with minimal manual editing.

## Scope

- Must ship:
  - Web-based single-user voice recording or local audio upload
  - Mixed-language ASR for Cantonese + English + medical shorthand
  - LLM-driven extraction into SOAP-style clinical fields
  - Dual-panel review UI with editable structured output
  - One-click export to Markdown or JSON
  - Draft watermark and explicit no-write-to-EHR safety boundary
- Not in v1:
  - Direct auto-write to hospital EHR/eHR systems
  - Device-level integration with hardware systems
  - Surgical record or complex multi-specialty hospital workflows

## Principles

- Solve the primary user story before adding optional polish.
- Prefer boring, understandable, and maintainable solutions.
- Keep generated documentation short, current, and reviewable.
- Verify user-visible improvements in the actual workflow.
- Do not invent missing clinical facts.

## AI Position

- AI is used for: ASR transcription, clinical information extraction, draft generation, and structured field mapping.
- AI is not used for: direct clinical sign-off, auto-archival, or direct writes to hospital core systems.
- Human approval required for: any external export, production write, or clinically sensitive finalization flow.