GitHub Pages + Google Sheets Setup (No Frontend Apps Script)

Goal:
- Host the form UI on GitHub Pages.
- Save submissions to Google Sheets through a Google Apps Script Web App endpoint.

Files in this repo:
- `index.html`, `styles.css`, `scripts.js`: frontend
- `config.js`: backend URL config
- `google-apps-script/Code.gs`: backend script to paste into Apps Script

1) Create / prepare Google Sheet
- Open your target spreadsheet.
- Ensure it has a sheet named `Applications`.
- Optional: create a `Dashboard` sheet if you want counters.

2) Deploy backend (Apps Script Web App)
- Open `https://script.new`.
- Paste the content from `google-apps-script/Code.gs`.
- Update constants at top of file:
  - `SPREADSHEET_ID`
  - `APPLICATIONS_SHEET_NAME`
  - `APPLICATIONS_SHEET_GID` (optional, but recommended)
  - `SUBMISSION_CUTOFF_LOCAL_ISO`
- Click `Deploy` -> `New deployment` -> type `Web app`.
- Execute as: `Me`.
- Who has access: `Anyone`.
- Deploy and copy the `/exec` URL.

3) Connect frontend to backend
- Open local `config.js`.
- Set:
  - `window.__FORM_CONFIG__.gasUrl = "YOUR_DEPLOYED_EXEC_URL"`

4) Publish frontend on GitHub Pages
- Push repository to GitHub.
- In repo settings: `Pages`.
- Source: `Deploy from a branch`.
- Branch: `main` (or your branch), folder `/ (root)`.
- Save and wait for the published URL.

5) Test
- Open your GitHub Pages URL.
- Submit one test entry.
- Verify new row is created in `Applications`.
- Optional health check:
  - `YOUR_EXEC_URL?health=1`

Notes
- Frontend is static and does not require Apps Script templating.
- Backend is Apps Script Web App used only as API endpoint.
- If submission fails:
  - verify `config.js` URL,
  - check Apps Script execution logs,
  - confirm Web App access is `Anyone`.
