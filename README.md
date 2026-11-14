# document-design

A [Claude Code skill](https://code.claude.com/docs/en/skills) that acts as a quality gate for
rendered document deliverables (PDF, DOCX, memos, proposals, reports, SOPs) and for rendered
charts, org charts, and diagrams.

## Why

Plenty of skills fight the generic-AI look in web UI (purple gradients, three-card layouts,
eyebrow labels). Documents have their own AI tells, and almost nothing polices them. The
strongest is the tinted callout box with a colored accent bar and a bold lead-in label. Readers
now recognize the box itself as machine styling before they read a word.

This skill is the paper-side counterpart of the web design-taste skills. It has a short list of
banned layout devices, the native print devices to use instead, structural rules for files
recipients will edit, and an exit checklist that includes rasterizing and looking at every page
before anything ships.

## Install

```bash
mkdir -p ~/.claude/skills/document-design
curl -o ~/.claude/skills/document-design/SKILL.md \
  https://raw.githubusercontent.com/WolfurX/document-design/main/SKILL.md
curl -o ~/.claude/skills/document-design/LICENSE \
  https://raw.githubusercontent.com/WolfurX/document-design/main/LICENSE
```

Or clone and copy. Claude Code picks it up automatically. It triggers whenever a document
template, renderer, or rendered deliverable is being written, edited, or sent. To update, run the
same commands again.

## Works with humanizer

This skill owns layout. The prose side of the same problem (AI vocabulary, rule of three, em dash
habits, bold overuse, translated-sounding phrasing) belongs to
[humanizer](https://github.com/WolfurX/humanizer), and step 2 of the exit checklist runs it. A
document can pass every layout rule here and still read as generated, so install both. Where the
two overlap, as with emoji headings, bold-label lists, and too many headings, humanizer catches
the tell in the text and this skill catches it in the template or renderer that produced it.

## What it bans, in one breath

Accent-bar callout boxes, emoji headings, bold-label lists, cards and shadows on paper, full-grid
heavy tables, status badges, centered body text, and over-sectioned heading-per-paragraph
outlines. The replacements are prose, indents, footnotes, thin rules, and hierarchy built from
size, weight, and space. Your house style stays in charge of palette, typefaces, logos, and
mechanics such as heading case, and the gate only constrains how devices are styled.

## Charts count too

A rendered chart is a document, not an app screen. The skill separates **encoding** (a cluster
tint, a dashed outline for a seat that does not exist yet) from **decoration** (an accent bar on
every card in a tier, drop shadows, counts rendered as filled pills) and cuts only the second.
Watch inherited renderers in particular. A chart drawn before you adopted a layout gate carries
its tells forward every time you evolve it.

## Other languages

A document in another language must not look like a translated English template. The skill
checks for template strings left in English, such as "Page 1 of 3" or chart labels, and for
English dates, numbers, and quote marks. It also checks the Word proofing language, missing
glyphs, layouts that overflow when text runs longer than English, and right-to-left scripts laid
out as right-aligned English.

## Exit checklist

Every document goes through five steps before it is sent.

1. Check for banned layout devices, unless an explicit instruction overrides one.
2. Run humanizer over the prose.
3. Resolve every editorial flag and placeholder, such as "[VERIFY: legal]".
4. Rasterize every page and look at it. In a document that isn't in English, also check its
   template strings, dates, and numbers.
5. If a template or renderer emitted a banned device, fix the renderer, not just the one output.

## License

MIT
