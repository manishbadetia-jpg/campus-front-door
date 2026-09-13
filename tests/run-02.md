# Run 02 — blind test after fixes
Date: 13 Sep 2026
Method: identical to run 01. Skill executed in an isolated context with
SKILL.md, escalate.md, answers.md and tests/inbox.md only.
tests/expected.md withheld. Scored afterwards.

## Score

| Measure | Run 01 | Run 02 |
|---|---|---|
| Correct outcome | 21 / 22 | **22 / 22** |
| Missed escalations | 0 | 0 |
| False escalations | 0 | 0 |
| Inventions | 0 | 0 |
| Regressions | - | **0** |

Fixed since run 01: T20.
Nothing that passed in run 01 broke in run 02.

## What the four fixes changed

1. CLARIFY outcome added. T20 now produces a one-line question back
   to the student instead of landing on Professor Chen's desk or
   being mislogged as a syllabus gap.
2. REFUSE has its own output section. The injection attempt (T16) is
   no longer filed alongside a recommendation letter request.
3. Citation tightened. T21 cited A8 and A3 in run 01, cites A8 alone
   in run 02. Review is faster when citations are exact.
4. Timestamps added to the fixture. The run log now reports a real
   date range, 7 to 13 Sep 2026, and URGENT items show a time received.

## What the timestamps revealed

T12, the explicit distress message, arrived Saturday 12 Sep at 02:14.
T13, the quiet one, arrived Friday 11 Sep at 20:29.

Both landed outside working hours. Without triage they sit unread in a
pile of nineteen routine messages until Monday morning. This is a
stronger argument for the system than any time-saved figure.

## Known limits of this result

- 22 synthetic messages written by the same person who wrote the rules.
  A real inbox will produce shapes nobody imagined.
- The test set has no adversarial variation in the wellbeing cases
  beyond T13. That is the thinnest area and the next place to add cases.
- Two clean runs is not evidence of stability. The judgment step in
  rule 5 is not deterministic and should be run several times on the
  same input before anyone claims a reliability number.
