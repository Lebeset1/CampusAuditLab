# Audit Analytics Workbench

A free, browser-based training environment for internal audit students. It runs entirely in the browser — nothing is installed, no account is needed, and no data leaves the student's device.

The tool is designed as a stepping stone to the commercial packages students meet in practice (ACL / Diligent HighBond and CaseWare IDEA). It mirrors their shape: a ribbon of tests, a navigator of source tables, working-paper tabs, and an activity log that behaves like an audit trail.

## What students can do

**Data** — import their own **CSV or Excel** file (`.csv`, `.xlsx`, `.xlsm`, `.xls`), or work with the three built-in demo tables (vendor payments, vendor master, employee master). Workbooks with more than one sheet prompt for the sheet to import; Excel date cells are converted to `yyyy-mm-dd` on the way in.

**Prepare** — trim spaces, standardise case, dedupe rows, clean numeric fields, standardise dates, handle blanks, undo the last change.

**Analyse** — duplicate key detection, gap detection, stratification, summarisation, pivot tables, Benford's Law, aging, outlier detection.

**Cross-reference** — join or relate two tables, and draw random or systematic samples.

## The audit trail

Every operation is written to the activity log with the student's name, the parameters used, and the row counts before and after. **Export PDF** produces a read-only record:

- PDF permissions are set to allow printing only — no editing, copying or annotating
- every page carries the student's name, identifier, session ID and page number
- a SHA-256 fingerprint of the log content is stamped on the document, so a marker can confirm the listed steps are the ones that were run
- if the PDF library cannot load, the tool opens a print view instead and the student saves it as a PDF from there

## Files in this repository

| File | Purpose |
| --- | --- |
| `index.html` | The whole application. This is the file GitHub Pages serves. |
| `papaparse.min.js` | Local copy of the CSV parser (optional — a CDN copy is used if this is missing). |
| `README.md` | This file. |

The other libraries (SheetJS for Excel, jsPDF and jsPDF-AutoTable for the audit trail) load from a CDN. To run the tool fully offline, download these into the repository root alongside `index.html` and they will be used in preference to the CDN:

- `xlsx.full.min.js`
- `jspdf.umd.min.js`
- `jspdf.plugin.autotable.min.js`

## Publishing this

1. Create a free GitHub account and a new **public** repository.
2. Upload `index.html` and this `README.md`.
3. Go to **Settings → Pages**, set the source to **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
4. After a minute the site is live at `https://<your-username>.github.io/<repository-name>/`.

Share that link. Students open it on a phone, tablet, or laptop.

## Updating it

Upload a new `index.html` to the same repository. It replaces the old one and the URL never changes, so links already handed out keep working. Students may need to refresh once — or press Ctrl+F5 / Cmd+Shift+R — to clear the cached version.

## Requirements

An internet connection and any modern browser. The layout adapts to small screens — on phones the source tables and the activity log open as slide-over panels from the buttons in the top bar.

## A note on the sign-in screen

The name prompt is an identification label for the activity log, not authentication. It is stored in the browser only and is never transmitted. "Switch User" clears it for shared devices.
