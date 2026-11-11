# Buoy Board

Live NOAA buoy readings, tide stations, VHF weather radio channels and marine forecast zones from the Gulf of Maine to the Caribbean. Built for boat captains and delivery skippers.

This repository hosts the app free on GitHub Pages. A GitHub Action republishes the site every 15 minutes with a fresh copy of NOAA's buoy observations, so the app can show live readings without a separate server.

## Files

| File | What it does |
| --- | --- |
| `index.html` | The whole app: My Stations, Stations, Tides, WX Radio |
| `manifest.webmanifest`, `icons/` | App name, colors and icons, so phones can install it |
| `sw.js` | Offline support |
| `privacy.html` | Privacy policy (required by Google Play and Apple) |
| `.github/workflows/deploy.yml` | Publishes the site and refreshes NOAA data every 15 minutes |
| `assetlinks.json` (add later) | Android app link file from PWABuilder |
| `CNAME` (optional) | Your custom domain, one line, e.g. `buoyboard.app` |

## Set up (about 15 minutes, all in the browser)

1. **Create the repository.** On GitHub, click **+ → New repository**. Name it `dscottpoii.github.io` so the app is served at the top of the address (`https://dscottpoii.github.io/`). Android app links require that. Make it **Public** and click **Create repository**.
2. **Upload the files.** Click **uploading an existing file**. Drag in everything from this folder except the `.github` folder (the web uploader can skip folders whose names start with a dot). Click **Commit changes**.
3. **Add the publishing workflow.** Click **Add file → Create new file**. In the name box type `.github/workflows/deploy.yml` (the slashes create the folders). Paste in the contents of `deploy-workflow.yml` (it comes in the download next to this folder; open it in Notepad or TextEdit) and click **Commit changes**.
4. **Turn on Pages.** Go to **Settings → Pages**. Under **Source**, choose **GitHub Actions**.
5. **Run it once.** Go to the **Actions** tab, click **Publish Buoy Board → Run workflow**. After about a minute the run turns green.
6. **Test on your phone.** Open `https://dscottpoii.github.io/`, go to My Stations, and tap **Pin a Chesapeake sample**. Live wind and pressure for Thomas Point should appear.

## Updating the app

Edit a file on GitHub (pencil icon) and commit. The site republishes within a minute or two. If you change `index.html`, also raise the version in `sw.js` (`buoyboard-gh-v1` to `buoyboard-gh-v2`) so installed apps pick up the change.

## Things to know

- **Data freshness.** The buoy file refreshes every 15 minutes, but GitHub sometimes runs scheduled jobs late. NOAA's own readings are 20–60 minutes old anyway, and the app shows each reading's age.
- **Keep it active.** GitHub pauses scheduled workflows after 60 days with no changes to the repository. It emails a warning first. Click **Enable workflow** in the Actions tab or commit any small change to keep it running.
- **Android app link.** When PWABuilder gives you `assetlinks.json`, upload it to the top of this repository (not in a folder). The workflow publishes it at `/.well-known/assetlinks.json` automatically.
- **Custom domain.** Add a file named `CNAME` containing just your domain, enter the same domain under **Settings → Pages → Custom domain**, and point your DNS at GitHub Pages.

Buoy Board is not affiliated with NOAA or the National Weather Service. Always confirm conditions with official forecasts before getting underway.
