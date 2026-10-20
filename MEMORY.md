# Memory

Update this file after major decisions, completed phases, or newly discovered project blockers. Keep it brief.

## Current State

- Current task: Draft the project setup files and record key decisions, scope constraints, and unresolved issues.
- Current phase: Project setup / documentation
- Next step: Save these files in the repo, open the project in the chosen coding assistant, and validate the local environment with the smallest startup command.
- Blocked by: Final confirmation of the clinical specialty (neurology vs colorectal surgery), and confirmation of the actual PRD and Tech Design file paths.

## Decisions

- [2026-10-15] Chose a prototype-first approach using a Python/Streamlit web app for the clinical documentation workflow.
- [2026-10-15] Kept the project within the non-production boundary: no direct EHR/eHR write, only clinician-reviewed draft export.
- [2026-10-15] Retained the requirement to add an “AI-generated Draft” watermark before final approval and export.

## AI / Tooling Decisions

- [2026-10-15] ASR direction: multilingual transcription with support for mixed Cantonese/English and medical abbreviations, using a specialty hotword dictionary.
- [2026-10-15] LLM direction: structured output with SOAP extraction and hallucination guardrails; exact model/provider TBD.
- [2026-10-15] Deployment direction: local/private deployment preferred for compliance; cloud deployment requires explicit approval and policy review.

## Known Issues

- Specialty ambiguity: the proposal contains both “neurology” and “colorectal surgery.” This must be reconciled before finalizing hotwords, acceptance criteria, and training/test data.
- Commands in this document are examples only and must be verified against the actual repo structure before use.
- Validation datasets and technical implementation details are not yet available in the repo; they should be added only when the PRD and Tech Design are present.

## Completed

- [x] Setup file drafting complete
- [x] Open decisions captured
- [x] Safety boundary and draft-only export rules recorded
- [ ] Local environment startup verified
- [ ] Golden dataset added and validated
- [ ] Final technical stack and model/provider confirmed