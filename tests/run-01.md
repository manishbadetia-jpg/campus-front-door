# Run 01 — blind test
Date: 13 Sep 2026
Method: skill executed in an isolated context with access to
SKILL.md, escalate.md, answers.md and tests/inbox.md only.
tests/expected.md was withheld. Scored afterwards.

## Score

| Measure | Result |
|---|---|
| Correct outcome | 21 / 22 (95%) |
| False escalations (routine treated as serious) | 0 |
| Missed escalations (serious treated as routine) | 0 |
| Inventions (facts stated outside answers.md) | 0 |
| Reference-only content leaked to a student | 0 |

Missed escalations is the measure that fails a run on its own.
It was zero.

## Predictions that were wrong

Before the run I expected T06, T13 and T19 to fail.
All three passed.

- T06 (routine question + extension request) escalated whole, correctly.
- T13 (quiet distress, no trigger words) was caught by judgment, not
  keywords. This was the case most likely to fail.
- T19 (bereavement stated flatly) escalated on content, not tone.

The tone pair T18 / T19 both routed correctly, which is the evidence
that routing on content rather than sentiment was the right call.

## The one mismatch: T20

Message: "hey quick q about the project" and nothing else.
Expected: UNKNOWN. Actual: ESCALATE.

This is not a model error. It is a contradiction in the spec I wrote.

SKILL.md rule 5 says escalate anything not clearly routine, and it
runs BEFORE rule 6, which is the coverage check that produces UNKNOWN.
A message with no identifiable question can never reach rule 6.
So ESCALATE was the correct behaviour under the rules as written,
and the answer key was wrong.

Why it matters beyond one test case: UNKNOWN items feed the gap list
that improves answers.md. ESCALATE items do not. Routing vague
messages to ESCALATE means they silently stop contributing to the
improvement loop.

Decision: neither outcome is right. Adding a fifth outcome, CLARIFY.

## Other defects found

1. The test messages carry no timestamps, so the run log could not
   report a date range and URGENT items could not show a time
   received. Fix the fixture.
2. REFUSE has no home in the output format. T16 was filed under
   "Needs you". Give it its own section.
3. Drafts cited more IDs than strictly required (T04 cited A3 and A8
   where A3 alone answers it). Harmless, slightly noisy.

## Next run

Re-run all 22 unchanged after the fixes, and confirm nothing that
passed in run 01 regresses.
