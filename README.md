# MARROW — releases

This repository is the update channel for the MARROW server at https://marrow.framebound.win.

- `release/app.js` — the newest server file (the whole game, website and co-op server in one file).
- `release/latest.json` — which build that is, its size and SHA-256.

The server checks `release/latest.json` every 10 minutes. When the build changes it downloads `release/app.js`,
checks the size, the SHA-256 and a test start, keeps the old file as `server.js.bak`, and restarts when nobody is
playing. A broken or incomplete download is never installed.

To publish a patch: replace both files in `release/` with the ones from `server/build/release/` and commit.
To pause updates on the server: put `update.json` next to `server.js` containing `{ "enabled": false }`.
