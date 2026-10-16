# OncoLens local app

This is a working local research prototype based on the OncoLens PRD. It uses a small Node.js server (built-in modules only) to call public source APIs and serve the interface. No patient data should be entered.

## Run

1. Install Node.js 18 or later, if it is not already available.
2. Open a terminal in this folder.
3. Run `node server.js`.
4. Open `http://127.0.0.1:4173` in a browser.

The server binds only to `127.0.0.1`. It calls HGNC REST, NCBI E-utilities (PubMed), Europe PMC REST, and ClinicalTrials.gov API v2. Internet access is required for live results. Source APIs may rate-limit or change; the interface shows partial-source failures.

## Available now

- Gene, optional alteration, cancer type, and jurisdiction search.
- HGNC symbol/alias lookup for query normalization where available.
- Federated PubMed and Europe PMC literature search with citation metadata and abstract snippets.
- Filters for year, study type, open access, and sort order.
- ClinicalTrials.gov records, phase and status filters, direct NCT links, and source update dates.
- Starter drug/biomarker associations for EGFR, BRAF, ERBB2, KRAS, and NTRK; jurisdiction label is explicitly marked as not verified by this prototype. This is not a complete drug catalog.
- Source links for CIViC, OncoKB, FDA, EMA, CDSCO, ClinVar, and cBioPortal. Knowledge-base data is linked out; commercial licensing and access are not bypassed.
- Browser-local saved searches, update checks while the app is open, CSV/RIS export, and print-to-PDF reporting.

## Limits

This app is a prototype, not a clinical decision support system. Literature recall is not exhaustive, therapies are a limited starter catalog, drug status is not integrated with regulator feeds, and trial status should be confirmed in the registry. No AI-generated summaries, patient matching, CTRI integration, or accounts/cloud sync are implemented. Saved searches and update checks stay in the current browser; alerts only run while the app is open.

## Folder

- `index.html` – interface structure
- `styles.css` – visual design
- `app.js` – search UI, filters, local saves, and exports
- `server.js` – local static server and public-source API bridge
