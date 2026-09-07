# GarageLog iOS V2.2

V2.2 adds full fuel/service record management:
- Edit fuel records
- Delete fuel records
- Edit service / maintenance records
- Delete service / maintenance records
- Recent activity history with Edit/Delete actions
- Dashboard totals, fuel economy, and maintenance tracking recalculate automatically after changes
- Existing multi-car, maintenance interval, cost summary, backup/import, and PWA features retained
- Service-worker cache bumped to V2.2

## Update GitHub Pages
1. Extract this ZIP.
2. Open your GarageLog GitHub repository.
3. Upload/replace the files in the repository root: `index.html`, `sw.js`, `manifest.webmanifest`, `icon-180.png`, and `README.md`.
4. Commit the changes.
5. Wait for GitHub Pages to deploy.

Do **not** upload your GarageLog backup JSON to GitHub. Your records remain in browser local storage.

If the old version remains on an iPhone Home Screen app, close it and reopen it after deployment. If necessary, remove the Home Screen shortcut and add the site again from Safari.
