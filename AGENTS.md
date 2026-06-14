# Repository Guidelines

## Project Structure & Module Organization

- `index.html` is the complete weather application. It contains the HTML structure, CSS theme and responsive layout, and client-side JavaScript.
- `GITpushUI.py` is a standalone Tkinter helper for staging, committing, and pushing repository changes. It is not part of the web application.
- `.claude/launch.json` defines the local preview server on port `8000`.
- There is currently no separate test, build, or asset directory. Keep tightly related UI changes together in `index.html`; introduce new files only when separation clearly improves maintainability.

## Build, Test, and Development Commands

No compilation or dependency installation is required.

```powershell
python -m http.server 8000
```

Serves the repository at `http://localhost:8000` for local browser testing.

```powershell
python -m py_compile GITpushUI.py
```

Checks the Python helper for syntax errors.

```powershell
git diff --check
```

Detects whitespace errors before committing.

## Coding Style & Naming Conventions

Use two-space indentation in `index.html` for HTML, CSS, and JavaScript. Preserve the existing plain JavaScript approach and CSS custom-property theme system. Use:

- `camelCase` for JavaScript variables and functions.
- `UPPER_SNAKE_CASE` for constants such as API endpoints and storage keys.
- kebab-case for CSS class names and descriptive `data-*` attributes.
- Four-space indentation and PEP 8 naming in Python.

Prefer small, focused functions and reuse existing DOM references, formatting helpers, and weather-theme tokens. Avoid adding frameworks or dependencies for features that fit the current standalone design.

## Testing Guidelines

There is no automated test framework or coverage requirement yet. Manually verify both bright and dark themes, city search, recent locations, forecast loading, calendar and timeline views, responsive layouts, and API failure states. Test through the local HTTP server rather than opening `index.html` directly. Run the Python syntax check when modifying `GITpushUI.py`.

## Commit & Pull Request Guidelines

Existing history mostly uses generic messages such as `new commit`; new commits should use concise imperative summaries, for example `Fix timeline date selection`. Keep each commit focused.

Pull requests should include a short behavior summary, verification steps, and screenshots for visible UI changes. Link relevant issues and call out changes to external API requests, local-storage keys, or browser compatibility.

## Security & Configuration

Do not commit API keys, tokens, credentials, or machine-specific paths. Open-Meteo currently requires no repository secret. Treat location data stored in `localStorage` as user data and avoid logging it unnecessarily.
