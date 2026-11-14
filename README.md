# document-design

A [Claude Code skill](https://code.claude.com/docs/en/skills) that acts as a quality gate for
rendered document deliverables (PDF, DOCX, memos, proposals, reports, SOPs) and for rendered
charts, org charts, and diagrams.

## Why

Plenty of skills fight the generic-AI look in **web UI** (purple gradients, three-card
layouts, eyebrow labels). Documents have their own AI tells, and almost nothing polices them.
The strongest one: the tinted callout box with a colored accent bar and a bold lead-in label.
Readers now recognize the box itself as machine styling before they read a word.

This skill is the paper-side counterpart of the web design-taste skills: a short list of
banned layout devices, the native print devices to use instead, structural rules for files
recipients will edit, and an exit checklist that includes rasterizing and eyeballing every
page before anything ships.

## Install

```bash
mkdir -p ~/.claude/skills/document-design
curl -o ~/.claude/skills/document-design/SKILL.md \
  https://raw.githubusercontent.com/WolfurX/document-design/main/SKILL.md
curl -o ~/.claude/skills/document-design/LICENSE \
  https://raw.githubusercontent.com/WolfurX/document-design/main/LICENSE
```

Or clone and copy. Claude Code picks it up automatically; it triggers whenever a document
template, renderer, or rendered deliverable is being written, edited, or sent.

## Install humanizer too

This skill owns layout. The prose side of the same problem (AI vocabulary, rule of three, em
dash habits, bold overuse) belongs to [humanizer](https://github.com/WolfurX/humanizer), and
step 2 of the exit checklist runs it. A document can pass every layout rule here and still read
as generated, so install both.

## Charts count too

A rendered chart is a document, not an app screen. The skill separates **encoding** (a cluster
tint, a dashed outline for a seat that does not exist yet) from **decoration** (an accent bar on
every card in a tier, drop shadows, counts rendered as filled pills) and cuts only the second.
Watch inherited renderers in particular: a chart drawn before you adopted a layout gate carries
its tells forward every time you evolve it.

## Other languages

A document in another language must not look like a translated English template. The skill
checks for template strings left in English; English dates, numbers, and quote marks; the wrong
proofing language; missing glyphs; and layouts that overflow when text runs longer than English.

## What it bans, in one breath

Accent-bar callout boxes, emoji headings, bold-label lists, cards and shadows on paper,
full-grid heavy tables, status badges, centered body text, and over-sectioned
heading-per-paragraph outlines. The replacements are prose, indents, footnotes, thin rules,
and hierarchy built from size, weight, and space.

## License

MIT
