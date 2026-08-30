---
name: notes-to-actions
description: Use when the user asks to turn meeting notes into actions or a task list, pull the action items or to-dos out of notes, work out who agreed to what or who owns what, or find the follow-ups from a meeting or transcript. Triggers on phrasings like "turn these notes into a task list", "extract the action items", "what do I actually need to do after this meeting", "who owns what from this call", "what are the follow-ups". Works on notes from a meeting, 1:1, standup, client call or retro. Do NOT use for a general summary or recap of a meeting, for a weekly or multi-meeting report, or for recording a decision - those are different jobs.
---

# Turning meeting notes into actions

Meetings produce notes. Notes produce nothing. Your job is to close that gap
without inventing anything that was not said.

## The one rule that matters most

**Never invent an owner or a deadline.**

If the notes do not say who is doing something, the owner is `UNASSIGNED`. If the
notes do not say when, the deadline is `NO DATE`. Do not infer either from who was
speaking, who usually does this kind of work, or what would be sensible.

A guessed owner is worse than a blank one. A blank one gets chased in the next
meeting; a guessed one gets quietly ignored by the person who never agreed to it,
and nobody finds out until the deadline passes.

## Steps

1. **Read the whole notes once before writing anything.** Ownership is often
   settled several lines after the task is first raised.

2. **Separate actions from discussion.** An action is something a specific person
   has to *do* after the meeting. Everything else — context, opinions, background,
   things considered and dropped — is discussion. See the test below.

3. **For each action, extract three things:** what is to be done, who owns it, by
   when. Use `UNASSIGNED` and `NO DATE` where the notes are silent.

4. **Write the task so it can be understood alone.** The owner will read this in a
   task list three days from now with none of the meeting in their head.
   "Follow up with them" is not an action. "Email Priya the revised Q3 forecast" is.

5. **Handle dates by how precise they are.** There are three kinds and they are
   treated differently:

   - **Precise and relative** — "by Friday", "next Tuesday", "in two weeks", "end of
     the month". Resolve against the meeting date if the notes give one:
     "by Friday" in notes dated Tuesday 12 August becomes `2026-08-15`. If there is
     no meeting date, keep the words and flag it. Never assume today.
   - **Vague** — "early next week", "soon", "ASAP", "at some point", "before too
     long". These do **not** resolve to a date, even when a meeting date is given.
     Keep the words in the Due column and flag it under Needs a human. "Early next
     week" could mean three different days to three different people.
   - **Absolute** — "by 15 August". Use as given.

6. **List anything needing a human decision** under Needs a human. Every entry starts
   either with an action number (`Action 2: ...`) when it is about a row in the table,
   or with `General:` when it is not tied to one — for example something half-agreed
   that you could not justify making an action, or a missing meeting date. Include
   every `UNASSIGNED`, every `NO DATE`, every vague deadline, and anything you were
   genuinely unsure about.

7. **Never drop something because it was unclear.** An unclear item goes in the
   output marked unclear. Silence loses information; a flag does not.

## Is it an action or just discussion?

Ask: **would somebody have to do something after this meeting because of it?**

| Notes say | Verdict | Why |
|---|---|---|
| "Sam will send the deck by Thursday" | Action | Named person, specific task |
| "we should probably look at pricing at some point" | Discussion | Nobody committed, no timeframe |
| "we agreed to move the launch to October" | Discussion + flag | A decision, not a task — see below |
| "someone needs to chase legal" | Action, `UNASSIGNED` | Real task, no owner named |
| "Priya has already done the migration" | Discussion | Already finished, nothing to do |
| "Tom said he would think about it" | Discussion | Thinking is not a deliverable |

Decisions are not actions, but do not throw them away. Put them under
**Decisions mentioned** so they are not lost, and note that a proper decision record
is a separate job.

## Output format

Always these four sections, in this order, even when a section is empty. An empty
section headed "None" tells the reader you checked; a missing section tells them
nothing.

