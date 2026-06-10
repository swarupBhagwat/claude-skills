# Claude Skills Marketplace

A Claude Code plugin marketplace for study-related skills.

## Available Plugins

### study-skills
Skills for turning notes into study materials:
- **flashcard-maker** — Generates Q&A flashcards from notes, textbook excerpts, or any topic text.
- **study-summary** — Condenses notes into a compact study summary / cheat sheet.
- **illustrated-notes-pdf** — Expands notes into a detailed, point-wise, book-style explanation with small diagrams and a custom color scheme, exported as a PDF.

See [`my-study-skills-plugin/README.md`](my-study-skills-plugin/README.md) for plugin details.

## Installation

1. Add this repo as a marketplace:
   ```
   /plugin marketplace add swarupBhagwat/claude-skills
   ```

2. Install the plugin:
   ```
   /plugin install study-skills
   ```

3. Use the skills (namespaced by plugin name):
   ```
   /study-skills:flashcard-maker <notes>
   /study-skills:study-summary <notes>
   /study-skills:illustrated-notes-pdf <notes>
   ```

## Requirements

- `illustrated-notes-pdf` shells out to `npx @mermaid-js/mermaid-cli` and `npx md-to-pdf`, so **Node.js** must be installed. The first run downloads those packages plus a matching headless Chrome build (~1-2 min one-time cost); subsequent runs are cached and fast.

## Updating

To pick up new plugin versions, refresh the marketplace and reinstall:
```
/plugin marketplace update claude-skills
/plugin install study-skills
```
