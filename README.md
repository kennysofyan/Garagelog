# GarageLog iOS V2.3

Personal, local-first vehicle fuel and maintenance tracker.

## V2.3 additions

- Google Sheets cloud backup connector
- Backup the complete GarageLog database to a Google Sheet
- Restore the complete database from the Google Sheet
- Human-readable Vehicles, Fuel, Maintenance and Schedules tabs are created automatically
- Local storage remains the primary working storage, so the app still works offline
- JSON export/import remains available as an additional backup method
- Existing V2.2 features are retained: multiple cars, editable/deletable fuel and service records, maintenance intervals, due status, fuel economy, cost summary, and PWA support

## Important: Google backup is optional

GarageLog does not require Google backup. If you do not configure it, the app works like V2.2 using local browser storage.

## Set up Google Sheets backup

### 1. Create the Google Sheet

Create a new Google Sheet, for example:

`GarageLog Cloud Backup`

### 2. Open Apps Script

In the Google Sheet:

**Extensions → Apps Script**

Delete the default code and paste the contents of:

`GarageLog_GoogleAppsScript.gs`

### 3. Set your private sync key

At the top of the Apps Script, change:

`CHANGE-THIS-TO-A-LONG-RANDOM-PRIVATE-KEY`

to a long random phrase that only you know.

Example:

`GarageLog-2026-MyPrivateBackup-7f4K9x2P`

Do not publish this key anywhere else.

### 4. Deploy the script

In Apps Script:

**Deploy → New deployment**

Select:

- Type: **Web app**
- Execute as: **Me**
- Who has access: **Anyone**

Click **Deploy** and copy the Web app URL ending in `/exec`.

### 5. Connect GarageLog

Open GarageLog:

**Tools & data → Google backup**

Enter:

- Google Apps Script Web App URL
- The same private sync key

Tap **Save connection**.

### 6. Back up

Tap:

**Back up to Google**

GarageLog will write:

- `GarageLog_Backup` — full-fidelity JSON backup
- `Vehicles` — vehicle list
- `Fuel` — fuel history
- `Maintenance` — service history
- `Schedules` — maintenance intervals

The full JSON backup is the authoritative restore source. Do not manually edit the JSON in `GarageLog_Backup!A1`.

## Restoring

Before restoring, it is recommended to use **Export backup** to save a local JSON copy.

Then:

**Tools & data → Google backup → Restore from Google**

The cloud copy will replace the GarageLog data stored on that device.

## Security model

The Google Sheet is yours. GarageLog does not send vehicle data to a third-party GarageLog server.

The Apps Script web app is an endpoint that can be reached by URL, so the sync key is used as an additional application-level check. Keep the Web App URL and sync key private. This is intended for personal use, not as a multi-user production database.

## Offline behavior

Local storage remains the primary working database. You can add and edit records without internet access. Google backup requires internet access.

## PWA installation

Host the app on HTTPS, such as GitHub Pages. On iPhone Safari:

**Share → Add to Home Screen → Open as Web App**

## Important backup advice

Keep at least one JSON export occasionally even if Google backup is enabled. The safest arrangement is:

1. Local GarageLog data
2. Google Sheet backup
3. Occasional JSON export

Do not upload your JSON backup to the public GitHub repository.
