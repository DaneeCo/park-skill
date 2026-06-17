# Park

**Brought to you by [Danee Co](https://www.linkedin.com/in/daneechavez), creative operations and AI enablement consultant.**

A Claude skill that consolidates a working session into one clean, resumable handoff document, so you can close a task and pick the work back up cold, even days later, without replaying the whole thread.

## What it does

Long task threads get expensive and lossy. Every extra turn drags the full history along, and when you return later you either reload a bloated thread or lose context entirely. Park solves that. It distills everything that matters from the current session into a single self-sufficient handoff file you can drop into a brand-new task. The new session starts cold but fully oriented.

Think of it as a parking lot. You say "park" when you're done for now, and Park leaves you a labeled spot: a state doc plus a paste-able resume prompt you can pull back into whenever.

## When it runs

Triggers on "park", "parking lot", "park it", "let's park", and on softer end-of-session signals like "let's stop here", "I'm done for the day", "save where we're at", or "I'll come back to this tomorrow." Works in any project workspace.

## What you get

One dated Markdown file written to a `Parking Lot/` folder in your workspace, containing:

- **Where we are:** the project and current state, in plain terms.
- **What got done this session:** distilled, not transcribed.
- **Decisions locked:** each with a one-line why, so they aren't relitigated.
- **Open items / where we were headed:** unresolved questions and intended next direction.
- **Next task:** the obvious next step, stated automatically.
- **Read these first:** an ordered list pointing to the real source docs.
- **A paste-able resume prompt:** drop it into a fresh task to continue cold.

## Principles

- **One file per park.** Tidy beats thorough.
- **Self-sufficient.** A fresh task needs only this doc and the files it references, not the old thread.
- **Distill, don't dump.** Capture the through-line and decisions, not a transcript.
- **Never overwrite a prior park.** Each pause is its own labeled spot.
- **Doesn't touch memory.** Memory stays user-triggered.

## Install

Drop the `park/` folder (containing `SKILL.md`) into your Claude skills directory. In Claude Cowork or Claude.ai with skills enabled, it loads automatically and fires on the trigger phrases above.

## License

MIT

---

Built by Danee Co. If Park saved you a reload, tell me what landed: https://www.linkedin.com/in/daneechavez
