---
name: document-design
description: >
  Gate for rendered DOCUMENT and DIAGRAM deliverables: PDF, DOCX, memos, proposals, reports,
  one-pagers, SOPs, deck exports, and any rendered chart, org chart, infographic, or diagram
  image. Read BEFORE writing or editing any document or diagram template or renderer
  (HTML-to-PDF styles, HTML-to-PNG chart renderers, docx generators, LibreOffice pipelines) and
  before sending any rendered document or chart. Web design skills guard web UI; this guards
  paper. This skill owns LAYOUT tells; the ai-copyedit skill (github.com/WolfurX/ai-copyedit) owns
  prose tells, and the exit checklist runs both.
license: MIT
metadata:
  version: "1.1.0"
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
9. Raw Markdown or chat formatting in the rendered file, such as literal **, ##, backticks, or
   pipe tables that the generator passed through instead of converting. It shows the content
   was pasted from a chat tool. Fix the generator so it converts or strips the markup.

Devices 2, 3, 8, and 9 have prose-level twins in ai-copyedit (its emoji, inline-header list,
fragmented-header, and Markdown-in-plain-text patterns). ai-copyedit catches them in the text;
this gate catches them in the template or renderer that produced the text, which is where they
come back from.

## Use the document's native devices instead

An aside belongs **in the prose** where it matters, or in: a plain indented paragraph, an
italic aside, a footnote, a margin note, or a one-row table. A genuinely required warning gets
a thin single rule in the text color. It carries no tint or accent bar, and its label stays in
body weight.

Hierarchy comes from **size, weight, and space**, not from spraying color. One accent color,
used at most for: rules, page furniture (header/footer), and genuine emphasis. Tables: thin
horizontal rules only (header rule + closing rule); vertical rules only when columns truly
need separating. Inline editorial flags (e.g. "[VERIFY: legal]") are content, not decoration, so
they may keep their color while the document is a draft. Resolve every one before it is sent.

Your organization's house style stays sovereign where defined: this gate constrains HOW devices
are styled, never WHAT your palette, typefaces, or logo lockups are. The same holds for
ai-copyedit: a written house style decides mechanics such as heading case, quote marks, and
spelling.

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

## Pick the form before drawing

Decide what the figure has to show, then ask for the form by name. "Make a diagram of this" gets
a default, where "a swimlane diagram with three lanes" gets the right one.

| To show | Ask for |
|---|---|
| One question or whole broken down | Logic tree, or a pyramid diagram for layers |
| Ideas around one topic | Mind map |
| What groups share | Venn diagram |
| Items sorted on two axes | 2x2 matrix |
| Steps and decisions | Flowchart, or a swimlane diagram when several people or teams own the steps |
| A loop | Cycle diagram |
| Causes of one problem | Fishbone diagram |
| Events or phases in time | Timeline, a Gantt chart when tasks have durations, a chevron process for phases in a row |
| Stages that narrow | Funnel chart |
| What a person does and feels at each stage | Customer journey map |
| How two numbers relate | Scatter plot, or a bubble chart to add a third number |
| Parts of a whole | 100% stacked bar chart, or a treemap when the parts are many |
| Values across two categories | Heatmap |
| A share of people | Pictogram chart |
| Nested scopes | Concentric circle diagram |

A single value is a figure in a sentence, not a chart, and anything past about seven categories
or twelve nodes reads better as a table. A diagram earns its place when the point is how things
connect. Show a screen with the screen itself, not with a diagram of it.

Unless the house style or the brief says otherwise, these defaults keep a chart honest. Bars
start at zero, or the axis says where it starts. A chart has one y-axis, so two units become two
small charts instead of a combo chart with two scales. Parts of a whole go in a stacked bar
instead of a pie, donut, or gauge. A series is named by a label or a swatch, and the label text
stays in the text color.

Labels take one to three words in the reader's terms, so a tool goes by its name and a step by
its result. An invented layer name such as "orchestration layer" is ai-copyedit's invented
concept label drawn in a box. A tool with no logo on hand is its name in text, not a letter in
a circle.

## Word/DOCX structural rules (recipients edit these files)

- Real Word heading styles (the navigation pane must work), real tables, real lists.
  Do not lay pages out with text boxes or shapes. They shatter the moment a recipient edits.
- Filenames carry document number/name/version; the version derives from the source of truth,
  never invented at render time.

## Documents in other languages

A document whose body is in another language must not look like a translated English template.
These are the layout-side signs, and ai-copyedit covers the prose side.

- Template strings left in English, such as "Page 1 of 3", "Table of Contents", "Confidential",
  "Draft", "Figure 1", chart axis labels, legends, and header or footer text. Every string the
  renderer emits belongs in the document's language.
- English mechanics in the template, such as title case headings, English quote marks, English
  date and number formats, and a currency symbol in the English position. Take them from the
  document's locale or its house style.
- The wrong proofing language. Set the language of the Word styles to the document's language,
  or hyphenation, spell check, and generated fields such as the table of contents follow English.
- Missing glyphs. A typeface without the language's accented or non-Latin characters falls back
  to another font mid-word, which looks broken. If the house typeface lacks them, use the house
  style's designated fallback or raise it with whoever owns the style.
- Layouts sized for English. German, French, and Spanish text often runs longer than English and
  overflows boxes, table cells, and diagram labels sized for it. Arabic and Hebrew need a mirrored
  right-to-left layout, not right-aligned English.

## Exit checklist (all five, every time)

1. Layout: zero banned devices above (or an explicit instruction overriding one).
2. Prose: run the [ai-copyedit](https://github.com/WolfurX/ai-copyedit) skill over the text (AI
   vocabulary, rule of three, em dash habits, bold overuse, translated-sounding phrasing).
   Install it alongside this one.
3. Flags: resolve every editorial flag and placeholder ("[VERIFY: legal]", "[NEEDS NAME]")
   before the document leaves your hands. A leftover flag reads as unfinished, and ai-copyedit
   treats it as a sign of AI text.
4. Verification: convert every DOCX/PDF and rasterize EVERY page, then actually look at each
   one before sending. In a document that isn't in English, also check every template string,
   date, and number against the document's language. A plausible file that is broken on page 4
   is worse than no deliverable.
5. If a template or renderer emitted a banned device, fix the RENDERER, not the one output.
