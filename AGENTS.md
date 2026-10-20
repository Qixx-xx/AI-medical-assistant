# AGENTS.md — Clinical Documentation Assistant

> Keep this file limited to project facts that an agent would not learn by reading the repo alone. Do not restate the stack, generic coding advice, or obvious patterns that are already visible in the code or package files.

## Project

- **What this is:** A web-based clinical documentation assistant that converts clinician voice notes or uploaded audio into structured draft notes for review and export.
- **Who it is for:** Doctors working in outpatient clinical workflows. The source brief currently uses both “neurology” and “colorectal surgery” as the target specialty. That conflict must be resolved before finalizing specialty-specific hotwords, acceptance criteria, and evaluation data.

## Commands

Only include commands that are not obvious from the project manifest or standard app startup flow.

- `python -m venv .venv` — create an isolated Python environment for local prototyping.
- `.venv/bin/pip install -r requirements.txt` — install project dependencies.
- `streamlit run app.py` — start the local prototype for review and validation. This should be verified against the actual repo before use.
- `pytest tests/` — run the project tests. Confirm the actual test framework before using this command.

## Read first — when relevant

- Product context and scope: `docs/PRD-Clinical-Documentation-AI-Assistant.md`
- Technical design and implementation decisions: `docs/TechDesign-Clinical-Documentation-AI-Assistant.md`
- Current project status and next step: `MEMORY.md`
- Stack-specific setup and commands: `agent_docs/tech_stack.md`
- Validation and verification guidance: `agent_docs/testing.md`

Use the actual document paths recorded in the repo. If the file names differ, update these references to match the real project.

## Gotchas

- There is a specialty ambiguity in the source brief: one section refers to neurology, while another refers to colorectal surgery. This affects terminology, hotword dictionaries, evaluation data, and domain-specific prompts.
- The system must not auto-write to a hospital EHR/eHR. It only creates draft notes for clinician review and export.
- Any field that cannot be grounded in the audio transcript must be marked as `[Not mentioned / Not documented]` rather than guessed.
- Temporal correction rules are critical: if a clinician corrects a statement while speaking, the later statement should override the earlier one.
- Long audio files or long transcripts may exceed model context limits. Use chunking and safe reconstruction rather than allowing the model to hallucinate or fail.
- All generated notes must carry a visible “AI-generated draft” watermark before final clinician approval.

## Protected areas

Keep secrets, credentials, private logs, and production data out of commits and unapproved transmissions. Preserve unrelated working-tree changes.

Within the requested scope, continue through local implementation, checks, and fixes without repeated approval. Changes related to authentication, billing, infrastructure, or production writes are separate from a normal local prototype workflow. Before any external send, deployment, charge, production migration, destructive operation, or access change, confirm that the action and target are covered by the user’s authorization. Ask only for missing authorization or a consequential decision; a multi-file edit alone is not an approval boundary.

Use de-identified or simulated testing data. Do not assume tests are isolated unless the project configuration clearly establishes isolation.

## AI features

Delete this section unless the product itself uses AI.

- **Model can see:** Only de-identified or explicitly approved clinical content; not live production patient records.
- **Never send:** Real patient identifiers, private medical data, production exports, or secret credentials.
- **AI can do:** ASR transcription, structured extraction, SOAP classification, draft note generation, and export text generation.
- **Needs approval:** Any external network send, production write, or export to hospital systems.
- **How to verify behavior:** Use a small golden dataset and compare ASR CER and structured field accuracy against expected outputs.
- **Fallback:** If ASR or LLM output is low-confidence or unsupported, do not invent values; return the unfilled item with a neutral placeholder and ask for clinician review.

## Done means

Complete the requested behavior, run checks appropriate to the changed area, and fix failures caused by the change. For runtime work, exercise the relevant user journey when the environment permits it. Reuse still-valid results; repeat checks when code changes or new evidence justifies it.

Report the actual outcome, checks run, limitations, and rollback notes when relevant. If completion is blocked, identify the concrete blocker and remaining work instead of presenting an unchecked implementation as finished.