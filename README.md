# Skills

Personal Codex skills for reusable agent workflows.

## Included skills

- `book-idea-miner`: Mines books and long-form texts for ideas that can become new or improved AI skills.
- `codebase-reconnaissance`: Builds a verified working model of an unfamiliar repository before changes are made.
- `readability-refactor`: Improves code readability while preserving behavior.
- `skill-retrospective`: Reviews a session to identify evidence-backed improvements to invoked skills.

## Structure

Each skill lives under `.agents/skills/<skill-name>/` and contains a `SKILL.md` file with its instructions. A skill may also include an `agents/openai.yaml` file with display metadata.

## Usage

Clone the repository, then make the skills available from the `.agents/skills` directory in your Codex environment. Invoke a skill by name when its workflow matches your task.

```bash
git clone git@github.com:beserb/skills.git
```

The local `resource/` directory is intentionally excluded from version control.
