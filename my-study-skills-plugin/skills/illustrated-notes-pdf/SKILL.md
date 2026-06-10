---
name: illustrated-notes-pdf
description: Turns notes into a detailed, point-wise, book-style explanation with small diagrams, highlighted key terms, and a custom color scheme, then exports it as a PDF. Use when the user wants their notes expanded into a textbook-style PDF study guide with diagrams and highlights.
---

# Illustrated Notes-to-PDF Generator

Expand the user's notes into a detailed, point-wise, book-style explanation, add small diagrams where they clarify a concept, apply a color scheme with highlighted key terms, and export everything as a single PDF.

## Steps

### 1. Get the color scheme
If the user hasn't specified a color palette / highlight style in their request, ask before generating anything (e.g. "soft blue headings with yellow highlights", "dark mode with green accents", etc.). Offer 2-3 quick example palettes if they have no preference. Do not proceed to content generation until this is settled.

### 2. Expand the notes, book-style
For each topic/section in the source notes:
- Write a short intro paragraph (1-3 sentences) framing the topic, like a textbook chapter opener.
- Break the explanation into clearly numbered or bulleted points — each point should be a complete, self-contained idea (not just a fragment).
- Define key terms inline and mark them for highlighting (see step 4).
- Add short examples or analogies where they aid understanding, but don't pad — stay close to what's in the source notes plus reasonable elaboration of it.
- End each section with a brief "Key Takeaways" list.

Do not invent facts that contradict or have no basis in the source notes. Elaboration/explanation beyond the notes is fine; new claims of fact are not.

### 3. Build the Markdown document (with inline Mermaid diagrams)
Create a single Markdown file (`notes.md`) containing the expanded content:
- Use `#`/`##`/`###` headings matching the book-style structure.
- Highlight key terms/definitions using `<mark>term</mark>` (the highlight color comes from the CSS in step 5).
- For 1-3 of the most structural/relational concepts (processes, hierarchies, comparisons, cycles), embed a small Mermaid diagram directly as a fenced code block (flowchart, graph, or sequence — keep to 3-8 nodes):
  ````
  ```mermaid
  graph TD
      A[Start] --> B[End]
  ```
  ````
  Don't diagram everything; only where a visual genuinely clarifies the relationship better than text.

### 4. Render all diagrams in one pass
Convert every `mermaid` code block in the markdown to an SVG image in a single mermaid-cli call (much faster than rendering one diagram at a time — one browser launch instead of N):
```
npx --yes @mermaid-js/mermaid-cli -i notes.md -o notes-rendered.md -b transparent -t neutral
```
This produces `notes-rendered.md` (with `![diagram](./notes-rendered-1.svg)` etc. in place of the code blocks) plus one `.svg` file per diagram. If there are no diagrams, skip this step and use `notes.md` directly in step 6.

(First-ever run on a machine downloads mermaid-cli + a matching headless Chrome build — expected, ~1-2 min one-time cost. If it fails with a Chrome version mismatch, run `npx --yes puppeteer browsers install chrome-headless-shell@<version from error>`.)

### 5. Write the CSS for the chosen color scheme
Create a stylesheet (`style.css`) implementing the palette agreed in step 1: heading colors, body text/background, `mark` highlight color, blockquote/callout styling for "Key Takeaways", and image sizing/centering for diagrams (e.g. `img { max-width: 80%; display: block; margin: 1em auto; }`).

### 6. Convert to PDF
Use `md-to-pdf` with a small config file pointing at the stylesheet:
```
npx --yes md-to-pdf notes-rendered.md --config-file md-to-pdf.config.cjs
```
Where `md-to-pdf.config.cjs` exports something like:
```js
module.exports = {
  stylesheet: ['style.css'],
  pdf_options: { format: 'A4', margin: '20mm' },
};
```
If the CLI rejects a flag, run `npx --yes md-to-pdf --help` to check current options and adjust.

### 7. Clean up
Delete the intermediate `.md`, `.svg`, `.css`, and config files, leaving only the final PDF in the working directory (per the user's preference for PDF-only output). Tell the user where the PDF was saved.

## Notes
- Keep diagrams genuinely small and simple — they're an aid, not decoration.
- Reserve highlighting for key terms, definitions, and important warnings/exceptions — over-highlighting defeats the purpose.
- If source notes are very short, say so and offer a more modest expansion rather than padding with filler.
- This pipeline uses exactly two Puppeteer launches total (one for diagram rendering, one for PDF export), regardless of how many diagrams there are — keep it that way rather than rendering diagrams individually.
- Both `@mermaid-js/mermaid-cli` and `md-to-pdf`, plus the matching headless Chrome build, are cached after first use — repeat runs only take a few seconds.
