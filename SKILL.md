---
name: publish-skill-to-github
description: >
  Package one of Danee's Claude skills for publishing on GitHub: auto-drafts a
  README from the skill's own SKILL.md, applies the locked Danee Co branding,
  bundles a clean folder plus a one-click install zip, and hands over the exact
  GitHub upload steps and repo description. Use whenever Danee says "upload a
  skill to GitHub", "publish my skill", "put this skill on GitHub", "package
  this skill for GitHub", "get this skill ready to share", or names a skill she
  wants to ship publicly. This skill stops at publishing. It does NOT write the
  follower-facing install instructions (that is a separate skill).
---

# Publish Skill to GitHub

Turns a finished Claude skill into a publish-ready GitHub package: a branded README, a clean folder, and a one-click install zip, plus the exact steps to put it up. The order below is fixed. Run it in sequence, and stop at the approval gate before packaging anything.

## When to run

Trigger on "upload a skill to GitHub", "publish my skill", "put this skill on GitHub", "package this skill for GitHub", "get this skill ready to share", or when Danee names a skill and says she wants it public. If she has not said which skill, ask which one before doing anything else.

## The order of steps

Run these in order. Do not skip the approval gate.

1. **Identify and read the source skill.** Confirm which skill she means, then read its `SKILL.md` (usually in her skills directory). Everything downstream is drafted from this file, so read it fully first.

2. **Auto-draft the README from the SKILL.md.** Pull what the skill actually does, when it runs, what it produces, and its principles straight from the source. Do not invent features. Use the README template below.

3. **Apply the Danee Co branding precedent** (locked rules in the next section). Branding goes on the README and as one attribution line inside the SKILL.md copy. It never goes into whatever the skill itself generates at runtime.

4. **Approval gate.** Show Danee the drafted README and wait for an explicit yes before packaging or zipping. Nothing gets bundled until she approves.

5. **Package the folder.** Create a folder named after the skill (e.g. `park/`) holding `README.md` and the branded `SKILL.md`.

6. **Build the install zip.** Zip the folder as `<skill-name>.zip` so followers can download once and upload straight into Claude.

7. **Hand over the GitHub steps.** Give her the upload walkthrough, the repo short-description one-liner, and the note to put her LinkedIn in the Website field. Mention Releases only as an optional tidier path, and default to a plain commit.

## Danee Co branding precedent (locked)

Apply every time, no exceptions:

- **README header**, near the top, bold: `Brought to you by [Danee Co](https://www.linkedin.com/in/daneechavez), creative operations and AI enablement consultant.`
- **README footer**, last line: a short, warm CTA back to LinkedIn, in her voice. Example shape: `Built by Danee Co. If this saved you time, tell me what landed: https://www.linkedin.com/in/daneechavez`
- **SKILL.md attribution**, one italic line directly under the `#` title: `*Brought to you by Danee Co, creative operations and AI enablement consultant. Say hi on LinkedIn: https://www.linkedin.com/in/daneechavez*`
- **Never in generated output.** If the skill writes working files at runtime (handoff docs, reports, drafts), branding stays out of those. Those belong to the user.
- **License:** MIT, unless Danee says otherwise.
- **LinkedIn URL:** https://www.linkedin.com/in/daneechavez

### Voice rules (non-negotiable on anything public)

The README and the repo description go out under Danee's name, so they follow her voice rules. Reference the `danee-voice-skill` for the full set. The hard ones:

- **No em dashes.** Restructure with commas, colons, or periods. If a dash is unavoidable, use a double dash `--`, and at most once.
- **No "genuinely", no "moved the needle"**, and no other obvious AI tells.
- Plain and direct. No filler, no hype.

Run the finished README and description through this check before handing them over.

## File format

- `README.md`: GitHub-flavored Markdown. Renders on the repo landing page.
- `SKILL.md`: YAML frontmatter (`name`, `description`) followed by the Markdown body. The branded copy adds the one attribution line under the title; the rest of the body is unchanged.
- Folder: `<skill-name>/` containing both files. This is what gets committed to the repo.
- `<skill-name>.zip`: the folder, zipped, for one-click follower download and install.

## README template

Draft from the source SKILL.md. Keep it lean. No em dashes.

```markdown
# [Skill Name]

**Brought to you by [Danee Co](https://www.linkedin.com/in/daneechavez), creative operations and AI enablement consultant.**

[One or two sentences: what the skill is and the problem it solves, pulled from the SKILL.md.]

## What it does

[2 to 4 short paragraphs distilled from the SKILL.md body.]

## When it runs

[The trigger phrases and situations, from the SKILL.md description.]

## What you get

[Bulleted outcomes. Use a colon after each label, not a dash:]
- **Label:** what it produces.

## Principles

[The skill's core rules, distilled.]

## Install

Drop the `[skill-name]/` folder (containing `SKILL.md`) into your Claude skills directory. In Claude Cowork or Claude.ai with skills enabled, it loads automatically and fires on the trigger phrases above.

## License

MIT

---

Built by Danee Co. If this saved you time, tell me what landed: https://www.linkedin.com/in/daneechavez
```

## GitHub repo short-description template

The one-liner beside the repo name. Front-load the value; only the first ~120 characters show before truncation.

`[Skill Name]: a Claude skill that [core value in one clause]. By Danee Co.`

## GitHub upload steps (hand these to Danee)

1. On github.com, click **+** then **New repository**. Name it after the skill (e.g. `park-skill`). Paste the short description. Choose Public or Private. Check **Add a README file**, then **Create repository**.
2. Put her LinkedIn in the **Website** field (gear icon by the About section, or the repo settings).
3. Click **Add file** then **Upload files**. Drag in `README.md`, `SKILL.md`, and `<skill-name>.zip`. Scroll down and **Commit changes**.
4. Edit the auto-created `README.md`, paste the branded version, **Commit**.
5. Followers download the skill by clicking `<skill-name>.zip` then **Download**. That is the link to point to from LinkedIn.

Optional: instead of committing the zip into the file tree, attach it under **Releases** for a tidy, stable download link. Skip unless she asks.

## Principles

- **Draft from the source, never invent.** The README reflects what the SKILL.md actually does.
- **Approval before packaging.** Show the README, wait for yes, then zip.
- **Branding on the wrapper, not the output.** README and SKILL.md attribution, never the runtime files.
- **Voice rules are not optional.** Public copy gets the no-em-dash, no-AI-tells pass every time.
- **One folder, one zip, clean steps.** Tidy beats clever.
