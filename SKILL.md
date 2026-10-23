---
name: document-design
description: >
  Gate for rendered DOCUMENT and DIAGRAM deliverables: PDF, DOCX, memos, proposals, reports,
  one-pagers, SOPs, deck exports, and any rendered chart, org chart, infographic, or diagram
  image. Read BEFORE writing or editing any document or diagram template or renderer
  (HTML-to-PDF styles, HTML-to-PNG chart renderers, docx generators, LibreOffice pipelines) and
  before sending any rendered document or chart. Web design skills guard web UI; this guards
  paper. This skill owns LAYOUT tells; the humanizer skill (github.com/WolfurX/humanizer) owns
  prose tells, and the exit checklist runs both.
---

# Document design: the paper gate

AI-produced documents have their own recognizable slop, distinct from web slop. The styled
callout box alone marks a document as machine-made before a single word is read. This gate
exists so nothing outward-facing ships with those marks.

## Banned on paper (the document AI-tells)

1. Tinted callout or admonition boxes with a colored accent bar and a bold colored lead-in
   label. This is the single strongest visual tell, and it includes "note", "warning", and
   decision boxes.
2. Emoji or icons in headings, icon bullets, and decorative pictograms next to section titles.
3. Bold-label list items ("**Speed.** Sentence...", repeated down a list). If every item
   opens with a bold label, fold the list into prose or a table.
4. Rounded-corner "cards" on paper, drop shadows, glassmorphism, and gradient header bands.
5. Heavy full-grid table borders on every cell, plus alternating row tints by default.
6. Badge or pill styling for status, version, or tags. Status is text, not a sticker.
7. Center-aligned body blocks, and covers stacked with four or more font sizes.
8. Over-sectioning: a heading over every two-sentence block, and bullet lists where two
   sentences of prose would read better. An over-sectioned document reads as a generated
   outline, so merge tiny sections and let prose be prose.

Devices 2, 3, and 8 have prose-level twins in humanizer (its emoji, inline-header list, and
fragmented-header patterns). Humanizer catches them in the text; this gate catches them in the
template or renderer that produced the text, which is where they come back from.

## Use the document's native devices instead

An aside belongs **in the prose** where it matters, or in: a plain indented paragraph, an
italic aside, a footnote, a margin note, or a one-row table. A genuinely required warning gets
a thin single rule in the text color. It carries no tint or accent bar, and its label stays in
body weight.

Hierarchy comes from **size, weight, and space**, not from spraying color. One accent color,
used at most for: rules, page furniture (header/footer), and genuine emphasis. Tables: thin
horizontal rules only (header rule + closing rule); vertical rules only when columns truly
need separating. Inline editorial flags (e.g. "[VERIFY: legal]") are content, not decoration, so
they may keep their color.

Your organization's house style stays sovereign where defined: this gate constrains HOW
devices are styled, never WHAT your palette, typefaces, or logo lockups are.

## Charts and diagrams are in scope

A rendered chart is a document, not an app screen. The banned list above applies to it, and the
excuse "the boxes are the chart's native device" does NOT license the decoration around them.

Distinguish **encoding** from **decoration**, and keep only encoding. Encoding carries
information: a cluster tint that says which group a box belongs to, a dashed outline that says
this position does not exist yet, a color that maps to a legend. Decoration carries none: an
accent bar across the top of a card when every card in that tier has one (it distinguishes
nothing), a bold colored role label above a name, drop shadows on boxes, a count or status
rendered as a filled pill instead of plain text.

The accent-bar-plus-colored-label combination on a card is the same tell as banned device 1,
just rotated onto a diagram. If a chart renderer predates this skill, run the gate over it before
reusing it. **Inherited renderers are the most common way a banned device survives**: it was drawn
before the rule existed, and evolving it silently carries the tell forward.

## Word/DOCX structural rules (recipients edit these files)

- Real Word heading styles (the navigation pane must work), real tables, real lists.
  Do not lay pages out with text boxes or shapes. They shatter the moment a recipient edits.
- Filenames carry document number/name/version; the version derives from the source of truth,
  never invented at render time.

## Exit checklist (all four, every time)

1. Layout: zero banned devices above (or an explicit instruction overriding one).
2. Prose: run the [humanizer](https://github.com/WolfurX/humanizer) skill over the text (AI
   vocabulary, rule of three, em dash habits, bold overuse). Install it alongside this one.
3. Verification: convert every DOCX/PDF and rasterize EVERY page, then actually look at each
   one before sending. A plausible file that is broken on page 4 is worse than no deliverable.
4. If a template or renderer emitted a banned device, fix the RENDERER, not the one output.
