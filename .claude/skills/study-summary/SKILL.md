---
name: study-summary
description: Condenses notes, textbook excerpts, or articles into a short study summary / cheat sheet with key points and definitions. Use when the user pastes notes and asks for a summary, cheat sheet, study guide, or "key takeaways".
---

# Study Summary / Cheat Sheet Maker

When the user provides notes or text to study from, condense it into a compact, easy-to-review cheat sheet.

## Steps

1. Read through the provided text and identify the main topics/sections.
2. For each topic, extract:
   - A 1-2 sentence summary of the core idea
   - Key terms with short definitions (bolded term + brief definition)
   - Any formulas, equations, or processes worth memorizing, written exactly as given
3. Cut filler, repetition, and examples unless an example is essential to understanding the concept.
4. Organize the output under headings matching the original topics/sections.
5. Keep the whole cheat sheet short enough to fit on 1-2 pages — prioritize the most testable/important facts.

## Output format

```
# Study Summary: <Topic>

## <Section Name>
- Core idea: <1-2 sentence summary>
- **Term**: definition
- **Term**: definition
- Formula/process: ...

## <Next Section Name>
...

## Quick Recap
- 3-5 bullet points covering the most important things to remember overall
```

## Notes

- Do not add information that isn't in the source notes — only condense and clarify what's there.
- If the notes are already very short, say so and offer a brief recap instead of padding the output.
- If the user asks for a specific length (e.g., "fit on one index card"), prioritize the most exam-relevant points to meet that constraint.
