# Fit-50
reporting tracker
Fit at 50 — Android folder backup + OneDrive sync
What this does
This PWA saves workout entries immediately in browser storage. When open and granted directory access, it also writes Fit_at_50_DEVICEID_latest.json into your chosen folder 12 seconds after edits, plus one dated JSON recovery copy per day. FolderSync (separate Android app) uploads the files to your personal OneDrive. The PWA does NOT itself confirm a OneDrive upload and cannot write files while closed. Permissions may require reauthorization after app restart.
Deploy and install
1. Host the files in this ZIP on an HTTPS site (e.g. GitHub Pages), without uploading any personal log JSON. Visit the URL in up-to-date Android Chrome and choose Install app.
2. In the installed PWA, open Backup & Export. Choose backup folder, create/select a dedicated accessible folder such as Documents/FitAt50Backups, and tap Write test backup now. Verify in Android Files that the Fit_at_50_..._latest.json and dated snapshot exist. If permission is refused or unavailable, use Download full JSON backup manually instead.
3. Import your previous workout log via Backup & Export > Import selected backup. This package deliberately contains no personal training history. Test writing again.
Configure FolderSync (third-party app, separate permissions)
1. Install FolderSync from its official site / trusted app store: https://foldersync.io/
2. Add your personal Microsoft OneDrive as a cloud account in FolderSync; only FolderSync receives that authorization.
3. Create a FolderPair: local folder = the EXACT same folder selected in the PWA; remote folder = OneDrive/Fit at 50/Gym Log Backups (create it if necessary). Direction To remote folder / Upload only. Avoid two-way sync and avoid delete propagation until backups are verified.
4. Set a schedule, e.g. every 1–3 hours, with Wi-Fi or connectivity constraints you prefer. Android background/battery restrictions may delay syncing. Run Sync now for the first test.
5. Open OneDrive separately and verify the latest JSON filename, modified time and contents, not just a FolderSync success message.
