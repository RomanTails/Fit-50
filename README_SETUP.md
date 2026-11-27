# Fit at 50 — Android folder backup + OneDrive sync

## What this does
This PWA saves workout entries immediately in browser storage. When open and granted directory access, it also writes `Fit_at_50_DEVICEID_latest.json` into your chosen folder 12 seconds after edits, plus one dated JSON recovery copy per day. FolderSync (separate Android app) uploads the files to your personal OneDrive. The PWA does NOT itself confirm a OneDrive upload and cannot write files while closed. Permissions may require reauthorization after app restart.

## Deploy and install
1. Host the files in this ZIP on an HTTPS site (e.g. GitHub Pages), without uploading any personal log JSON. Visit the URL in up-to-date Android Chrome and choose Install app.
2. In the installed PWA, open Backup & Export. Choose backup folder, create/select a dedicated accessible folder such as `Documents/FitAt50Backups`, and tap Write test backup now. Verify in Android Files that the `Fit_at_50_..._latest.json` and dated snapshot exist. If permission is refused or unavailable, use Download full JSON backup manually instead.
3. Import your previous workout log via Backup & Export > Import selected backup. This package deliberately contains no personal training history. Test writing again.

## Configure FolderSync (third-party app, separate permissions)
1. Install FolderSync from its official site / trusted app store: https://foldersync.io/
2. Add your personal Microsoft OneDrive as a cloud account in FolderSync; only FolderSync receives that authorization.
3. Create a FolderPair: local folder = the EXACT same folder selected in the PWA; remote folder = `OneDrive/Fit at 50/Gym Log Backups` (create it if necessary). Direction **To remote folder / Upload only**. Avoid two-way sync and avoid delete propagation until backups are verified.
4. Set a schedule, e.g. every 1–3 hours, with Wi-Fi or connectivity constraints you prefer. Android background/battery restrictions may delay syncing. Run Sync now for the first test.
5. Open OneDrive separately and verify the latest JSON filename, modified time and contents, not just a FolderSync success message.

## End-to-end test
1. Enter a harmless test set in the tracker. Wait around 12–20 seconds while the PWA stays open.
2. The Backup & Export page should say `Local backup saved`; Android Files should show the JSON updated. If it instead says `Permission needed`, tap Reauthorize folder, then Write test backup now.
3. Run the FolderPair using FolderSync's Sync now command.
4. Verify the corresponding filename and new timestamp under OneDrive > Fit at 50 > Gym Log Backups. Download a copy and confirm the test set is present in the `data.entries` JSON object.
5. Keep your original historical backup until you have successfully tested restoration from a synced backup.

## Important boundaries
- Local browser entries and saved folder files are distinct. If a folder write fails, the local log may still be saved, but the cloud copy will be stale.
- Choose a normal user Documents folder, not Android/data or the root storage folder.
- No automatic sync occurs after closing the PWA; FolderSync may upload previously written files in the background.
- FolderSync upload is one-way BACKUP, not two-way synchronization of workouts between phone and Surface Pro.
- Daily recovery snapshots are created only on days when the PWA actually writes a backup. Save manual backups periodically.
- File permissions on Android may not persist between PWA launches. Use the visible status and Reauthorize folder control; do not assume success.
- On some Android devices/Chrome versions, the file picker or write access may not be usable. The manual JSON export option remains available.
