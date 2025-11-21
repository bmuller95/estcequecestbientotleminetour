# Repository Guidelines

## Project Structure & Module Organization
The site is a single-page app served from `index.html`. HTML, CSS, and vanilla JS live inline: the `<style>` tag controls the responsive gradient layout and `<script>` handles countdown logic plus event boundaries (`EVENT_START`, `EVENT_SOFT_END`, `EVENT_HARD_END`). Keep new helpers self-contained in that script or factor them below the constant definitions. If you add media or fonts, place them under an `assets/` directory and reference relative URLs so everything still works on GitHub Pages.

## Build, Test, and Development Commands
- `python3 -m http.server 4173` – spins up a quick static server inside the repo root so the countdown runs via http instead of the `file://` protocol.
- `npx serve .` – alternative Node-based static server; useful if Python is unavailable.
- `npm run lint` – reserved for future linters; add it once tooling lands so contributors have a single command to run.
No bundler is required; changes to `index.html` reflect immediately after a browser refresh.

## Coding Style & Naming Conventions
Use two-space indentation to match the existing file. Stick to semantic HTML tags (`main`, `footer`, etc.) and keep CSS selectors descriptive but short (e.g., `.countdown`). In JS prefer `const` and `let`, camelCase for variables (`formatDiff`), and single quotes inside template literals to avoid HTML entity noise. When extending copy, keep strings localized in French and escape apostrophes consistently.

## Testing Guidelines
There is no automated framework yet; rely on manual verification. After edits, load the local server, confirm each state: before the event, during (`Oui !`), soft end, and post-event. Use DevTools to override the system clock or temporarily tweak `EVENT_START` values to force each branch. Keep console output clean—log statements should be removed or wrapped in debug guards.

## Commit & Pull Request Guidelines
Current history uses short, imperative commits (`Init`), so continue with concise present-tense summaries such as “Update countdown copy”. Each PR should describe the user-visible change set, list manual test steps (time travel scenarios), and link any tracking issue. Include screenshots or short screen recordings when modifying layout, especially for light/dark themes or responsive tweaks, so reviewers can validate without rebuilding.
