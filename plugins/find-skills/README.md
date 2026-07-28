# Find Skills Plugin

Helps Claude discover and install agent skills from the open agent skills ecosystem, powered by the [Skills CLI](https://skills.sh/) (`npx skills`).

## What It Does

Claude uses this skill when you ask things like "how do I do X", "find a skill for X", or "is there a skill that can...". It checks the [skills.sh](https://skills.sh/) leaderboard and searches with `npx skills find`, verifies quality (install counts, source reputation, GitHub stars), and offers to install a matching skill with `npx skills add`.

## Usage

```
"Is there a skill for reviewing PRs?"
"How do I make my React app faster?"
"Find a skill for writing changelogs"
```

Claude will search for relevant skills, present the best matches with install counts and sources, and install one for you if you'd like.

## Learn More

- [Skills CLI documentation](https://github.com/vercel-labs/skills)
- [Browse skills at skills.sh](https://skills.sh/)

## Source

This skill is adapted from [vercel-labs/skills](https://github.com/vercel-labs/skills), licensed under MIT.

## Authors

Vercel
