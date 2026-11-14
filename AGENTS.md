# Guide for agents

This file explains how to change document-design without breaking it. The repo holds one agent
skill written in Markdown. It has no build step and runs no code, and it should stay that way.

## Files

- `SKILL.md` is the skill itself and the source of truth. Its frontmatter carries `name`,
  `description`, `license`, and `metadata.version`, following the Agent Skills spec.
- `README.md` covers installation and use, for people and for agents doing the install.
- `LICENSE` is MIT and carries the notices for adapted portions.
- `CHANGELOG.md` holds release notes, newest first.
- `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json` make the repo a Claude Code
  plugin and marketplace. The `"skills": ["./"]` entry loads the root `SKILL.md`.
- `.cursor-plugin/plugin.json` describes the Cursor plugin. It has no skills path, so Cursor loads
  the root `SKILL.md`.
- `agents/openai.yaml` holds the display name, short description, and default prompt for Codex
  and other OpenAI-compatible agents.

## Rules for changes

- Keep the skill agent-neutral. Names such as Claude Code, Codex, and Cursor are examples, not
  limits, and the skill must work in any language.
- Keep the same version in `SKILL.md` under `metadata.version`, in both `plugin.json` files,
  and in the first `CHANGELOG.md` heading. Bump the patch number for wording fixes, the minor
  number for new rules or patterns, and the major number for a renamed skill or removed behavior.
- Every word of `SKILL.md` is read each time the skill runs, so new words have to earn their
  place. Prefer tightening an existing rule over adding a new one.
- Follow the skill's own rules in every file: no em dashes outside examples, no lists where every
  item opens with a bold label, sentence-case headings, and no invented facts in examples.
- Keep humanizer and document-design consistent. They give the same fix for a required warning,
  defer to the same house style, require the same flags to be resolved before sending, and refer
  to each other's rules by name.
- The banned devices are numbered. If you add one, update the README summary and any reference
  to the device numbers in this skill and in humanizer.

## Checks before publishing

- Run `claude plugin validate .` and fix anything it reports.
- Run `npx skills add . --list` and confirm it finds exactly one skill, named `document-design`.
- Keep the frontmatter description under 1,024 characters.
