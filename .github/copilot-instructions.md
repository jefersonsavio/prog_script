## Quick orientation for AI coding agents

This repository is a small teaching playground of static HTML/CSS/JavaScript "aulas" (lessons). The purpose of this file is to give an AI coding agent the minimal, actionable context needed to be productive when making edits, fixes, or small feature additions.

Key points
- Repo layout: top-level lesson folders named `aula1`, `aula2`, ... `aula6`. Each folder contains a simple `*.html` page (example: `aula6/aulaEvento.html`).
- Tech stack: plain static HTML pages with embedded JavaScript. No build system, bundler, or package manager.
- Content language: Portuguese. Keep visible UI strings and comments in Portuguese unless asked to internationalize.

Concrete examples and patterns
- Inline scripts: most JS is embedded directly inside the HTML files. Example: `aula6/aulaEvento.html` uses `window.onload` to register an onclick handler for `btnConverter` and a helper function `conversaoRealParaDolar(valor, dolar)`.
- DOM usage: elements are referenced by `document.getElementById(...)` and results set via `.innerHTML`. Prefer preserving element IDs and semantic structure when modifying behavior.
- User input: numeric fields use `<input type="number">` with values read as strings. Existing code sometimes omits parsing (use `parseFloat`/`parseInt` as needed) — check for `toFixed` and locale formatting (repo uses `replace('.', ',')` pattern in `aula6`).

Developer workflows (how to run / debug)
- No build step. To preview pages locally either:
  - Use VS Code Live Server extension (recommended) to serve files and allow hot reload.
  - Or run a simple HTTP server from the repo root (PowerShell):

    python -m http.server 8000

  then open http://localhost:8000/aula6/aulaEvento.html
- Debugging: open DevTools in the browser (F12) and use the Console for logs and breakpoints. When adding logs, follow the existing style (simple `console.log` statements).

Project-specific conventions
- Filenames and folders use Portuguese words (`aula`, `exercicio`). When creating new lessons follow that same pattern (e.g., `aula7/aula7.html`).
- Keep UI text in Portuguese by default. If you change labels/messages, update all lessons consistently.
- Minimal external dependencies: there are none. Avoid adding heavy toolchains unless requested.

Integration points and external expectations
- There are no external APIs or services integrated. Work is limited to static files and local behavior.

Edit contract for an AI agent (inputs / outputs / checks)
- Inputs: path to one or more `aula*/` HTML files and a short description of desired change (bug fix, UX tweak, new example).
- Outputs: updated HTML files with minimal, well-scoped changes. Keep modifications localized and preserve existing layout and Portuguese text unless instructed otherwise.
- QA smoke checks: open the modified page in a browser, verify the interactive behavior (buttons, prompts) and check console for errors. If numeric logic changed, test with edge values (empty, zero, decimals).

Edge cases to watch for
- Inputs left empty (null/""), non-numeric entries
- International decimal separators (existing code replaces `.` with `,`) — be careful when changing number formatting
- Avoid removing `meta charset="UTF-8"` or changing language attribute `lang="pt-br"`.

If you need clarification
- Ask whether new text should be in Portuguese or English.
- If introducing a dependency/toolchain, confirm the user's willingness to accept a larger change (adds complexity).

Assumptions made
- No CI/build/test setup exists in the repo; I assume pages are previewed in the browser only. If there is an external workflow, tell me and I'll incorporate it.

Files to reference when making changes
- `README.md` — repo purpose
- `aula6/aulaEvento.html` — example: event handling and number formatting
- `aula3/aula3.html` — example: prompts/alerts and basic JS usage

Please review this draft and tell me any missing specifics (preferred commit message style, coding style preferences, or additional files to cite). I'll iterate.
