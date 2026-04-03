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

**How many job listings are on francetravail.fr?**
France Travail (formerly Pôle Emploi) is France's official national employment portal with over 700,000 active listings at any given time, covering all industries and regions.

**What contract types can I filter by?**
The actor supports filtering by CDI (permanent), CDD (fixed-term), MIS (temporary/interim), SAI (seasonal), LIB (freelance/self-employed), and REP (takeover). Leave blank to return all contract types.

**What location format should I use?**
Use department codes suffixed with D — e.g. `75D` for Paris, `69D` for Lyon, `13D` for Marseille. You can also pass a city name or region name.

**Does the actor include salary data?**
Yes. When `includeDetails` is enabled, the actor fetches the detail page for each listing and extracts structured salary data: minimum, maximum, currency, period (hourly/monthly/annual), and the raw salary text.

**Is it legal to scrape francetravail.fr?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash based on title, salary, location, and description. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

- **No official API access** — The actor scrapes the public HTML interface. France Travail has an official OAuth API, but it requires registration and has usage restrictions. The scraper works without credentials.
- **Contact details availability** — Phone numbers and email addresses appear on a minority of listings and depend on the employer's preferences. Expect nulls for most listings.
- **Skills extraction** — Skill tags are only present on listings where the employer explicitly structured them. Many listings have `null` for `skills` and `softSkills`.
- **Result limits** — France Travail caps search results at roughly 1,000–1,100 listings per query, even if more matches exist. Use location filters to narrow searches for large queries.
- **Dynamic availability** — Listings expire quickly on France Travail. A listing found during SERP collection may be unavailable by the time the detail fetch runs, resulting in a null description.

---

## Related products by Black Falcon Data

- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 04*
