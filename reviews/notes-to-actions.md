# Review log — notes-to-actions

**Reviewer:** none available. See method below.  
**Author:** Milind Yadav  
**Pull request:** [#1](https://github.com/milinddollar-sketch/meeting-ops-skill-pack/pull/1)

## Method

This pack was meant to be a group of three with reviews in a circle. I was not placed
in a working group, so there was no second person to review my Skill.

What I did instead: handed the file to three assistants with no other context — they
had not seen it written and had no idea what I intended. Each got the file and one
task, and I recorded what came back.

That mirrors the five checks in the brief (does it fire when it should, does it stay
quiet when it should, where does it break, is anything ambiguous, would a real person
say this), and it is the closest available substitute for what the brief describes:
*"The reviewer is the first person who does not know what you meant."*

It is **not** a peer review and I am not calling it one. A person would have argued
with my judgement, not just my wording. Section "What this missed" at the end is
honest about that.

**Five defects found. All five fixed. Re-tested after fixing.**

---

## Defect 1 — The description fired on requests it should have refused

**What I tried:** gave a reviewer only the description line and six requests, asking
strictly which would fire.

**What happened:** 4 of 6 correct. Two wrong:

- *"Summarise this meeting for me"* → **fired.** It should not. Asking for a summary
  is not asking for a task list.
- *"Here are my lecture notes, make me a to-do list of what to revise"* → borderline,
  held out only by inference.

Verdict quoted: *"the description blurs extract actions/owners with generic write up a
standup or call, so it will over-fire on plain summarization requests that do not
actually want a task list."*

**Why it happened:** I wrote `write up a standup or call` into the trigger list. To me
that meant "produce the actions from a standup". Read cold, it means "write up the
meeting" — which is a summary. My own phrase meant something to me that it does not
mean to anybody else.

**What changed:** removed that phrase, added an explicit negative boundary —
*"Do NOT use for a general summary or recap of a meeting, for a weekly or
multi-meeting report, or for recording a decision — those are different jobs."*

**After the fix:** 6 of 6 correct.

## Defect 2 — Two kinds of vague date handled inconsistently

**What I tried:** realistic weekly-sync notes dated 26 Aug containing both
*"before month end"* and *"probably early next week"*.

**What happened:** it resolved "before month end" to `2026-08-31` but left "early next
week" as words. Both defensible individually. Together inconsistent, and nothing in my
instructions said which to do.

**Why it happened:** step 5 said "resolve relative dates against the meeting date" and
separately "never turn soon into a date". Those two rules collide in the middle and I
never defined the middle. Two people reading my Skill would split on this — which is
exactly the definition of a defect the brief gives.

**What changed:** rewrote step 5 into three named categories — precise-and-relative
(resolve), vague (never resolve, keep the words, flag), absolute (use as given).

**After the fix:** "early next week" stayed as words and appeared under Needs a human
with the reason *"could mean different days to different people."*

## Defect 3 — "Needs a human" had no room for anything that was not a numbered action

**What I tried:** the same notes, which contain *"Aisha to bring numbers next time?
She is away though."* — half-agreed, question mark, and the person is on leave.

**What happened:** the reviewer flagged it under Needs a human, but my format defined
every entry as referring to an action row by number, and this had no action row. The
output ended up with a floating entry that did not match my own spec.

**Why it happened:** I designed that section imagining only two kinds of gap — missing
owner, missing deadline. Real notes are full of things that are neither.

**What changed:** every entry now starts with either `Action N:` or `General:`.

**After the fix:** three `General:` entries appeared, including the CI numbers question
and the unowned vendor invoice.

## Defect 4 — "Say so plainly" had nowhere to be said

**What I tried:** deliberately fragmentary notes — four bullets, one of them literally
`??? follow up`, no names, no dates, no meeting date.

**What happened:** it handled this well and invented nothing. But my instruction said
*"if the notes are too fragmentary, say so plainly"* — and my output format has four
fixed sections with no place for a sentence like that. So it produced a
confident-looking table for notes that deserved a warning.

**Why it happened:** I wrote a rule about behaviour without giving the output a shape
to carry it. The instruction was unfollowable, not wrong.

**What changed:** added a "When the notes are too thin to work with" block with an
example opening sentence that goes above the four sections.

## Defect 5 — My own worked example broke the rule I had just written

Fixing defect 3 meant the two examples inside the Skill no longer matched the format
the Skill demanded. Small, but a reader copies the example, not the rule. Both updated.

---

## What was tested and did NOT break

Worth recording, because a log that only lists failures is as unbalanced as one that
lists none.

**The trap worked.** The test notes contained a deliberate one: *"Aisha said she would
look at it — actually no, she is on leave from Wednesday, so let us say Carlos picks it
up."* The owner is named several lines after the task is raised, and a wrong reading
gives Aisha. Both runs correctly assigned Carlos. Step 1 — "read the whole notes once
before writing anything" — was doing real work.

**Nothing was ever invented.** Across every run, no owner and no deadline appeared that
was not in the source text. The SOW action stayed `UNASSIGNED` even though Ben was
mentioned in the same sentence as holding the old version — the single most tempting
wrong answer in the whole test, and the exact failure mode this Skill exists to prevent.

---

## One thing I could not fix

**The same notes did not produce quite the same actions twice.**

In the first run the unpaid vendor invoice became an `UNASSIGNED` action row. After the
fixes it moved out of the table into `General:` under Needs a human, plus a line under
Discussed, no action.

Both readings are defensible — nobody committed to the invoice, so whether it is an
unowned action or an unresolved discussion point is a genuine judgement call. But my
Skill does not decide it, so the answer moves between runs. Someone using this for real
would get a slightly different list depending on the day.

I do not know how to fix this without writing a rule so specific it breaks on the next
set of notes. Recorded rather than resolved.

**Also known and not fixed:** the description still has no explicit negative for
non-meeting note sources — lecture notes, reading notes, a project doc. Flagged after
the fix. I judged that adding more exclusions would make the description longer than the
thing it describes, and the positive source list is doing enough. That is a judgement I
could be wrong about.

---

## What this missed

Everything above was found by testing the wording. A person would have argued with the
**design** — whether "Decisions mentioned" should exist at all when nothing consumes it,
whether `UNASSIGNED` is genuinely better than a best guess with a confidence marker.

Nobody challenged a single one of my decisions, only my phrasing. I suspect that is
where the real defects are.
