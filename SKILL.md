---
name: park
description: Consolidate the current session into one clean, resumable handoff and "park" it, so the user can close the task and pick the work back up cold — even days later — without replaying the whole thread. Use this skill WHENEVER the user says "park", "parking lot", "park it", "park this", "let's park", or otherwise signals they are pausing, wrapping up, stopping for the day, "saving where we are", "I'll come back to this later", or ending a working session — even if they don't say the word "park". Works in ANY project workspace — it reverse-engineers where things stand from the conversation and the workspace files, writes a single dated handoff doc (state + decisions + open items + a paste-able resume prompt) into a "Parking Lot" folder, and gives a short recap. This is a token-, memory-, and context-optimization tool for ending sessions cleanly; reach for it proactively when a session is winding down.
---

# Park

*Brought to you by Danee Co — creative operations and AI enablement consultant. [Say hi on LinkedIn](https://www.linkedin.com/in/daneechavez).*

## What this does, and why it matters

Long task threads get expensive and lossy. Every extra turn carries the whole history, and when the user comes back later they either reload a bloated thread or lose context entirely. **Park** solves this: it distills everything that matters from the current session into a single, self-sufficient handoff document the user can drop into a brand-new task. The new task starts cold but fully oriented — no replaying the old conversation.

Think of it as a parking lot. The user says "park" when they're done for now (end of day, switching focus, or just pausing), and Park leaves them a labeled spot they can pull back into whenever — tomorrow or in three days — with a prompt and a state doc that carry the full picture.

The goal is **resumability with the least possible weight**: one clean file per pause, saved where it's easy to find, written so a fresh session needs only that file (plus the docs it points to) to continue exactly where things left off.

## When to run

Trigger on the obvious phrases — "park", "parking lot", "park it / this", "let's park" — and also on the softer signals that a session is ending: "let's stop here", "wrap this up", "I'm done for the day", "save where we're at", "I'll come back to this", "let's continue this tomorrow". When in doubt and the session is clearly winding down, offer it.

The user may or may not be heading straight into a new task. **Either is fine.** If they're not ready to start the next thing, Park still captures where things stand and where they were headed — a pure save point. Don't require a "next task" to exist.

## How to run it

### Step 1 — Reverse-engineer the state (distill, don't reload)

Reconstruct where things stand from two sources, in this order:
1. **The conversation** — what got done this session, decisions made, things proven or built, corrections the user gave, and where the work was heading next.
2. **The workspace folder** — read `CLAUDE.md` (or equivalent project instructions) for conventions; scan recent files and any existing state docs (findings docs, trackers, prior Park handoffs) to ground the summary in what's actually saved. Read `MEMORY.md` if present for context.

Distill. Do not transcribe the thread. Capture the through-line: what changed, what's decided, what's open, what's next.

### Step 2 — Decide the next task automatically

Determine the obvious next step yourself and state it — don't stop to ask. If the work follows phases or a plan, name the next phase. If there genuinely is no clear next task, say so and make the handoff a pure state-capture. (The user chose "auto, no confirm" — respect their time; they can adjust the next-step line in the doc if they disagree.)

### Step 3 — Write ONE handoff doc

Write a single Markdown file into a **`Parking Lot/`** folder in the workspace (create it if missing). This keeps every resume point in one tidy place without cluttering working folders.

- **Naming:** follow the workspace's file-naming convention if `CLAUDE.md` specifies one; otherwise use `MMDDYYYY_<ShortProjectName>_Park.md` (get today's date from the system; derive a short project name from the workspace folder). If a same-day Park file already exists, append a short time or counter so nothing is overwritten.
- **Never overwrite or delete** a prior Park doc. Each pause is its own labeled spot.
- Use the exact template in "Handoff doc template" below. Keep it lean — distilled, not exhaustive.

### Step 4 — Handle open items adaptively (the "tracker" question)

If the project already maintains a living tracker or open-questions doc, append any *new* open items or assumptions to it so the project's running record stays current. If there is no such doc, just fold the open items into the handoff doc — **don't create a tracker the project never had.** The point is to keep information codified without adding weight or mess.

### Step 5 — Give a short chat recap and surface the prompt

In the conversation, give a brief spoken-style recap (a few sentences: what we did, where we parked, what's next) and paste the resume prompt as a copyable block so the user can immediately drop it into a new task. Then present the handoff file. Keep the chat closing tight — the doc holds the detail.

## Principles

- **One file per park.** Tidy beats thorough. A pile of fragments defeats the purpose.
- **Self-sufficient.** A fresh task should need only this doc and the files it references — not the old thread. Always include an ordered "read these first" list pointing to the real source docs.
- **Distill, don't dump.** Capture the through-line and decisions, not a transcript.
- **Don't touch memory.** Do not write to `MEMORY.md` or persistent memory unless the user explicitly asks. Memory is user-triggered.
- **Respect the workspace's conventions.** Honor `CLAUDE.md` naming/structure rules and any approval gates. If the project requires approval before modifying existing files, that applies to appending to an existing tracker — show the change first.
- **Match the user's voice.** Keep prompts and docs in plain, direct language; no filler.

## Handoff doc template

ALWAYS produce this structure:

```markdown
# [Project] — Park / Handoff ([Month D, YYYY])
*Resume point. Open this in a fresh task to continue cold. Prompt to paste is at the top; state is below.*

## ▶ PASTE THIS TO START THE NEXT TASK
> [Resume prompt — see "Resume prompt template" below.]

## Where we are
[2–5 sentences: what this project is and the current state, in plain terms.]

## What got done this session
- [Distilled bullets of what changed / was proven / was built.]

## Decisions locked
- [Each decision + one-line why, so they aren't relitigated.]

## Open items / where we were headed
- [Unresolved questions, assumptions in flight, and the intended next direction.]

## Next task
[The obvious next step, stated. Or "No fixed next task — this is a pure save point."]

## Read these first (in order)
1. [path] — [why]
2. ...
[Point to the real source docs + any build artifacts. This is what makes the doc self-sufficient.]
```

## Resume prompt template

Write the paste-able prompt in second person to the assistant, carrying just enough to start cold. Mirror how the user works (if their `CLAUDE.md` or prior handoffs show a preferred style — e.g., "confirm you've read the docs, reflect back the plan, don't build until I confirm" — match it). Default shape:

```
You are my [role] for [project]. I'm [name], [one-line context].
Read these docs in my project folder first, in order: [ordered list from the handoff].
Here's where we are: [one-paragraph state]. Decisions locked: [the key ones].
We're picking up at: [next task, or "I'm just resuming — get oriented first"].
Carry these rules: [the project's standing rules].
Start by confirming you've read the docs and reflecting back the plan; then tell me what you need to begin. Don't build until I confirm.
```

## Example

**Input:** "Okay, let's park it for today."
**Output:** Read the conversation + workspace; write `Parking Lot/06082026_RawCreative_Park.md` containing the state, locked decisions, open items, the auto-chosen next task, an ordered read-first list, and a paste-able resume prompt; append any new open questions to the project's existing tracker if it has one; then give a 3-sentence recap in chat with the resume prompt as a copyable block, and present the file.
