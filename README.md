# GarageLog iOS V2.3.1

Personal vehicle fuel and maintenance tracker, designed for iPhone Safari / Home Screen PWA use.

## V2.3.1
- Keeps V2.2 edit/delete fuel and maintenance records.
- Multiple vehicles and maintenance schedules.
- Local/offline storage remains the primary working storage.
- Adds Google Sheets cloud backup and restore.
- Adds a real connection test before backup.
- Backup writes a full-fidelity JSON copy plus readable Vehicles, Fuel, Maintenance, and Schedules tabs.
- Backup is verified by reading the saved backup ID back from Google before reporting success.

## Google Sheets setup
1. Create a blank Google Sheet, e.g. `GarageLog Data`.
2. Open **Extensions → Apps Script** from that sheet.
3. Replace the default Apps Script code with `GarageLog_GoogleAppsScript.gs` from this ZIP.
4. In the script, set `SPREADSHEET_ID` to the ID from your Google Sheet URL. Example:
   `https://docs.google.com/spreadsheets/d/ABC123XYZ/edit` → Spreadsheet ID is `ABC123XYZ`.
5. Set `SYNC_KEY` to your own private phrase.
6. Save.
7. Deploy → New deployment → Web app.
8. Execute as: **Me**.
9. Who has access: **Anyone**.
10. Deploy and authorize the script if Google asks.
11. Copy the Web app URL ending in `/exec`.
12. In GarageLog → Google backup, paste the URL and the same sync key.
13. Press **Test connection**. Only after it succeeds, press **Back up to Google**.

Google's Apps Script documentation confirms that a web app must expose `doGet`/`doPost` and is deployed from **Deploy → New deployment → Web app**. https://developers.google.com/apps-script/guides/web

## Important
- Do not upload your personal Google Sheet, JSON backups, or sync key to GitHub.
- The public GitHub Pages app contains no Google account password.
- Local GarageLog storage remains available for offline use.
- Google backup is a separate cloud copy; it does not replace local storage.
