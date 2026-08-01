# document-design

A [Claude Code skill](https://code.claude.com/docs/en/skills) that acts as a quality gate for
rendered document deliverables — PDF, DOCX, memos, proposals, reports, SOPs.

## Why

Plenty of skills fight the generic-AI look in **web UI** (purple gradients, three-card
layouts, eyebrow labels). Documents have their own AI tells, and almost nothing polices them.
The strongest one: the tinted callout box with a colored accent bar and a bold lead-in label.
Readers now recognize the box itself — before reading a word — as machine styling.

This skill is the paper-side counterpart of the web design-taste skills: a short list of
banned layout devices, the native print devices to use instead, structural rules for files
recipients will edit, and an exit checklist that includes rasterizing and eyeballing every
page before anything ships.

## Install

```bash
mkdir -p ~/.claude/skills/document-design
curl -o ~/.claude/skills/document-design/SKILL.md \
  https://raw.githubusercontent.com/WolfurX/document-design/main/SKILL.md
```

Or clone and copy. Claude Code picks it up automatically; it triggers whenever a document
template, renderer, or rendered deliverable is being written, edited, or sent.

## What it bans, in one breath

Accent-bar callout boxes, emoji headings, bold-label lists, cards and shadows on paper,
full-grid heavy tables, status badges, centered body text — replaced by prose, indents,
footnotes, thin rules, and hierarchy built from size, weight, and space.

## License

MIT
