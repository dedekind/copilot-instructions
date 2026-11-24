---
description: "Use when editing Markdown files. Covers structure and formatting."
applyTo: "**/*.md"
---

# Markdown Style

- Surround lists with a blank line above and below.
- Hard-wrap prose at 100 characters, filling lines close to the limit before wrapping. Do not
  hard-wrap headings, table rows, link URLs, or lines inside fenced code blocks. These may exceed
  100 characters.
- Keep links, inline code, bold spans, and italic spans on one line. Never split them when
  hard-wrapping, even if the previous line ends up short. Put a link that does not fit within 100
  characters on its own line.
- Capitalize section headings in title case.
- Specify a language tag for every fenced code block. Never use a bare code fence. Use `text` for
  plain output and command examples.
- Use backticks for CPU instructions, registers, exception mnemonics such as `#GP(0)`, and API or
  tool names. Do not use backticks for mechanisms or concepts, inside headings, inside link text,
  or inside bold spans.
- Put punctuation outside bold markers, for example, **MSR accesses**.
- In list items that start with a label, term, or link followed by a colon, capitalize the text
  after the colon, for example, `- **Transport**: Delivers messages`. Do not capitalize after a
  colon in the middle of a sentence.
- Use ASCII-only symbols in pseudo-graphics such as diagrams, trees, and flow sketches.

## Notes

- Use a Note for side information the reader does not need to follow the main flow, such as
  caveats, exceptions, terminology mappings, clarifications of a table or list, and pointers to
  related sections. Keep the main explanation in regular paragraphs.
- Write a Note as its own paragraph starting with `**Note**:`, and capitalize the text after the
  colon.
- Place a Note right after the paragraph, list, or table it qualifies, with blank lines around it.
  Do not put a Note inside a list item.
- Keep a Note to one idea, usually up to 4 lines. Use regular paragraphs for longer text.
- Use these variants when they fit:

  - `**Linux Note**:` for Linux kernel behavior.
  - `**Terminology Note**:` for how the document uses a term or maps it to other terminology.
  - `**Important**:` for a caveat that can lead to wrong conclusions or wrong code.
  - `**Note 1**:`, `**Note 2**:` for several consecutive Notes on the same text.
  - `**Notes**:` or `**Linux Notes**:` followed by a list for several short related Notes.

## Links

- Add a link where the reader may want to stop and read about a concept first.
- Do not link forward to a subsection of the current section. Give enough context for the current
  text and let the subsections add details, or write "see below" or "explained below".
- Link a target at most once per section. In a large section, once per subsection is fine when a
  reader may start reading at that subsection, for example, after following a link.
- Prefer linking to a section, usually at the `##` level, over a subsection.
