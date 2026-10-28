# Gather — iPhone-ready web app (PWA)

**Current version: v1.0.0**


This folder is a deployable Progressive Web App version of Gather. It reuses the existing meal planner and adds iPhone layout refinements, a web app manifest, app icons, and a service worker for caching the app shell.

## Important: hosting is required

An iPhone can install a Home Screen web app only from a secure website (HTTPS), except for local development. This folder is not yet published to the internet. You can host it from Windows 11 using a static host such as GitHub Pages, Cloudflare Pages, or Netlify. Upload the **contents of this `gather-pwa` folder** as the site root, not the parent Windows/Electron project.

### Easy deployment outline

1. Create a site/project with a static host.
2. Upload `index.html`, `manifest.webmanifest`, `service-worker.js`, and the `icons` folder preserving their relative paths.
3. Wait for the host to publish an HTTPS URL.
4. On iPhone, open that URL in **Safari**.
5. Tap **Share → Add to Home Screen**. If offered, enable **Open as Web App**, then tap Add.
6. Launch Gather from the new Home Screen icon. Open it once online so the service worker can cache the app shell for later offline use.

## Local testing on Windows

Service workers do not register from `file://` URLs. Serve this folder over localhost instead. With Node.js installed, open Command Prompt in this folder and run:

```bat
npx --yes http-server -p 8080
```

Then open `http://localhost:8080` in your PC browser. This tests the web app locally, but the phone installation still needs an HTTPS-hosted URL reachable from the phone.

## Data and privacy

- Recipes, plans, preferences, and checked grocery items are stored in browser local storage on that device/origin.
- There is no account, server-side database, or automatic sync. The iPhone's PWA storage is separate from the Windows Electron app and from ordinary browser storage in some cases.
- Use **Preferences → Export backup** before clearing browser data or moving devices. Use **Import backup** to restore a JSON backup.
- The service worker caches the app shell for offline launch after the first successful online visit. Browser storage can still be cleared by iOS, so keep backups of important recipes.

## Updating the PWA

Upload the changed files to your host. When changing cached assets, increment `CACHE_VERSION` in `service-worker.js` (for example, `gather-shell-v2`) so devices replace the old cache. A service worker update may take a reload or two to activate.

## Current limitations

- This is a personal-use web app, not an App Store application.
- Sync is optional and uses Supabase. Both devices must use the same project and account; first sync requires choosing whether to use cloud data or upload that device.
- Only the app shell is cached; there are no external images or APIs in the current app. Offline behavior should be tested on the target iPhone after deployment.
- The recipe library is starter data. Several recipes use generated general cooking guidance rather than fully tested recipe steps.
