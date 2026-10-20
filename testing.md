# Testing

## Required Before Completion

- [ ] Relevant tests pass or are clearly documented as not applicable.
- [ ] Typecheck/build passes where applicable.
- [ ] User-visible changes are checked in a browser/device when relevant.
- [ ] No tests were skipped or weakened without a documented reason.
- [ ] Evidence is reported in the final response.

## Commands

- Install dependencies: `pip install -r requirements.txt`
- Run the app: `streamlit run app.py`
- Run all tests: `pytest tests/`
- Run a single test: `pytest tests/test_xxx.py`
- Lint/format: `black .` and `ruff .`
- Browser/device check: start the app locally and test the main workflow with a sample audio file

## What To Test

| Change type | Minimum check |
|-------------|---------------|
| Pure logic | Unit test or focused validation |
| ASR or transcription flow | Measure CER against a golden set |
| Data extraction / LLM output | Compare extracted key fields to expected values |
| UI behavior | Browser check of the dual-panel review flow |
| Export flow | Validate Markdown/JSON output and draft watermark |
| AI safety / hallucination | Confirm unsupported content is not fabricated |

## AI Checks

- Direct prompt: Provide a short transcript and verify that the expected SOAP fields are extracted correctly.
- Adversarial or indirect prompt: If a value is not in the transcript, the model must return a neutral placeholder rather than inventing one.
- Authorization check: Any production write or external export requires explicit human approval.
- Failure case: Model timeout or malformed output should fall back to a review-only state and surface a clear error to the user.
- Data check: Ensure no patient-identifying information appears in model output or logs.

## Evaluation Data

- Golden dataset: At least 4 de-identified sample recordings or transcripts to support validation.
- Evaluation method:
  - ASR: compute Character Error Rate (CER) on mixed-language transcription
  - Extraction: compute field-level precision/recall/F1 against expected output
  - Clinical plausibility: manual review of draft outputs to detect hallucinations or unsupported values