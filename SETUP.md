# Setting up Front Door for your course

About twenty minutes, once. No coding.

---

## Before you start

You need your syllabus open, and Claude installed.

---

## Step 1 — Make your course folder

Create a folder anywhere you like, named after your course.

    Documents/mktg450/

This folder holds YOUR content. It is private to you. It never goes
into the shared repository.

## Step 2 — Copy the two templates into it

From this repository, copy:

    plugins/front-door/templates/escalate.template.md
    plugins/front-door/templates/answers.template.md

into your course folder, and rename them:

    escalate.md
    answers.md

## Step 3 — Fill in escalate.md first

Do this one before the other one. It is the list of things the
assistant may never answer.

Most of it is already written and the defaults are safe for any
course. You are filling in the bracketed parts:

- your university's accessibility office name
- your counselling service and dean of students office
- anything specific to your course that should never be auto-answered

**Do not delete a category because it seems unlikely.** The cost of a
category you never needed is zero. The cost of one you removed is not.

## Step 4 — Fill in answers.md from your syllabus

Open your syllabus next to it and copy the answers across. Class
times, office hours, due dates, submission format, group rules, and
so on.

Two rules while you do this:

1. **Do not invent policy here.** If you cannot find the answer in
   your syllabus, leave the entry blank. A blank entry means the
   assistant says "not covered" instead of guessing, which is exactly
   what you want.
2. **Put your late policy and integrity policy in the "Reference
   only" section at the bottom.** Those are written down so you can
   see them while reviewing, but the assistant is forbidden from
   quoting them to a student. Both are negotiations, not answers.

Expect this to take fifteen minutes and to be slightly annoying. That
annoyance is the point: you are finding out which parts of your
syllabus do not actually answer a question.

## Step 5 — Run it

Open Claude in your course folder and type:

    run the front door

The first time, run it against the example messages in `tests/inbox.md`
rather than your real inbox, so you can see what it does before it
touches anything real.

## Step 6 — Read the output before trusting it

You get six sections. Check three things:

1. Did anything appear under **Drafts ready** that should not have?
   That is a missed escalation, and it is the only failure that matters.
2. Does every draft cite an answer ID, like [A4]? Click through one or
   two and confirm the answer file actually says that.
3. What is under **Not covered**? That list is the set of questions your
   syllabus does not answer. Add them to answers.md and they stop
   appearing.

## Step 7 — Point it at your real inbox

Once you trust the output on the test set, run it against the last
seven days of your real email.

It still drafts. You still send.

---

## Keeping it healthy

**Every week:** add whatever showed up under "Not covered" to answers.md.

**Every term:** re-read escalate.md before classes start and update the
date at the top. A governance file with a stale review date is fiction.

**When something goes wrong:** add that message to `tests/inbox.md` as a
new case with the outcome it should have produced. The test set should
grow every time reality surprises you.
