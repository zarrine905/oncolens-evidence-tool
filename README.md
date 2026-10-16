# OncoLens

**Gene and cancer evidence discovery for oncology teams.** Search a gene, optional variant, and cancer type to explore research literature, trial records, and a small, clearly labeled therapy reference catalog.

> **Research prototype · Not for clinical decision-making**  
> OncoLens is an early evidence-discovery prototype. It is not a medical device or clinical decision-support system, and it does not recommend or select treatment. Verify findings in their original sources and against current institutional guidance. **Do not enter patient-identifiable or protected health information.**

<img width="1474" height="696" alt="image" src="https://github.com/user-attachments/assets/2286227d-1aed-439c-a69c-2cefa31fe2f5" />


## What you can do

- **Search a gene and context:** enter a gene symbol, optional alteration, cancer type, and regulator region. HGNC symbol and alias lookup helps normalize gene names when available.
- **Explore publications:** retrieve citation metadata and available abstract text from PubMed and Europe PMC, with source links, basic filters, and deduplication where possible.
- **Review trial records:** search ClinicalTrials.gov and inspect phase, status, interventions, and registry update details through direct NCT links.
- **Check starter therapy associations:** view a limited biomarker-to-drug catalog for selected EGFR, BRAF, ERBB2, KRAS, and NTRK queries, with links to regulator and knowledge-base sources for verification.
- **Keep and share research:** save searches in the current browser, check them for new literature while the app is open, export citations as CSV or RIS, and print a report to PDF.

OncoLens links to resources such as CIViC, OncoKB, ClinVar, cBioPortal, and regulator sites. These links do not mean their records are imported, complete, or licensed for reuse in this prototype.

## Run locally

**Requirements:** Node.js 18 or later and an internet connection. The app uses Node's built-in modules and needs no package installation.

1. Download or clone this repository.
2. From the project folder, start the server:

   ```bash
   node server.js
   ```

   On Windows, you can instead double-click `run.bat`.
3. Open [http://127.0.0.1:4173](http://127.0.0.1:4173).

The server binds to **127.0.0.1** (your local machine). Live search requires outbound internet access to the public sources listed below. Source services may be slow, unavailable, or rate-limited; results may be partial when a source is unavailable.

## Example searches

- `EGFR` + non-small cell lung cancer
- `BRAF V600E` + melanoma
- `NTRK1 fusion` + a selected cancer type

These are research-query examples, not treatment recommendations.

## Data sources

| Source | Used for | Notes |
| --- | --- | --- |
| [HGNC REST](https://www.genenames.org/help/rest/) | Gene symbol, name, and aliases | Normalization may be unavailable for some inputs. |
| [NCBI PubMed E-utilities](https://www.ncbi.nlm.nih.gov/books/NBK25501/) | Publication search, citation details, and available abstracts | Results depend on the query and page size. |
| [Europe PMC REST](https://europepmc.org/RestfulWebService) | Publications, abstracts, open-access and preprint metadata | May overlap with PubMed; records are deduplicated where possible. |
| [ClinicalTrials.gov API v2](https://clinicaltrials.gov/data-api/about-api) | Trial records, status, phase, and interventions | Confirm current status on the registry record. |
| CIViC, OncoKB, ClinVar, cBioPortal, FDA, EMA, CDSCO | Linked reference and regulator resources | Opened as source links; not complete integrated or independently validated feeds. |

Check each result at its linked source. Sources have their own terms, update schedules, and reuse conditions. This project does not bypass subscriptions or access restrictions.

## Important limitations

- Literature retrieval is query-based and **not exhaustive**. Synonyms, variant formatting, indexing, and cancer terminology can affect recall. Ranking and filters use basic prototype logic and are not a validated evidence-ranking system.
- Abstract snippets are source text, not AI-generated summaries. OncoLens does **not** generate AI summaries or adjudicate evidence quality.
- The therapy catalog is a small set of starter associations, not a comprehensive drug database. Regulatory status is explicitly unverified; approvals vary by jurisdiction, indication, biomarker, and date. Follow the regulator link and check the current product label.
- Knowledge-base annotations and clinical guidelines are not fully integrated. A missing result does not mean evidence or a treatment option does not exist.
- Trial data comes from ClinicalTrials.gov only; CTRI and other registries are not integrated.
- Saved searches live in browser storage on the current device. Update checks run only while the app is open; there are no accounts, cloud sync, or background notifications.
- Patient matching, patient data storage, and clinical decision support are not implemented.

## Privacy and data flow

The app has no sign-in or cloud database. Search requests go from the local server to HGNC, NCBI, Europe PMC, and ClinicalTrials.gov to retrieve public records. Saved searches stay in browser-local storage. Do not enter patient data, identifiers, or confidential institutional information.

## Project files

- `index.html` — application interface
- `styles.css` — visual styles
- `app.js` — search interface, filters, local saved searches, and exports
- `server.js` — local web server and public-source API bridge
- `run.bat` — Windows launch helper

## Contributing and licensing

Bug reports and suggestions are welcome through GitHub Issues. Do not include patient information in issues or examples. When proposing clinical evidence or therapy content, include the primary source and the date checked.

**License:** this repository currently has no license file. Public visibility alone does not grant permission to reuse or redistribute the code. Add a license if you want to grant those rights.

---

OncoLens is an evidence-discovery aid for research and education only. It does not replace professional judgment, molecular tumor board review, current guidelines, regulatory labeling, or consultation of the original evidence.


## Screenshots

The screenshots below show the same molecular query across OncoLens evidence views.

| Search overview | Published literature |
| --- | --- |
| ![OncoLens search for BRAF V600E in melanoma](Screenshot%202026-10-16%20125644.png) | ![OncoLens literature results](Screenshot%202026-10-16%20125717.png) |

| Targeted therapy evidence | Knowledge annotations |
| --- | --- |
| ![OncoLens targeted therapy evidence](Screenshot%202026-10-16%20125733.png) | ![OncoLens knowledge annotations](Screenshot%202026-10-16%20125816.png) |
