# Job Scraper

**name:** job-scraper
**description:** Scrapes Indian job sites for new positions matching your profile. Deduplicates across runs. Triggers on: job scrape, find jobs, search jobs, new jobs, job search, scrape jobs, /scrape
**allowed-tools:** Read, Write, Edit, Glob, Grep, WebFetch, WebSearch, Agent, AskUserQuestion

---

## How It Works

This skill's **default** is **remote-global** roles open to India. It fetches remote-first job
boards that expose open APIs/RSS (RemoteOK, Remotive, We Work Remotely, Himalayas, HN "Who is
Hiring") — these return full job data with no anti-bot blocking, so matches can be auto-read
end-to-end. It deduplicates against previously seen jobs and the application tracker, applies the
critical **India-eligibility filter** (skip US-only/EU-only/region-locked roles), and presents
new matches with a quick fit assessment.

Indian portals (Naukri, LinkedIn, Wellfound, Instahyre) are a **secondary** net run on
`/scrape india` — discovery works via WebSearch, but their full JDs are fetch-blocked, so the
user pastes the JD for any role they want to deep-dive. See `search-queries.md` for full strategy.

## Invocation

The user triggers this skill by saying things like:
- "Find new jobs"
- "Scrape for jobs"
- "Any new positions?"
- "/scrape"

Optional arguments:
- A focus area, e.g. "/scrape data science" or "/scrape geophysics"
- "broad" to run all search categories, e.g. "/scrape broad"

---

## Execution Steps

### Step 0: Load State

1. Read `job_scraper/seen_jobs.json` (create if missing - start with `{"seen": {}}`)
2. Read `job_search_tracker.csv` to extract already-applied companies+roles
3. Read `search-queries.md` (this directory) for the search strategy

### Step 1: Search

Read `search-queries.md` for the full strategy. **Default = Section A (remote-global).** Run
Section B (Indian portals) only on `/scrape india`, or both on `/scrape broad`.

**Section A (default) — remote APIs via `WebFetch`:**
- `WebFetch` the endpoints in `search-queries.md` Section A (RemoteOK, Remotive, We Work Remotely RSS, Himalayas, HN Who-is-Hiring). They return full JSON/RSS — no blocking.
- In each fetch prompt, ask for roles matching the stack (JS/TS/React/Next/Node/Mongo/Redis), and have it report the candidate-location eligibility per role.
- Apply the **India-eligibility filter**: keep ✅ ELIGIBLE (Anywhere/Worldwide/India/Asia) and ⚠️ CHECK; drop ❌ SKIP (US-only/EU-only/region-locked).

**Section B (`/scrape india`) — Indian portals via `WebSearch`:**
- Use `WebSearch` with the site-specific queries (naukri.com, linkedin.com/jobs, wellfound.com, instahyre.com).
- Full JDs are fetch-blocked on these — present discovery results and note the user must paste the JD to deep-dive.

**Default: keep only postings from the last 7 days** (freshness drives conversion — sort newest-first and lead with the freshest). Widen only on request (`/scrape 14d`, `/scrape 30d`).

### Step 2: Fetch & Parse

For each promising result from Step 1:
- Use `WebFetch` to retrieve the job posting page
- Extract: **job title**, **company**, **location**, **posting date** (or "recent"), **URL**, **key requirements** (brief), **application deadline** (if listed)
- Skip if the URL or company+title combo already exists in `seen_jobs.json`
- Skip if the company+role already appears in `job_search_tracker.csv`

### Step 3: Quick Fit Assessment

For each new job, do a rapid fit check (NOT the full evaluation from `04-job-evaluation.md` - just a quick signal):

- **High match**: Role directly involves your core skills
- **Medium match**: Role is adjacent to your experience
- **Low match**: Role requires significant skills you lack

### Step 4: Deduplicate & Store

1. Add ALL fetched jobs (new and skipped) to `seen_jobs.json` with structure:
```json
{
  "seen": {
    "<url_or_company_title_key>": {
      "title": "...",
      "company": "...",
      "url": "...",
      "first_seen": "YYYY-MM-DD",
      "fit": "high/medium/low",
      "status": "new/skipped/evaluated"
    }
  }
}
```
2. Only present jobs NOT already in the seen list or tracker.

### Step 5: Present Results

Present new jobs in a table sorted by fit (high first):

```
## New Job Matches - YYYY-MM-DD

Found X new positions (Y high, Z medium, W low match).

| # | Fit | Title | Company | Location | Deadline | URL |
|---|-----|-------|---------|----------|----------|-----|
| 1 | High | ... | ... | ... | ... | [Link](...) |

### High-Match Highlights
For each high-match job, add 2-3 bullet points:
- Why it matches your profile
- Key requirements to check
- Any red flags
```

After presenting, ask:
> "Want me to evaluate any of these in detail? Just give me the number(s)."

If the user picks a number, invoke the **job-application-assistant** skill workflow (fit evaluation first, then CV + cover letter if approved).

### Step 6: Update Tracker (Optional)

If the user decides to apply to any job, add a row to `job_search_tracker.csv`.

---

## Important Rules

1. **Never fabricate job postings.** Only present jobs found via actual WebSearch/WebFetch results.
2. **Respect deduplication.** Always check seen_jobs.json AND job_search_tracker.csv before presenting.
3. **Focus on configured geographic area.** Skip jobs that require relocation or are clearly outside commute range.
4. **Only open positions.** Skip postings with expired deadlines or those marked as closed.
5. **Be efficient with WebFetch.** Don't fetch every search result - use titles and snippets to pre-filter before fetching.
6. **Parallel searches.** Use the Agent tool or parallel WebSearch calls to speed up the search phase.
