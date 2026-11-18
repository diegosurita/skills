# Agent instructions

## Where skills live

Create every skill under `skills/<skill-name>/`. Do not put skills at the repository root or in `.cursor/skills/`. The skills CLI discovers each skill from `skills/<skill-name>/`.

```text
skills/<skill-name>/
  SKILL.md
  README.md
```

## README in every skill

Every skill folder must include a `README.md` that explains:

- the purpose of that skill
- how to use it
- the command to install it, including every skill it depends on

The install command names this skill and each skill its `SKILL.md` tells the agent to follow. Repeat `--skill` for each dependency. When the skill follows no other skill, the command names only itself:

```bash
npx skills add diegosurita/skills --skill <skill-name> --skill <dependency>
```

## SKILL.md

`SKILL.md` is the agent's instructions. The human explanation stays in the skill's `README.md`.

`SKILL.md` starts with YAML frontmatter:

- `name` matches the folder name (`skills/<skill-name>/` uses `name: <skill-name>`)
- `description` says what the skill does and when to use it
