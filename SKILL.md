---
name: document-design
description: >
  Gate for rendered DOCUMENT deliverables — PDF, DOCX, memos, proposals, reports, one-pagers,
  SOPs, deck exports. Read BEFORE writing or editing any document template or renderer
  (HTML-to-PDF styles, docx generators, LibreOffice pipelines) and before sending any rendered
  document. Web design skills guard web UI; this guards paper. Pairs well with a prose
  de-AI-ification pass (e.g. a humanizer skill); this skill owns LAYOUT tells.
---

# Document Design — the paper gate

AI-produced documents have their own recognizable slop, distinct from web slop. The styled
callout box alone marks a document as machine-made before a single word is read. This gate
exists so nothing outward-facing ships with those marks.

## Banned on paper (the document AI-tells)

1. **Tinted callout/admonition boxes with a colored accent bar** and a bold colored lead-in
   label — the single strongest visual tell. Includes "note"/"warning"/decision boxes.
2. **Emoji or icons in headings**, icon bullets, decorative pictograms next to section titles.
3. **Bold-label list items** ("**Speed.** Sentence...", repeated down a list). If every item
   opens with a bold label, fold the list into prose or a table.
4. **Rounded-corner "cards" on paper**, drop shadows, glassmorphism, gradient header bands.
5. **Heavy full-grid table borders** on every cell plus alternating row tints by default.
6. **Badge/pill styling** for status, version, or tags. Status is text, not a sticker.
7. **Center-aligned body blocks** and covers stacked with four or more font sizes.
8. **Over-sectioning**: a heading over every two-sentence block, and bullet lists where two
   sentences of prose would read better. An over-sectioned document reads as a generated
   outline; merge tiny sections and let prose be prose.

## Use the document's native devices instead

An aside belongs **in the prose** where it matters, or in: a plain indented paragraph, an
italic aside, a footnote, a margin note, or a one-row table. A genuinely required warning gets
a thin single rule in the text color — no tint, no bar, label in body weight.

Hierarchy comes from **size, weight, and space** — not from color spraying. One accent color,
used at most for: rules, page furniture (header/footer), and genuine emphasis. Tables: thin
horizontal rules only (header rule + closing rule); vertical rules only when columns truly
need separating. Inline editorial flags (e.g. "[VERIFY: legal]") are content, not decoration —
they may keep their color.

Your organization's house style stays sovereign where defined: this gate constrains HOW
devices are styled, never WHAT your palette, typefaces, or logo lockups are.

## Word/DOCX structural rules (recipients edit these files)

- Real Word heading styles (the navigation pane must work), real tables, real lists.
  **No text boxes, no shapes-as-layout** — they shatter the moment a recipient edits.
- Filenames carry document number/name/version; the version derives from the source of truth,
  never invented at render time.

## Exit checklist (all four, every time)

1. Layout: zero banned devices above (or an explicit instruction overriding one).
2. Prose: a de-AI-ification pass on the text (AI vocabulary, rule-of-three, em-dash habits,
   bold overuse — use a humanizer-style skill if you have one).
3. Verification: convert every DOCX/PDF and rasterize EVERY page, then actually look at each
   one before sending. A plausible file that is broken on page 4 is worse than no deliverable.
4. If a template or renderer emitted a banned device, fix the RENDERER, not the one output.
