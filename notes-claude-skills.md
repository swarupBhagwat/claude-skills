# Claude Skills Notes (Sample for testing skills)

## What is a Skill?

A **skill** is a packaged set of instructions that extends Claude's capabilities for a specific task. Skills let Claude follow a consistent, repeatable process instead of improvising each time.

- Skills are stored as folders containing a **SKILL.md** file (and optionally supporting scripts/assets).
- They can live at the **project level** (`.claude/skills/`) or **user level** (`~/.claude/skills/`).
- A skill is invoked either automatically (Claude recognizes the task matches a skill's description) or explicitly via a slash command like `/flashcard-maker`.

## SKILL.md Structure

- **Frontmatter**: A YAML block at the top with `name` and `description` fields.
  - `name`: A short, kebab-case identifier for the skill.
  - `description`: Explains what the skill does and **when** to use it — this is what Claude matches against user requests to decide whether to trigger the skill automatically.
- **Body**: Markdown instructions describing the steps Claude should follow, the expected output format, and any special notes or constraints.

## How Skills Get Triggered

- Claude reads the `description` field of every available skill.
- If a user's request matches the description (e.g., "make flashcards from these notes" matches a flashcard skill), Claude launches that skill automatically.
- Users can also explicitly invoke a skill using `/skill-name`, optionally with arguments (e.g., `/study-summary notes.md`).

## Best Practices for Writing Skills

- **Be specific in the description**: vague descriptions cause skills to trigger too often or not at all.
- **Keep steps concrete and ordered**: numbered steps reduce ambiguity about what to do first.
- **Define the output format explicitly**: show an example template so output is consistent across runs.
- **Add a Notes section**: capture edge cases, things to avoid, or constraints (e.g., "don't invent facts not in the source").
- **Avoid over-engineering**: a skill should solve the task at hand, not handle every hypothetical future case.

## Skills vs Other Claude Code Features

- **Skills**: reusable task instructions, triggered by description match or slash command.
- **Hooks**: shell commands the harness runs automatically on events (e.g., after a tool call) — used for automated behaviors like linting after edits.
- **Subagents**: separate agents with their own tools and context, used for delegating complex or parallel research/work.
- **Memory**: persistent file-based notes about the user, project, and feedback that carry across conversations.

## Quick Recap

- A skill = SKILL.md (frontmatter + instructions) inside `.claude/skills/<skill-name>/`.
- The `description` field controls automatic triggering — make it specific.
- Skills can be invoked automatically or via `/skill-name [args]`.
- Good skills have clear numbered steps, an explicit output format, and a notes section for edge cases.
