# Contributing to SynCare AI

Thank you for helping improve SynCare AI, a hospital patient-journey and navigation prototype.

## Project overview
A single-file web app (`index.html`: HTML, CSS, vanilla JS, SVG) with simulated data. Read [docs/TECHNICAL_DOCUMENTATION.md](docs/TECHNICAL_DOCUMENTATION.md) first.

## Development setup
1. Fork and clone the repo.
2. Open `index.html` in Chrome or Edge, or run `python -m http.server 8000`.
3. Use browser DevTools (Console, Application > Local Storage) to debug.
4. Do not use real patient data anywhere.

## Repository structure
- `index.html` the application
- `docs/` documentation and images
- `assets/` logo and favicon
- `presentation/` pitch deck
- `.github/` issue templates and Pages workflow

## Workflow
1. Open or pick an issue.
2. Create a branch from `main`.
3. Make small, focused changes. Do not remove existing features without discussion.
4. Test manually (see checklist below).
5. Open a pull request.

### Branch names
`feat/<short-name>`, `fix/<short-name>`, `docs/<short-name>`, `chore/<short-name>`

### Commit messages
Format `type: short description`, e.g. `feat: add appointment booking`, `fix: correct stairs routing`, `docs: update user guide`. Types: feat, fix, docs, style, refactor, test, chore.

## Pull request process
- Describe what changed and why; link the issue.
- Include screenshots for UI changes.
- Confirm the checklist: all 4 languages still render, login flow works, map route works, emergency flow works, no console errors.
- A maintainer reviews and merges.

## Coding standards
- Keep the app self-contained unless a dependency is approved.
- Escape user text before inserting into HTML.
- Add new UI text to the translation dictionary `T` in all four languages.
- Voice must stay **click-only** (never speak automatically).
- Use clear names and short comments for non-obvious logic.

## Documentation standards
Update the matching file in `docs/` and `CHANGELOG.md`. Mark features as IMPLEMENTED, SIMULATED or PLANNED honestly.

## Bug reporting
Use the Bug report template. Include browser, steps, expected and actual result, and screenshots.
