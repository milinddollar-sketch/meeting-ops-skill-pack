# Meeting Operations Skill Pack

**Week 3 · AI & Machine Learning Internship · London Success Academy**
Author: Milind Yadav

## What this pack covers

The Meeting Operations job: turning what was said in a meeting into a record somebody can act on.

The full pack is three Skills. **This repository contains one.**

| Skill | Owner | Status |
|---|---|---|
| `notes-to-actions` | Milind Yadav | Written, reviewed, five defects fixed |
| `weekly-report` | unassigned — no group | Not written |
| `decision-log-entry` | unassigned — no group | Not written |

## What happened with the group

This week is written for groups of three: one Skill each, reviewed in a circle. I was not in a working group. My assigned partner from Week 2 has no submissions on record for any week, and I did not get placed into another group in time.

The brief covers this: *"If someone in your group goes quiet — keep going. Ship a two-Skill pack instead of three, close the review circle between the two of you, and say plainly in your submission what happened."*

So this is one Skill, not three. Writing all three would have been doing three people's jobs and would have missed the point of the week, which is the review rather than the volume.

**There was no peer reviewer.** What I did instead is in [`reviews/notes-to-actions.md`](reviews/notes-to-actions.md): I ran the brief's five checks by handing the Skill to assistants with no other context — no memory of writing it, no knowledge of what I meant — and recorded what they actually produced.

That is the closest available substitute for what the brief describes: *"The reviewer is the first person who does not know what you meant."* It is **not** a peer review and I am not calling it one. A person would have argued with my judgement, not just my wording.

The pull request in this repository was therefore opened and merged by me. The review comments on it are the real findings from that testing, not a rubber stamp.

## What notes-to-actions does

Takes messy raw meeting notes and returns a clean action list — what is to be done, who owns it, by when — plus everything the notes left unresolved, flagged rather than guessed.

The single decision the whole Skill is built around: **it never invents an owner or a deadline.** Missing owner is `UNASSIGNED`, missing deadline is `NO DATE`, and both are listed under a "Needs a human" section.

A guessed owner is worse than a blank one. A blank one gets chased at the next meeting; a guessed one gets quietly ignored by someone who never agreed to it, and nobody finds out until the deadline passes.

## How the three would have fitted together

`notes-to-actions` runs first and produces the action list. `weekly-report` would consume several of those outputs across a week. `decision-log-entry` would take the "Decisions mentioned" section that `notes-to-actions` deliberately separates out but does not process — which is why that section exists in the output format even though nothing here consumes it.

## Layout

```
README.md
skills/
  notes-to-actions/
    SKILL.md
reviews/
  notes-to-actions.md
```
