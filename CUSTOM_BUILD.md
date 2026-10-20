# GitSync Custom

This fork adds a text-color button to the file editor's top bar. Enter a
six-digit hex color, such as `#E6E6E6`, preview it, and save. The setting applies
to all file text across repositories and survives reopening the app. Choose
Use default to restore the original syntax colors. Logs and diffs retain their
existing colors.

The Android app is named GitSync Custom. Its debug package is
`com.adamtcroft.gitsync.dev`, separate from the official app.

## Build and update

Run the Build GitSync Custom workflow on the `editor-text-color` branch.
Download the GitSync-Custom-arm64 artifact from the successful run and extract
its APK. The workflow uses a persistent personal debug signing key stored in
the repository's CUSTOM_DEBUG_KEYSTORE secret so future APKs can update the
same installation. This is a personal debug build, not a store release.

The build uses the empty OAuth configuration template. Use HTTPS with a token
or SSH; provider OAuth login requires registering your own OAuth clients.
Do not commit tokens, keys, or exported backups.

## Move settings from official GitSync

1. In official GitSync, open global settings, then Backup / Restore, then
   Encrypted backup. Save the backup with a password you keep locally.
2. Disable scheduled and app-triggered syncing in official GitSync before
   letting the custom app manage the same folders.
3. Install GitSync Custom and grant its own storage permissions. Complete any
   initial setup needed to reach global settings, then use Encrypted restore
   with that backup and password.
4. Check every repository's directory, remote, and authentication before
   enabling automatic syncing. Android accessibility, notification, battery,
   and folder permissions must be granted to the custom app separately.

The backup includes configuration, repository entries, and stored credentials.
It does not contain working files or Git history. Existing repositories in
shared storage can be reused if accessible; otherwise copy the complete folder
including `.git`, or clone again after preserving local changes. Restoring
multiple repositories goes through upstream's premium check. Store purchases
are not guaranteed to transfer to a separately identified custom app.

Migration is based on the backup/restore source and still needs verification
with the installed version and device. Keep the official app and its data until
the restored configuration has been checked.
