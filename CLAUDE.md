# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page static site for **HOYNK (Hold On! You Never Know)**. Keep the parts, before the whole thing goes. Plain HTML/CSS, no build step, no framework, no dependencies. Deployed via GitHub Pages from the `/web` folder with custom domain `hoynk.issify.com` (mapped via `web/CNAME`).

## Structure

```
web/
  index.html    # the whole page (hero, why, in-practice, what-it-isn't)
  style.css     # external stylesheet
  app.js        # dynamic footer year
  icon.svg      # favicon
  CNAME         # custom domain for GitHub Pages
```

Typography uses the OS system font stack — no webfont requests.

## Local preview

Just open `web/index.html` directly in a browser, or serve the folder:

```sh
cd web && python3 -m http.server 8000
```

## Deployment

GitHub Pages serves `/web` on `main`. Pushing to `main` redeploys.

## Commit messages

Use Conventional Commits:

- `feat:` — new feature or content addition
- `fix:` — bug fix
- `docs:` — README / docs only
- `style:` — CSS / formatting
- `refactor:` — code change that is neither feat nor fix
- `chore:` — tooling, gitignore, housekeeping

Format: `<type>: <short imperative summary>`, ≤72 chars, imperative mood.

## Staging

Stage files by explicit path. Do **not** use `git add -A` or `git add .` — avoids pulling in `.DS_Store`, `.idea/`, or other stray local files.

## Git workflow (MANDATORY)

**This is a strict rule — Claude Code MUST follow it in every interaction.**

- **NEVER** run `git add`, `git commit`, `git push`, `git tag`, or any other git command that mutates repository state.
- **NEVER** stage files on behalf of the user.
- When changes are ready, **propose**:
  1. A commit message following the Conventional Commits format (see above).
  2. The explicit list of files the user should stage.
- The user reviews and runs all git commands themselves.
- This rule overrides any default assistant behavior that would otherwise create commits automatically.
