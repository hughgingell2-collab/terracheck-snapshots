# terracheck-snapshots

Static data snapshots for [TerraCheck](https://hughgingell2-collab.github.io/terracheck-screening/), served via
GitHub Pages. **Generated — do not edit.** Source pipeline: `terracheck-data` (`pipelines/export_snapshots.py` →
`pipelines/publish_snapshots.py`). Every publish is a history-free commit; the repo is a CDN, not a code repo.

| Path | What | Origin |
|---|---|---|
| `da/nsw-da-index.js` | Index of per-LGA Online DA bundles (all NSW councils), with normalised name keys | NSW Planning Portal Online DA Data API (open data) + council DA trackers (outcomes) |
| `da/nsw-da-<lga>.js` | Per-LGA bundle, schema v2 (`cols` + `rows`), 36-month lodgement window | as above |
| `cond/nsw-cond-<lga>.js` | Conditions extracted verbatim from Notices of Determination (where retrieved) | council DA trackers |
| `activity/nsw-lga.json`, `activity/nsw-sal.json`, `activity/manifest.json` | DA activity per LGA and per suburb (ABS ASGS 2021 SAL): lodged/determined in 6/12/24-month windows from `as_of`, outcome mix, themes, cost, dwellings, cl 4.6, storeys, index — contract `SPEC-2026-08-23-activity-schema.md` in terracheck-screening | Online DA Data API + outcome join; ABS ASGS 2021 polygons for the SAL assignment |
| `dcp/nsw-dcp-index.json`, `dcp/nsw-<lga>.json` | Per-LGA DCP corpus: every council's development control plan PDFs (url, sha256, pages, applies_to for amalgamated areas) + residential controls extracted deterministically with a verbatim quote, page and section ref (`review_status: auto`, not human-verified; DCPs guide rather than bind — EP&A Act s 4.15(3A)) | NSW Planning Portal statewide DCP list + council websites (`pipelines/dcp.py`) |
| `manifest.json` | Publish time, generator versions, file sizes | — |

`da/` and `cond/` files are plain `registerRefData(key, {...})` JS so the app can load them by script injection from any origin; `activity/` and `dcp/` are JSON (fetch with CORS — GitHub Pages allows any origin).
Public government data only; provenance (source URL, retrieved_at, window) is inside every file.
