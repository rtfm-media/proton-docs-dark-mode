# Proton Docs Dark Mode

**[Download the extension only](https://github.com/rtfm-media/proton-docs-dark-mode/releases/latest/download/darkmodedocs.xpi)**

A tiny, local-only Firefox extension that gives [Proton Docs](https://docs.proton.me)
a comfortable dark appearance while Proton's editor is still light-only.

It is tested in [Waterfox](https://www.waterfox.com/), but should also work in
[LibreWolf](https://librewolf.net/), Firefox ESR, Firefox Developer Edition, and
Firefox Nightly, version 140 or newer. Regular Firefox only installs extensions
permanently if Mozilla has signed them, and this one is not signed.

## What it does

- Applies a reversible dark visual treatment only on `docs.proton.me`.
- Leaves images, video, and canvases in their intended colours.
- Keeps inline `currentColor` SVG interface icons light and preserves dark
  elevation shadows across Proton's UI.
- Lets you toggle the effect from the toolbar popup or with
  <kbd>⌘</kbd>/<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>D</kbd>.

## Privacy

This extension is deliberately boring:

- no network requests
- no analytics
- no background process
- no reading, changing, or sending of document contents
- one local browser setting: whether the effect is enabled

Its only site permission is `https://docs.proton.me/*`.

## Install in Waterfox

1. Open `about:addons`.
2. Click the gear icon and choose **Install Add-on From File…**.
3. Pick the downloaded `.xpi` file and confirm the install. Waterfox warns that
   the add-on cannot be verified. This is expected because Mozilla has not
   signed it.

## Install in LibreWolf, Firefox ESR, Firefox Developer Edition, or Firefox Nightly

1. Open `about:config` and accept the warning.
2. Search for `xpinstall.signatures.required` and set it to `false`.
3. Open `about:addons`.
4. Click the gear icon and choose **Install Add-on From File…**.
5. Pick the downloaded `.xpi` file and confirm the install.

## Use it

Open [Proton Docs](https://docs.proton.me). The dark mode is on by default.

The extension's button is in the Extensions menu, the puzzle piece icon in the
toolbar. Pin it to the toolbar from there if you want it in view. Click it to
turn the dark mode on or off. Changes apply to open Docs tabs straight away.

## How it works

Proton Docs is a moving target internally, so this extension avoids brittle
editor-specific selectors. It applies a display-only filter to the page,
reverses that treatment for raster media, and corrects each rendered shadow's
colour while retaining its original size and opacity. This keeps the extension
small, resilient, and content-safe.

## Caveat

This is a visual inversion, not a theme implemented by Proton. A rare embedded
widget or unusual image effect may look imperfect; use the toggle to disable it
for that view.

## Make the install file yourself

1. Open this repository's folder.
2. Select every file inside it, not the folder itself, and compress them into a
   zip file.
3. Rename the zip file so it ends in `.xpi`, for example `darkmodedocs.xpi`.

## Development

To test changes without making an `.xpi` file, load the folder as a temporary
add-on:

1. Open `about:debugging`.
2. Click **This Firefox** in the sidebar. Other browsers show their own name
   there, such as **This Waterfox**.
3. Click **Load Temporary Add-on…** and pick `manifest.json` in this folder.

After modifying a file, click **Reload** on the add-on's card, then refresh
Proton Docs. The temporary add-on is removed when the browser closes. No build
step or dependencies are required.
