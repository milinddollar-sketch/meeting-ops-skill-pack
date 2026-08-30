# Review log: notes-to-actions

**Reviewer:** none available, see method below.  
**Author:** Milind Yadav  
**Pull request:** [#1](https://github.com/milinddollar-sketch/meeting-ops-skill-pack/pull/1)

## Method

This pack was meant to be a group of three with reviews in a circle. I was not placed
in a working group, so there was no second person to review my Skill.

What I did instead was hand the file to three assistants with no other context. They
had not seen it being written and had no idea what I intended. Each got the file and
one task, and I recorded what came back.

That mirrors the five checks in the brief: does it fire when it should, does it stay
quiet when it should, where does it break, is anything ambiguous, and would a real
person phrase a request that way. It is the closest substitute I could find for what
the brief describes, which is that the reviewer is the first person who does not know
what you meant.

It is not a peer review and I am not calling it one. A person would have argued with
my judgement, not only with my wording. The last section says what that missed.

Five defects found. All five fixed. Re-tested after fixing.

---

## Defect 1: the description fired on requests it should have refused

**What I tried.** I gave a reviewer only the description line and six requests, and
asked strictly which would fire.

**What happened.** Four of six correct. Two wrong:

* "Summarise this meeting for me" fired. It should not. Asking for a summary is not
  asking for a task list.
* "Here are my lecture notes, make me a to-do list of what to revise" was borderline,
  held out only by inference.

The verdict was that the description blurs "extract actions and owners" with a generic
"write up a standup or call", so it will over-fire on plain summarisation requests that
do not actually want a task list.

**Why it happened.** I had written `write up a standup or call` into the trigger list.
To me that meant "produce the actions from a standup". Read cold, it means "write up
the meeting", which is a summary. My own phrase meant something to me that it does not
mean to anybody else.

**What changed.** I removed that phrase and added an explicit negative boundary, so the
description now says not to use it for a general summary or recap, for a weekly or
multi-meeting report, or for recording a decision.

**After the fix.** Six of six correct.

## Defect 2: two kinds of vague date were handled inconsistently

**What I tried.** Realistic weekly-sync notes dated 26 August containing both
"before month end" and "probably early next week".

**What happened.** It resolved "before month end" to `2026-08-31` but left "early next
week" as words. Both are defensible on their own. Together they are inconsistent, and
nothing in my instructions said which to do.

**Why it happened.** Step 5 said "resolve relative dates against the meeting date" and
separately said "never turn soon into a date". Those two rules collide in the middle
and I never defined the middle. Two people reading my Skill would split on this, which
is the definition of a defect the brief gives.

**What changed.** I rewrote step 5 into three named categories: precise and relative
(resolve it), vague (never resolve it, keep the words, flag it), and absolute (use as
given).

**After the fix.** "Early next week" stayed as words and appeared under Needs a human
with the reason that it could mean different days to different people.

## Defect 3: Needs a human had no room for anything that was not a numbered action

**What I tried.** The same notes, which contain "Aisha to bring numbers next time?
She is away though." That is half-agreed, has a question mark, and the person is on
leave.

**What happened.** The reviewer flagged it under Needs a human, but my format defined
every entry as referring to an action row by number, and this had no action row. The
output ended up with a floating entry that did not match my own spec.

**Why it happened.** I designed that section imagining only two kinds of gap, a missing
owner and a missing deadline. Real notes are full of things that are neither.

**What changed.** Every entry now starts with either `Action N:` or `General:`.

**After the fix.** Three `General:` entries appeared, including the CI numbers question
and the unowned vendor invoice.

## Defect 4: "say so plainly" had nowhere to be said

**What I tried.** Deliberately fragmentary notes: four bullets, one of them literally
`??? follow up`, no names, no dates, no meeting date.

**What happened.** It handled this well and invented nothing. But my instruction said
that if the notes are too fragmentary it should say so plainly, and my output format
has four fixed sections with no place for a sentence like that. So it produced a
confident-looking table for notes that deserved a warning.

**Why it happened.** I wrote a rule about behaviour without giving the output a shape
to carry it. The instruction was unfollowable rather than wrong.

**What changed.** I added a "When the notes are too thin to work with" block with an
example opening sentence that goes above the four sections.

## Defect 5: my own worked example broke the rule I had just written

Fixing defect 3 meant the two examples inside the Skill no longer matched the format
the Skill demanded. Small, but a reader copies the example, not the rule. Both updated.

---

## What was tested and did not break

Worth recording, because a log that only lists failures is as unbalanced as one that
lists none.

**The trap worked.** The test notes contained a deliberate one: "Aisha said she would
look at it, actually no, she is on leave from Wednesday, so let us say Carlos picks it
up." The owner is named several lines after the task is raised, and a careless reading
gives Aisha. Both runs correctly assigned Carlos. Step 1, which says to read the whole
notes once before writing anything, was doing real work.

**Nothing was ever invented.** Across every run, no owner and no deadline appeared that
was not in the source text. The SOW action stayed `UNASSIGNED` even though Ben was
mentioned in the same sentence as holding the old version, which is the most tempting
wrong answer in the whole test and the exact failure this Skill exists to prevent.

---

## One thing I could not fix

The same notes did not produce quite the same actions twice.

In the first run the unpaid vendor invoice became an `UNASSIGNED` action row. After the
fixes it moved to a `General:` entry under Needs a human, plus a line under Discussed,
no action.

Both readings are defensible. Nobody committed to the invoice, so whether it is an
unowned action or an unresolved discussion point is a real judgement call. But my Skill
does not decide it, so the answer moves between runs. Someone using this for real would
get a slightly different list depending on the day.

I do not know how to fix this without writing a rule so specific that it breaks on the
next set of notes. It is recorded rather than resolved.

There is also one thing known and not fixed. The description still has no explicit
negative for non-meeting note sources such as lecture notes, reading notes or a project
doc. That was flagged after the fix. I judged that adding more exclusions would make the
description longer than the thing it describes, and that the positive source list is
doing enough. That is a judgement I could be wrong about.

---

## What this missed

Everything above was found by testing the wording. A person would have argued with the
design: whether "Decisions mentioned" should exist at all when nothing consumes it, or
whether `UNASSIGNED` is better than a best guess with a confidence marker.

Nobody challenged a single one of my decisions, only my phrasing. I suspect that is
where the real defects are.
