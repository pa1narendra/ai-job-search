# Search Queries for Job Scraper

<!-- Primary target: REMOTE-GLOBAL roles open to India. Secondary: Indian portals. -->
<!-- Configured for Pavan Narendra Peela: Full Stack / Backend / Frontend SWE -->
<!-- (React, Next.js, Node.js, TypeScript, MongoDB, Redis), ~2 yrs. -->

## Strategy

Pavan's priority is **remote roles that hire globally / from India, pay well, and work in English.**
Run **Section A (remote-global) first and by default.** Run Section B (Indian portals) only on
request (e.g. `/scrape india`) or as a secondary net.

**Why remote-first:** the remote-first boards expose OPEN APIs / RSS feeds that return full job
data with no anti-bot blocking — unlike Naukri/LinkedIn/Wellfound, which block automated fetch.
So remote roles can be auto-read end-to-end (fit score + tailored CV/cover letter) with no pasting.

---

## Section A: Remote-Global Sources (PRIMARY — fetchable, no blocking)

Fetch these directly with `WebFetch`. They return JSON/RSS with full descriptions.

| Source | Endpoint | Notes |
|--------|----------|-------|
| **RemoteOK** | `https://remoteok.com/api` | JSON. Sorted by date (noisy). Filter by tags + location. Also `https://remoteok.com/api?tags=react,node` |
| **Remotive** | `https://remotive.com/api/remote-jobs?category=software-dev` | JSON. `category=software-dev` is the clean filter. (Its `search=` param is unreliable — filter in the prompt instead.) |
| **We Work Remotely** | `https://weworkremotely.com/categories/remote-full-stack-programming-jobs.rss` | RSS. Also `remote-back-end-programming-jobs.rss`, `remote-front-end-programming-jobs.rss`. Cleanest "Anywhere in the World" tagging. |
| **Himalayas** | `https://himalayas.app/jobs/api` | JSON. Best region/timezone metadata; try larger `?limit=` and paginate. |
| **HN "Who is Hiring"** | `http://hn.algolia.com/api/v1/search_by_date?query=remote%20react%20node&tags=comment` | Monthly thread; open Algolia API; direct-to-company, often async-friendly. |

### The CRITICAL filter: India eligibility

Most "remote" roles are region-locked. For every role, classify candidate location into:
- ✅ **ELIGIBLE** — "Anywhere in the World", "Worldwide", "Global", "Remote - India", "Asia", or explicitly lists India
- ⚠️ **CHECK** — vague "Remote" with a US/EU company (verify by fetching the full JD before recommending)
- ❌ **SKIP** — "US only", "US-authorized", "EU only", "LATAM only", "must be in <country>" (no India)

**Only present ELIGIBLE and CHECK roles. Never present SKIP roles as matches.**

### Stack + level filter

- **Match stack:** JavaScript, TypeScript, React, Next.js, Node.js, NestJS, Express, MongoDB, Redis, PostgreSQL
- **Level:** target roles for ~1-4 years / "Software Engineer", "Mid-level", "II", "Full Stack Engineer". Flag (don't auto-skip) "Senior"/"Lead"/"Staff"/"III"/"7+ yrs" as stretch.
- **English:** all roles must be English-working. Skip roles requiring another working language.

### Vetting marketplaces (track separately — apply once, get matched)

Not scraped per-search. These place Indian devs into US/EU-remote contracts. See `marketplace_profile.md`.
- **Lemon.io**, **Arc.dev**, **Turing**, **Braintrust**, **Gun.io** (primary for ~2 yrs)
- **Toptal** (stretch — very selective, wants 3+ yrs)

---

## Section B: Indian Portals (SECONDARY — run on `/scrape india`)

Search via `WebSearch` (discovery works; full JD fetch is BLOCKED on these — user pastes JD for deep-dive).

- **naukri.com**, **linkedin.com/jobs**, **wellfound.com**, **instahyre.com**

### Queries

```
site:naukri.com "full stack developer" (React OR Next.js) Node.js Hyderabad
site:linkedin.com/jobs "software engineer" "React" "Node.js" India remote
site:wellfound.com "full stack" OR "node.js" engineer India remote
site:naukri.com "node.js developer" (MongoDB OR Redis) Hyderabad OR Bengaluru OR Pune
```

### Locations (for Indian roles)
- **Primary:** Hyderabad; **also:** Bengaluru, Pune, Chennai, Delhi NCR, Mumbai; **plus:** remote (India)

---

## Filters & Deal-breakers (apply to ALL sources)

- Salary target **9-15 LPA** (Indian roles) / for remote-global, aim well above via USD pay; flag clearly-low comp.
- **Skip** roles centered on 24x7 on-call / production-support.
- **Skip** primarily non-JS legacy stacks (.NET-only, PHP-only, legacy-Java-only with no React/Node).
- Only open postings; skip expired deadlines.

## Date Filter (DEFAULT: last 7 days — freshness drives conversion)

**Default: only present postings from the last 7 days.** Fresh postings convert far better — you
apply before the role is flooded. Apply this strictly:

- The remote APIs carry a publication date: RemoteOK `epoch`/`date`, Remotive `publication_date`,
  We Work Remotely RSS `pubDate`, Himalayas `pubDate`/`publishedAt`. **Filter on these; keep only
  roles posted within the last 7 days.** Sort newest-first and lead with the freshest.
- If a date genuinely can't be determined, include it but flag "date unknown" and rank it below dated roles.
- Widen only on request: `/scrape 14d`, `/scrape 30d`, "last two weeks", "last month". Plain
  `/scrape` = last 7 days.

## Adapting Queries

- `/scrape` or `/scrape remote` → Section A (default)
- `/scrape india` → Section B
- `/scrape backend` → bias toward Node.js/MongoDB/Redis/API roles in whichever section
- `/scrape broad` → run both sections
