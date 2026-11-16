# Gather v1.0.3

iPhone PWA / GitHub Pages

## Changes
- Backup export now displays the complete JSON with a copy fallback.
- Recipe form clears and displays confirmation after save.
- Manual Sync now merges custom recipes by ID without overwriting cloud preferences or plans.
- Automatic cloud writes disabled for safety while sync is being repaired.
- Last pre-sync snapshots are retained in localStorage (gatherPreSyncBackupV101 and gatherCloudPreSyncBackupV101).

**Important:** Export a backup from each device before using Sync now. Recipe edits with the same ID but different content pause synchronization. Deletions and non-recipe changes do not sync in this release.

## v1.0.3 fixes
- Corrects preference chip element IDs during rendering, including after cloud sync.
- Explicit Supabase auth session persistence and session restoration.
- Displays local/cloud recipe names and IDs when a conflict pauses sync.
- Keeps automatic cloud overwrites disabled; export both backups before resolving conflicts.
