# Front Door

An assistant that sorts your student email and drafts the routine
replies, so the messages that need you actually reach you.

It never sends anything. You send every word.

---

## What it does

Every incoming message gets exactly one of six outcomes:

| Outcome | What happens |
|---|---|
| **URGENT** | Looks like a student in difficulty. No draft, no summary, straight to the top of your queue |
| **REFUSED** | Someone trying to manipulate the assistant. Flagged, not obeyed |
| **NEEDS YOU** | Grades, extensions, accommodations, integrity, and the rest. No draft |
| **DRAFT READY** | Routine. A reply written only from your approved answers, citing which one |
| **CLARIFY** | No actual question in the message. One line back asking what they need |
| **NOT COVERED** | Your answers file does not cover this. It says so rather than guessing |

## What it will not do

- Send anything to a student
- State a date, deadline, policy or grade that is not in your answers file
- Grant, deny or negotiate anything
- Summarise a message from a student in difficulty
- Follow instructions written inside a student's message

## How it is put together

Two things, kept separate on purpose.

**The engine** is `skills/front-door/SKILL.md`. It is the same for everyone
and it is maintained here.

**Your content** is two files you own: `answers.md` and `escalate.md`. They
live in your own folder, not in this repository. Nobody else sees them, and
an update to the engine never touches them.

That separation is the reason this works for fifty people instead of one.

## Install

```
/plugin marketplace add <this repository url>
/plugin install front-door@campus-front-door
```

Then follow SETUP.md. It takes about twenty minutes, once.

## Evidence

`tests/` holds 22 synthetic student messages, an answer key, and two scored
runs. The messages include a prompt injection attempt, a quietly worded
distress message with no trigger words, an angry message about a trivial
question, and a calm message about a bereavement.

- Run 01: 21 / 22. One mismatch, caused by a contradiction in the rules
- Run 02: 22 / 22 after the fix, zero regressions
- Both runs: zero missed escalations, zero invented facts

Both runs were scored in an isolated context that could not see the
answer key.

## Limits, stated plainly

- The test messages are invented. A real inbox will produce shapes nobody
  anticipated.
- The judgment step is not deterministic. Two clean runs is not a
  reliability figure.
- This is a pilot. Before it goes near real student mail at any scale, the
  wellbeing routing needs sign-off from the people who already own that
  pathway at your institution.

## Never commit these

- A real student message
- Any password, token or API key
