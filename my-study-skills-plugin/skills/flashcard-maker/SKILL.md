---
name: flashcard-maker
description: Generates study flashcards (Q&A pairs) from notes, textbook excerpts, or any topic text. Use when the user pastes study notes and asks for flashcards, a quiz, or help studying/memorizing material.
---

# Flashcard Maker

When the user provides notes, a topic, or text to study from, generate flashcards to help them memorize and review the material.

## Steps

1. Read through the provided text and identify key terms, definitions, dates, formulas, and concepts.
2. Generate flashcards as Question/Answer pairs:
   - Q: <question, term, or prompt>
   - A: <answer, definition, or explanation>
3. Aim for 10-20 flashcards for a typical page of notes. Adjust based on content density.
4. If the notes cover multiple topics/sections, group flashcards under topic headings.
5. Keep questions clear and answers concise (1-3 sentences max).
6. Vary question types where it makes sense:
   - Definition ("What is X?")
   - Fill-in-the-blank ("___ is the process by which...")
   - Compare/contrast ("What's the difference between X and Y?")

## Output format

Default to a simple readable list:

```
## Topic Name

Q: ...
A: ...

Q: ...
A: ...
```

## Optional formats

If the user asks for an export format, provide:

- **CSV (Anki-importable)**: `Question,Answer` one pair per line, quoted if they contain commas.
- **Quiz mode**: Present only the questions first, then provide an "Answer Key" section at the end so the user can self-test before checking answers.

## Notes

- If the source text is very short or vague, ask the user for more context or a specific topic before generating flashcards.
- Do not invent facts not supported by the provided notes — flag anything you're unsure about rather than guessing.
