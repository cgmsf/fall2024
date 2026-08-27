# AGENTS.md

Guidance for AI coding agents (Cursor Cloud Agents and others) working in this repository.

## What this project is

A small, self-contained static web page: a **Grade Calculator** that weights
**Participation (40%)**, **Effort (40%)**, and **Improvement (20%)** into a final grade.

There is no backend, build step, framework, package manager, or dependencies — just
static files served over HTTP.

## Running / previewing

The Cloud Agent environment (`.cursor/environment.json`) automatically starts a static
file server, so you normally don't need to start anything:

- Server: `python3 -m http.server 8000` (run from the repo root)
- Directory listing: http://localhost:8000/
- The app: http://localhost:8000/Fall%202024%20Grade%20Calculator.html

To run it manually in a fresh shell: `python3 -m http.server 8000`.

## Conventions

- Keep the project **dependency-free and simple**. Do not introduce a build system,
  framework, bundler, or package manager unless the user explicitly asks for one.
- **HTML files must be real, renderable HTML.** Note: `Fall 2024 Grade Calculator.html`
  is currently a macOS "Cocoa HTML Writer" export whose body contains the calculator
  markup as *escaped text*, so browsers display its source code instead of rendering the
  calculator. If you edit that file, replace it with the un-escaped, working HTML (the
  correct markup is already embedded inside it as text).
- Preserve the grading weights (Participation 40%, Effort 40%, Improvement 20%) unless
  the user asks to change them.

## Testing changes

- For any UI or behavior change, load the page in a browser via the running server and
  verify it renders and that the **Calculate Final Grade** button produces the expected
  result (e.g. Participation 80, Effort 90, Improvement 100 → `88.00%`).
- When demonstrating a change, include a screenshot or short recording of the working page.
