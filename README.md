# Skills

![skills.sh](https://skills.sh/b/diegosurita/skills)

This repository stores the AI agent skills I use in my daily development workflow. Install them with the [skills CLI](https://github.com/vercel-labs/skills). That CLI needs Node.js 22.20 or later.

## Install

List the skills in this repository:

```bash
npx skills add diegosurita/skills --list
```

Install every skill into the current project. The CLI asks which agents to install them for:

```bash
npx skills add diegosurita/skills --skill '*'
```

Install them for every project on this machine:

```bash
npx skills add diegosurita/skills --skill '*' -g
```

The CLI installs only the skills named on the command. When a skill tells the agent to follow another skill, install that skill too, or install the whole repository.

- `specify` also needs `feature-document` and `manage-adr`
- `implement` also needs `review`
- `feature-document`, `manage-adr`, and `review` stand alone

```bash
npx skills add diegosurita/skills --skill specify --skill feature-document --skill manage-adr
npx skills add diegosurita/skills --skill implement --skill review
```

From the project that installed them, update with:

```bash
npx skills update
```
