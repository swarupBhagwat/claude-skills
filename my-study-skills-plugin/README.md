# Study Skills Plugin

A Claude Code plugin bundling skills for turning notes into study materials.

## Skills

- **flashcard-maker** — Generates Q&A flashcards from notes, textbook excerpts, or any topic text.
- **study-summary** — Condenses notes into a compact study summary / cheat sheet.
- **illustrated-notes-pdf** — Expands notes into a detailed, point-wise, book-style explanation with small diagrams and a custom color scheme, exported as a PDF.

## Local testing

```
claude --plugin-dir ./my-study-skills-plugin
```

Once loaded, invoke skills as:

```
/study-skills:flashcard-maker <notes file or pasted text>
/study-skills:study-summary <notes file or pasted text>
/study-skills:illustrated-notes-pdf <notes file or pasted text>
```

## Sharing

Push this folder to a git repository. Others can use it directly with `--plugin-dir` after cloning, or you can add a `marketplace.json` to support `/plugin marketplace add` + `/plugin install`.
