Static Web Deployment (HTML/CSS/JS)

This project is now structured as a normal website:
- `index.html`
- `styles.css`
- `scripts.js`
- `config.js`
- local assets (`.png`, etc.)

1) Frontend hosting
   - Upload the project files to any static host (Netlify, Vercel, GitHub Pages, cPanel, Nginx, etc.).
   - Keep `index.html`, `styles.css`, `scripts.js`, and `config.js` in the same directory.
   - Do not use Apps Script `include(...)` in frontend files.

2) Submission backend (optional)
   - `scripts.js` reads backend endpoint from `config.js` (`window.__FORM_CONFIG__.gasUrl`).
   - Put your backend endpoint there (for example, a deployed Apps Script Web App `/exec` URL).
   - If `gasUrl` is empty, submission will be blocked with a user-facing error.

3) Local testing
   - Use a local server (recommended), for example:
     - `python -m http.server 8080`
   - Open `http://localhost:8080/index.html`.

4) Production checks
   - Confirm fonts and logo load correctly.
   - Submit one test record and verify it reaches the backend sheet.
   - Check mobile layout on at least one Android and one iOS viewport.

Troubleshooting
   - If submit fails from static hosting, verify the `/exec` URL in `config.js`.
   - If backend returns errors, inspect Apps Script execution logs.
   - If styling/scripts are missing, confirm `index.html` references `./styles.css`, `./config.js`, and `./scripts.js`.
