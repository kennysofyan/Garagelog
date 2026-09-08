# GarageLog iOS V2.3.4

V2.3.4 keeps GarageLog local-first and adds reliable Google Sheets cloud backup.

## GitHub Pages
Upload the files in this folder to the root of your existing GarageLog repository and commit them. Do not upload GarageLog JSON backups.

## Google Sheets setup
1. Create a blank Google Sheet, e.g. `GarageLog Data`.
2. Copy the Spreadsheet ID from the URL: the text between `/d/` and `/edit`.
3. In that Sheet, open **Extensions → Apps Script**.
4. Delete the default code and paste all of `GarageLog_GoogleAppsScript.gs`.
5. At the top, set `SPREADSHEET_ID` to your Sheet ID and `SYNC_KEY` to your own private key.
6. Save.
7. Deploy → New deployment → Web app.
8. Execute as: **Me**. Who has access: **Anyone**.
9. Authorize when Google asks.
10. Copy the Web app URL ending in `/exec`.
11. In GarageLog → Google backup, paste the URL and the same Sync Key.
12. Save connection → **Test connection**. It must report success.
13. Press **Back up to Google**.

### V2.3.4 note
Browser backups use a JSONP GET request. This avoids the cross-origin POST/redirect behavior that could cause earlier versions to report a failed backup even though the connection test succeeded.

The backup creates/updates these tabs:
- `GarageLog_Backup` — full-fidelity JSON backup
- `Vehicles`
- `Fuel`
- `Maintenance`
- `Schedules`

Local GarageLog data is not changed by a failed cloud backup. Export JSON before using Restore if you are unsure.


## V2.3.4 vehicle ID cleanup
Existing vehicle IDs are normalized to V001, V002, V003, etc., and all Fuel, Maintenance, and Schedule references are updated consistently. New vehicles also receive sequential V### IDs.
