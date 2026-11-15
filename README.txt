# Christmas List PWA

This is the separate GitHub Pages version. It connects directly to Google Sheets using Google OAuth and the Google Sheets API. It does not use Apps Script.

## Before publishing

1. In Google Cloud Console, create/select a project.
2. Enable **Google Sheets API**.
3. Configure the OAuth consent screen. For a private app, choose External if required and add both Google accounts as test users while the app is in Testing.
4. Create an OAuth client ID of type **Web application**.
5. Add your GitHub Pages origin as an authorised JavaScript origin, for example:
   `https://YOUR-GITHUB-USERNAME.github.io`
   Do not add a client secret to this project.
6. Copy the OAuth Client ID into `index.html`, replacing:
   `PASTE_YOUR_GOOGLE_OAUTH_CLIENT_ID_HERE`
7. Make sure both Google accounts have **Editor** access to the Google Sheet.

## Publish on GitHub Pages

1. Create a NEW GitHub repository, e.g. `christmas-list`.
2. Upload all six app files from this folder (`index.html`, `manifest.json`, `sw.js`, `icon.svg`, `icon-192.png`, `icon-512.png`) to the repository root.
3. In the repository, open **Settings → Pages**.
4. Under Build and deployment, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
5. Wait for GitHub Pages to publish, then open the URL on each Android phone in Chrome.
6. Sign in with the Google account that has Editor access to the spreadsheet. Use Chrome's menu → **Install app** or **Add to Home screen**.

## Spreadsheet layout

The app expects these tabs and columns, with headings in row 1:

- People: `Person ID | Name | Created`
- Gifts: `Gift ID | Gift Name | Person ID | Status | Notes | Created | Updated`
- Settings: `Setting | Value`

The spreadsheet ID is already set in `index.html`.

## Notes

- Do not publish the spreadsheet publicly. Share it only with the intended Google accounts.
- The OAuth client ID is public configuration; never add a client secret to frontend code.
- The app needs the Sheets scope so it can read and edit the spreadsheet.
- The app uses the row order in the sheet when editing/deleting. Avoid manually sorting the People or Gifts tabs while the app is in use.
- The PWA shell can open offline, but reading/writing the shared list requires internet access.
- The manifest requests portrait orientation; Android/browser support for enforcing orientation varies.
