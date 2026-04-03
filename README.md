# France Travail Jobs Scraper

Extract structured data from [francetravail.fr](https://francetravail.fr) — francetravail.fr — France's official national job board. Salary ranges, skills, and contact data from 700 k+ listings.

**[France Travail Jobs Scraper on Apify →](https://apify.com/blackfalcondata/francetravail-scraper)**

---

## Key features

**Search with filters** — Search by keyword and location. Filter by contract type, and more.

**Detail enrichment** — Fetch full job descriptions, salary data, contact information for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

---

## Use cases

**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from francetravail.fr on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from francetravail.fr.

---

## Quick start

```json
{
  "query": "développeur",
  "maxResults": 50,
  "includeDetails": true
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Job title, skills, or keywords to search for. |
| `location` | string | — | Department code (e.g. 75D for Paris), city name, or region. |
| `contractType` | enum | `""` | Filter by contract type. |
| `maxResults` | integer | `25` | Maximum number of job listings to return (0 = unlimited). |
| `includeDetails` | boolean | `true` | Fetch detail page for each listing to get salary, skills, contact info, and full description. Slower but significantly richer data. |
| `descriptionMaxLength` | integer | `0` | Truncate job description to N characters. 0 = no truncation. |
| `compact` | boolean | `false` | Return core fields only — ideal for AI agents and MCP workflows. |
| `incrementalMode` | boolean | `false` | Only output new or changed listings compared to the previous run. |
| `stateKey` | string | — | Unique key to identify this tracked search universe (required when incrementalMode is true). |

---

## FAQ

<!-- WRITE: 4-6 Q&A pairs relevant to this product -->

**Is it legal to scrape francetravail.fr?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

<!-- WRITE: 4-6 honest limitations -->

- <!-- WRITE: limitation 1 -->
- <!-- WRITE: limitation 2 -->

---

## Related products by Black Falcon Data

- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 04*
