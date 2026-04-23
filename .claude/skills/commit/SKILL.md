---
name: commit
description: Stage and commit changes using this project's conventional commit style.
argument-hint: "[optional message hint]"
allowed-tools: Bash, Read, Glob, Grep
---

Stage and commit the current changes. $ARGUMENTS

## Steps

1. Run `git status` and `git diff --staged` plus `git diff` to understand exactly what changed.
2. Run `git log --oneline -5` to see recent commit style.
3. Check the active todo list — completed tasks inform the commit message scope and description.
4. Decide whether changes form one logical commit or should be split. Prefer one commit per cohesive unit of work.
5. Stage only the relevant files. Never stage:
   - `dist/` or any build output
   - `.env` or files containing secrets
   - `node_modules/`
6. Write a conventional commit message:
   - Format: `type(scope): description`
   - **type**: `feat` · `fix` · `style` · `refactor` · `docs` · `chore` · `test`
   - **scope**: the route, component, hook, or area changed — e.g. `routes/lesson`, `components/quiz`, `hooks/useProgress`, `tutorial/intro-to-loops`, `lab/build-a-calculator`
   - **description**: imperative present tense, under 72 chars, no trailing period
   - Add a body paragraph if the *why* is non-obvious
7. Create the commit.
