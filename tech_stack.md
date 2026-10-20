# Tech Stack

Last verified: 2026-10-15

## Stack

| Area | Choice | Notes |
|------|--------|-------|
| Frontend | Python + Streamlit (prototype) | Quick way to build a dual-panel review/editor interface for clinician feedback. |
| ASR | Multilingual ASR engine with a specialty dictionary | Needs support for mixed Cantonese/English and medical abbreviations such as TIA, NIHSS, MRI. Exact provider/model TBD. |
| LLM / Extraction | Structured-output model (exact provider TBD) | Must support strict JSON outputs and clinical guardrails. |
| Database | Local session cache only, or JSON/SQLite during prototype | No direct production storage or hospital database writes. |
| Auth | Not required for MVP unless hospital policy requires it | Keep the prototype simple and compliant until the deployment path is approved. |
| Styling | Streamlit native UI and minimal custom CSS | Prioritizes fast iteration and clinician usability. |
| Deployment | Local/private deployment preferred | Compliant with healthcare privacy expectations; cloud deployment needs explicit approval. |

## Commands

- Environment setup (proposed): `python -m venv .venv`
- Install dependencies (proposed): `.venv/bin/pip install -r requirements.txt`
- Run app (proposed): `streamlit run app.py`
- Run tests (proposed): `pytest tests/`
- Lint/format (proposed): `black .` and `ruff .`
- Browser verification: open the local app in a browser and test a representative audio sample

These commands are examples only and must be verified against the actual repo structure.

## AI Runtime

- Provider/runtime: TBD
- Model can see:
  - Public: Yes, if using public benchmark or mock data
  - User-owned: Only de-identified or explicitly approved clinic data
  - Never send: Real patient identifiers, production data, or any secret credentials
- Tools/actions: ASR and LLM-based extraction; no destructive or production-write actions
- Approval gates: Any export to an external system, production system, or hospital network requires explicit human approval
- Retention/training setting to verify: The chosen provider’s retention and training policy must be reviewed before production use
- Fallback: If the AI output is low confidence, switch to a conservative review-only path rather than auto-filling clinical content

## Important Patterns

- Data fetching: Perform transcription and preprocessing before extraction; apply dictionary corrections to medical terms and abbreviation mapping.
- State management: Keep per-session state in local memory or a lightweight local cache for review history and reprocessing.
- Forms/validation: Enforce required-field checks and unsafe-value guardrails at the boundary.
- Error handling: Return a clear clinician-visible message if the model is uncertain or unsupported.
- Logging/monitoring: Keep logs de-identified and do not leak patient information in traces or output.