```
## Actions

| # | Action | Owner | Due |
|---|--------|-------|-----|
| 1 | Email Priya the revised Q3 forecast | Sam Okafor | 2026-08-15 |
| 2 | Chase legal on the DPA | UNASSIGNED | NO DATE |

## Needs a human

- Action 2: no owner named. Somebody must claim it.
- Action 2: no deadline.
- General: no meeting date in the notes, so "by Friday" could not be resolved.

## Decisions mentioned

- Launch moved from September to October. (Not an action — record separately.)

## Discussed, no action

- Pricing review, raised but nobody committed.
```

### When the notes are too thin to work with

If the notes are so fragmentary that you cannot tell whether anything was actually
agreed, do not produce a confident table. Open with one plain sentence saying so,
then give the same four sections with whatever little you have:

> These notes are too fragmentary to tell what was agreed. I have listed the one
> possible action below, but none of it is confirmed and all of it needs checking
> with someone who was in the room.

## What it must never do

- Never assign an owner the notes did not name.
- Never invent a deadline, and never turn "soon" or "ASAP" into a date.
- Never output an empty Actions table with no explanation. If there were genuinely
  no actions, say so in a sentence.
- Never merge two people tasks into one row because they are related.
- Never soften or clean up what was agreed. If the notes are blunt, stay blunt.
- Never add a task that seems obviously necessary but was not discussed.

## When information is missing

| Missing | What to do |
|---|---|
| Owner | `UNASSIGNED` + list under Needs a human |
| Deadline | `NO DATE` + list under Needs a human |
| Meeting date, but relative dates used | Keep "by Friday" as written, flag it |
| Notes are a raw transcript with no structure | Still works — read it all, extract the same way |
| Notes are too fragmentary to tell if anything was agreed | Say so plainly. Do not produce a table of guesses. |
| Same task assigned to two people | One row, both names, flag under Needs a human |

## Example — good output

**Input notes**

> Standup 12/08. Sam to send revised forecast to Priya by Friday. Someone needs to
> chase legal re the DPA — still outstanding from last week. Discussed whether to
> review pricing, parked for now. Agreed we are moving launch to October. Tom said
> he would think about the vendor question.

**Output**

```
## Actions

| # | Action | Owner | Due |
|---|--------|-------|-----|
| 1 | Send revised forecast to Priya | Sam | 2026-08-15 |
| 2 | Chase legal on the outstanding DPA | UNASSIGNED | NO DATE |

## Needs a human

- Action 2: no owner named. It was outstanding last week too.
- Action 2: no deadline.

## Decisions mentioned

- Launch moved to October. (Record separately as a decision.)

## Discussed, no action

- Pricing review — raised and parked, nobody committed.
- Vendor question — Tom to think about it; no deliverable agreed.
```

## Example — bad output, and why

```
## Actions

| # | Action | Owner | Due |
|---|--------|-------|-----|
| 1 | Send forecast | Sam | Friday |
| 2 | Chase legal on the DPA | Tom | 2026-08-19 |
| 3 | Review pricing | Priya | End of month |
| 4 | Confirm October launch date | Sam | 2026-08-15 |
```

Four things wrong, and every one of them is the kind of mistake that looks tidy:

1. **Row 2 invented an owner.** The notes said "someone needs to chase legal". Tom
   was mentioned in a different sentence about something else. Tom will never do
   this, and nobody will notice until it is late.
2. **Row 3 invented an owner and a deadline for something explicitly parked.**
   Discussion became a task with a due date attached to a person.
3. **Row 4 turned a decision into a task nobody agreed to.**
4. **Row 1 says "Friday", not a date.** In three weeks nobody knows which Friday.

Also missing: no Needs a human section, so the reader has no way to see that
anything was uncertain. Everything is presented with equal confidence.

## Self-check before returning

- Can every owner be pointed to in the source text?
- Can every deadline be pointed to in the source text?
- Is every action understandable without reading the notes?
- Did anything unclear get dropped instead of flagged?
- Are all four sections present?
