# Review Checklist

Do not mark work complete until the relevant checks are actually passed or explicitly explained as not applicable.

## Basic Checks

- [ ] The diff stays focused on the requested task and does not include unrelated rework.
- [ ] No secrets, tokens, private logs, or production exports were exposed.
- [ ] The relevant tests, type checks, or build commands were run, or the failure reason is documented.
- [ ] UI changes were manually checked in a browser/device where applicable.
- [ ] Progress and blockers are reflected in `MEMORY.md`.

## Functional Acceptance

- [ ] ASR accuracy in mixed Cantonese/English/medical-abbreviation contexts is measured and meets the target (CER ≤ 15%).
- [ ] Structured extraction quality meets project goals (key domain fields accuracy ≥ 85%).
- [ ] Response latency for a 1–3 minute audio note remains within the target for end-to-end draft generation.
- [ ] The UI supports clinician correction without excessive friction and supports a clear review flow.
- [ ] Exported Markdown/JSON is valid, readable, and includes a draft watermark.

## Security

- [ ] Dependencies were checked for critical or high-severity issues.
- [ ] User input is validated at the system boundary.
- [ ] No real patient data was sent externally without explicit approval.
- [ ] Export and external-send actions remain inside the project’s approved boundaries.

## AI Checks

- [ ] The model-visible data boundaries are documented.
- [ ] Output does not invent unsupported clinical values; unsupported fields are marked clearly.
- [ ] The prompt and structured-output schema were tested against realistic sample inputs.
- [ ] Failure cases (timeout, low confidence, malformed output) are handled explicitly.
- [ ] Logs and traces do not reveal private or sensitive information.

## Final Evidence

The final response should include:

- Files changed
- Commands run
- Test/build/browser results
- AI/tooling evaluation results, if applicable
- Remaining risks and known blockers