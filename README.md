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

The easiest way is to ask your AI agent, in any language:

```text
Install the document-design skill from https://github.com/WolfurX/document-design, following its README.
```

The skill is plain text. It runs no code, needs no API key, and makes no network requests. Once
installed, it triggers whenever your agent writes, edits, or sends a document template,
renderer, or rendered deliverable.

### Claude Code

```text
/plugin install document-design --marketplace WolfurX/document-design
```

On Claude Code older than 2.1.275, run `/plugin marketplace add WolfurX/document-design` first,
then `/plugin install document-design@wolfurx-document-design`. To update later, run
`claude plugin update document-design@wolfurx-document-design`.

### Codex, Cursor, Gemini CLI, GitHub Copilot, Windsurf, OpenCode, and other agents

```bash
npx skills add WolfurX/document-design --global --agent codex
```

Replace `codex` with your agent's name, such as `cursor`, `gemini-cli`, `github-copilot`,
`windsurf`, `opencode`, or `claude-code`. Use `--agent '*'` to install for every agent the
[Skills CLI](https://github.com/vercel-labs/skills) supports, which is about 80. Leave off
`--global` to install only in the current project. The CLI needs Node.js 22.20 or later. Update
with `npx skills update document-design` and remove with `npx skills remove document-design`.

### Claude.ai and Claude Desktop

Download this repository as a ZIP (Code, then Download ZIP) and upload it as a skill in Settings.

### Any other agent

Copy `SKILL.md` and `LICENSE` into a folder named `document-design` inside your agent's skills
folder. The [Skills CLI agent list](https://github.com/vercel-labs/skills/blob/main/docs/agents.md)
shows where each agent looks. For Claude Code, that is:

```bash
mkdir -p ~/.claude/skills/document-design
curl -o ~/.claude/skills/document-design/SKILL.md \
  https://raw.githubusercontent.com/WolfurX/document-design/main/SKILL.md
curl -o ~/.claude/skills/document-design/LICENSE \
  https://raw.githubusercontent.com/WolfurX/document-design/main/LICENSE
```

### Notes for AI agents doing the install

1. Use the method for the agent you are running in: the plugin command in Claude Code, the
   Skills CLI with your own `--agent` name elsewhere, or a manual copy if neither works.
2. Install globally unless the user asks for the current project only.
3. Before installing, check for an existing skill folder named `document-design`. If its
   `SKILL.md` is not this one, ask the user before replacing it.
4. Afterward, confirm the installed `SKILL.md` starts with `name: document-design` and tell the
   user whether they need to restart the agent or open a new session.
5. This skill's exit checklist runs [ai-copyedit](https://github.com/WolfurX/ai-copyedit) over the
   prose, so install ai-copyedit too unless the user declines.

## Works with ai-copyedit

This skill owns layout. The prose side of the same problem (AI vocabulary, rule of three, em
dash habits, bold overuse, translated-sounding phrasing) belongs to
[ai-copyedit](https://github.com/WolfurX/ai-copyedit), and step 2 of the exit checklist runs it. A
document can pass every layout rule here and still read as generated, so install both. Where the
two overlap, as with emoji headings, bold-label lists, too many headings, and leftover Markdown,
ai-copyedit catches the tell in the text and this skill catches it in the template or renderer
that produced it.

## What it bans, in one breath

Accent-bar callout boxes, emoji headings, bold-label lists, cards and shadows on paper,
full-grid heavy tables, status badges, centered body text, over-sectioned heading-per-paragraph
outlines, and raw Markdown symbols left in the rendered file. The replacements are prose,
indents, footnotes, thin rules, and hierarchy built from size, weight, and space. Your house
style stays in charge of palette, typefaces, logos, and mechanics such as heading case, and the
gate only constrains how devices are styled.

## Charts count too

A rendered chart is a document, not an app screen. The skill separates **encoding** (a cluster
tint, a dashed outline for a seat that does not exist yet) from **decoration** (an accent bar on
every card in a tier, drop shadows, counts rendered as filled pills) and cuts only the second.
Watch inherited renderers in particular. A chart drawn before you adopted a layout gate carries
its tells forward every time you evolve it.

The skill also has you pick the form before drawing. It maps what a figure has to show to the
name of the form that shows it, from logic tree to swimlane diagram to treemap, because a form
asked for by name comes out right where "make a diagram" comes out as a default. A few defaults
keep charts honest: bars start at zero, a chart has one y-axis, and parts of a whole go in a
stacked bar instead of a pie, donut, or gauge.

## Other languages

A document in another language must not look like a translated English template. The skill
checks for template strings left in English, such as "Page 1 of 3" or chart labels, and for
English dates, numbers, and quote marks. It also checks the Word proofing language, missing
glyphs, layouts that overflow when text runs longer than English, and right-to-left scripts laid
out as right-aligned English.

## Exit checklist

Every document goes through five steps before it is sent.

1. Check for banned layout devices, unless an explicit instruction overrides one.
2. Run ai-copyedit over the prose.
3. Resolve every editorial flag and placeholder, such as "[VERIFY: legal]".
4. Rasterize every page and look at it. In a document that isn't in English, also check its
   template strings, dates, and numbers.
5. If a template or renderer emitted a banned device, fix the renderer, not just the one output.

## Lineage

The form names follow the diagram pack in
[showheyohtaki/motion-prompt](https://github.com/showheyohtaki/motion-prompt) (Shohei Ohtaki).
The chart defaults are adapted from [Nutlope/hallmark](https://github.com/Nutlope/hallmark), and
the rules for when to draw a diagram and how to label it from
[Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill). All three are MIT-licensed, and
the material is rewritten in this skill's own words.

## License

MIT
