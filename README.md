# Ring General — Wrestling Notes

A mobile-first app for planning wrestling matches: match structure notes,
reusable sequences, and your move set. Built as a progressive web app (PWA) —
no app store, installs straight to your phone's home screen and works offline.

## What's in it

- **Matches** — full match structure notes, for planning live show matches.
- **Sequences** — reusable spots filed as **Heel Heat**, **Comeback**, or
  **Finish** ideas.
- Matches and sequences are both grouped by match type: **Singles**, **Tag**,
  or **Triple Threat** (filter chips at the top).
- **Move Set** — your moves, categorised as **High Impact**, **Fake Finish**,
  or **Finish**.
- Search within a tab, and JSON export/import for backups or moving devices.

## Running it

It's a static site — no build step, no dependencies.

- **GitHub Pages (recommended):** in this repo's Settings → Pages, set the
  source to the `main` branch, root folder. Open the published URL on your
  phone, then use your browser's **Add to Home Screen** — it installs like a
  native app and works offline afterwards (a service worker caches the app
  shell).
- **Locally:** serve the folder with any static server, e.g.
  `python3 -m http.server`, and open `http://localhost:8000`.

## Where notes are stored

- **GitHub sync (recommended):** in the app, open **⋮ → Set up GitHub sync**.
  Notes are saved to a JSON file in a GitHub repo you own (default:
  `data/notes.json` in this repo) — private, versioned, and shared by every
  device you set it up on. Deletes sync too (tombstones), edits merge per
  note by last-write-wins, and offline changes queue up and sync when you're
  back online.

  You'll need a fine-grained personal access token from
  [github.com/settings/personal-access-tokens](https://github.com/settings/personal-access-tokens/new):
  give it access to **only** the notes repo, with **Contents: Read and
  write**. Paste it into the app once per device. The token is kept in that
  browser's storage, so don't set this up on a shared device.

- Without sync configured, notes live in the browser's `localStorage` on that
  device — use **⋮ → Export** now and then for a backup. (Opened as a
  published Claude artifact, the app instead stores notes in the artifact's
  database.)

- First run shows a few notes tagged **Example** — delete them like any other
  note once you've seen how things are laid out.

## Files

- `index.html` — the whole app (markup, styles, logic; no framework).
- `manifest.webmanifest`, `sw.js`, `icons/` — PWA install and offline support.
