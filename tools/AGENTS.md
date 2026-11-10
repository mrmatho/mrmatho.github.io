# Agent Instructions

## Repository shape

- This directory contains standalone browser tools: `algorithm-explorer.html`, `password-cracker.html`, `simple-password-cracker.html`, `rubric-editor.html`, and the SQL mystery games `sql-port-wren.html` and `sql-best-and-fairest.html`.
- `index.html` is the landing page for this directory: one card per tool, each with a title, a short tag, a one or two sentence description, and a link to the tool. It reuses the visual style of the site root `../index.html`.
- Each tool is self-contained: markup, inline CSS, and inline JavaScript live in one HTML file. There is no package manager, build system, test suite, or shared runtime in this directory.
- Preserve each page's existing visual language and keep changes local to the owning HTML file unless the task explicitly requires a cross-tool change.

## Keeping the index up to date

- Whenever an HTML tool is added to, renamed in, or removed from this directory, update `index.html` in the same change: add, rename, or remove its card so every tool is listed and no links are broken.
- New cards copy the structure of the existing `<article class="project-card">` cards: a heading link, a `tag`, a short description based on what the page actually does, and a `live-demo` button. Use relative links (e.g. `new-tool.html`).
- Also update the file list under "Repository shape" above.
- When a tool's purpose or audience changes noticeably, update its card description to match.

## Editing conventions

- Use modern browser APIs and plain JavaScript; do not add a framework or dependency for a small interaction.
- Keep DOM element IDs and data attributes stable because the scripts use them as their primary state and event wiring surface.
- Escape user-controlled values before inserting them into `innerHTML`. Treat imported rubric JSON as untrusted input and preserve the editor's existing validation/error behavior.
- Keep educational/security demos clearly client-side and limited to the existing demonstration scope. Do not add network transmission, credential collection, or real-target attack functionality.
- Avoid unrelated formatting churn. Match the page's existing typography, color variables, spacing, responsive rules, and naming style.
- Keep user-facing controls keyboard-accessible and ensure dynamic status/results remain understandable to assistive technology where the page already uses live regions.

## Validation

- For a quick manual check, serve this directory with `python -m http.server 8000` and open the changed HTML page at `http://localhost:8000/<file>.html`.
- Exercise the changed workflow in the browser at desktop and narrow/mobile widths. For `rubric-editor.html`, verify JSON export/import and editing/navigation; for the algorithm tools, verify demo/practice controls; for password tools, use only made-up example passwords.
- After changing `index.html`, open `http://localhost:8000/` and check that every card's link opens the right tool.
- Check the browser console for errors and inspect the generated/downloaded JSON when changing import/export behavior.
- Since there is no automated test command, report manual validation and any browser-dependent behavior in the final summary.
