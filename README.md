# terracheck-snapshots

Static data snapshots for [TerraCheck](https://hughgingell2-collab.github.io/terracheck-screening/), served via
GitHub Pages. **Generated — do not edit.** Source pipeline: `terracheck-data` (`pipelines/export_snapshots.py` →
`pipelines/publish_snapshots.py`). Every publish is a history-free commit; the repo is a CDN, not a code repo.

| Path | What | Origin |
|---|---|---|
| `da/nsw-da-index.js` | Index of per-LGA Online DA bundles (all NSW councils), with normalised name keys | NSW Planning Portal Online DA Data API (open data) + council DA trackers (outcomes) |
| `da/nsw-da-<lga>.js` | Per-LGA bundle, schema v2 (`cols` + `rows`), 36-month lodgement window | as above |
| `cond/nsw-cond-<lga>.js` | Conditions extracted verbatim from Notices of Determination (where retrieved) | council DA trackers |
| `manifest.json` | Publish time, generator versions, file sizes | — |

Files are plain `registerRefData(key, {...})` JS so the app can load them by script injection from any origin.
Public government data only; provenance (source URL, retrieved_at, window) is inside every file.
