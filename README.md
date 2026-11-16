# Gather v1.0.7-test-preferences-cleanup

iPhone/browser PWA

## Changes
- Recipe synchronization uses last-update-wins for additions, edits, and deletions.
- Each edited recipe receives an `updatedAt` timestamp; deleted recipes leave a persistent tombstone.
- Manual Sync now reconciles both devices without stopping on ordinary edits.
- The test reset still requires two-device coordination.
- Starter recipes are seeded once and are editable, deletable, and synchronized like every other recipe.

## Important
Export a backup from both devices before upgrading. Update both devices before testing deletion.
Manual Sync is still required; the device clocks must be reasonably accurate.
Supabase writes are not transactionally protected against simultaneous syncs.

### v1.0.7 Preferences cleanup
Cloud setup fields appear only when disconnected; account credentials appear only when signed out. Signed-in users see Sync now, Sign out, and Disconnect Supabase. Disconnect affects only this device and preserves local recipes.
