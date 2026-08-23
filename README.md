# Skills

Personal agent skills for reusable workflows.

## Structure

Each skill lives under `.agents/skills/<skill-name>/` and contains a `SKILL.md` file with its instructions. A skill may also include an `agents/openai.yaml` file with display metadata.

## Usage

Clone the repository, then make the skills available from the `.agents/skills` directory in your agent environment. Invoke a skill by name when its workflow matches your task.

```bash
git clone git@github.com:beserb/skills.git
```

The local `resource/` directory is intentionally excluded from version control.
