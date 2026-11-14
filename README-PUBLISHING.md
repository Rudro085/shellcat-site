# ShellCat website (draft)

Static GitHub Pages site: `index.html` (landing page, downloads, installation)
and `manual.html` (user manual). No build step, no external dependencies.

## 1. Screenshots

`screenshots/` contains real captures of the ShellCat interface with fictional demo
data (example.com hosts, a demo Teleport cluster, a generated diagnosis report).
The landing page uses `hero.png`, `diagnosis-findings.png`, `script-palette.png` and
`teleport-servers.png`; the manual uses all twelve. To replace one, overwrite it with
a 1600 × 1000 PNG of the same name, and keep real hostnames, IPs and cluster names out of it.

## 2. Check the download links

Download buttons point at
`https://github.com/Rudro085/ShellCat-go/releases/latest/download/<file>`.
The repository and file names are set in one place, the `<script>` block at the
bottom of `index.html`:

```js
const REPO = 'Rudro085/ShellCat-go';
const ASSETS = {
  windows: 'ShellCat-go-amd64-installer.exe',   // wails build -nsis
  windowsPortable: 'ShellCat-go.exe',
  linuxDeb: 'shellcat_amd64.deb',
  linuxTar: 'ShellCat-go-linux-amd64.tar.gz',
};
```

Upload release assets with exactly these names (or edit the names), and mark the
release as *latest*. Remove a button from `index.html` if you don't ship that package.
The Linux instructions mention the `.deb` and portable tarball; adjust them if you
publish something else (e.g. an AppImage).

## 3. Publish

This folder is git-ignored so drafts never get committed by accident. To publish
with GitHub Pages from the main branch:

1. Copy (or rename) this folder to `docs/` in the repository and commit it.
2. On GitHub: **Settings → Pages → Build and deployment → Deploy from a branch**,
   choose your branch and the `/docs` folder.
3. The site appears at `https://rudro085.github.io/ShellCat-go/`.

The `.nojekyll` file makes GitHub serve the files as-is.

## Preview locally

Open `index.html` in a browser, or run `python -m http.server` in this folder and
visit http://localhost:8000.
