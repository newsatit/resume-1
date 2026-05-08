# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A single-page LaTeX resume (`dawanit_resume.tex`) that compiles to a PDF. The template started from Sourabh Bajaj's base and has been extended with custom commands for a cleaner, one-column layout.

## Build Command

```bash
pdflatex dawanit_resume.tex
```

Run it twice if cross-references or formatting shifts after the first pass. Build artifacts (`.aux`, `.fls`, `.out`, `.log`) are gitignored; only the `.tex` and `.pdf` are tracked.

## Document Structure

The `.tex` file has a preamble defining custom commands, then a single `\begin{document}` block with these sections in order:

1. **Heading** – name, email, GitHub, LinkedIn, phone (centered)
2. **Education** – tabular entry with degree and GPA; coursework listed below
3. **Programming Skills** – free-form text lines for languages and frameworks
4. **Experience** – one or more `\exptitle` blocks with `\expitem` bullets
5. **Projects** – one or more `\projtitle` blocks with `\expitem` bullets
6. **Awards** – plain text lines
7. **Leadership** – plain text lines

## Custom Commands

The file defines two sets of commands. The **active** ones (used in the current content):

| Command | Args | Purpose |
|---|---|---|
| `\exptitle` | `{title}{company}{location}{date}` | Experience section heading |
| `\projtitle` | `{title}{context}` | Project section heading |
| `\award` | `{name}{date}` | Award entry |
| `\expstart` / `\expend` | — | Opens/closes bullet list for an entry |
| `\expitem` | `{text}` | Single bullet point |

The **original template** commands (`\resumeItem`, `\resumeSubheading`, `\resumeSubHeadingListStart`, etc.) remain defined but are unused—they are commented out at the bottom of the file. Do not remove them; they serve as reference for the original template structure.

## Formatting Conventions

- Margins are tightened via `\addtolength` (0.5 in on each side, 0.5 in top, 1.0 in height).
- Font size is 11pt on letterpaper.
- Section titles use `\scshape` + a `\titlerule` underline via the `titlesec` package.
- Bullet items use `\small` text with `-5pt` vspace after each `\expend` to keep spacing tight.
- When adding links, use `\href{url}{\bf anchor}` for bold links or `\href{url}{anchor}` for normal.
