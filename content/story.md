# ai-job-search — Story

> One-line pitch: I forked an open-source AI job-search agent that was built for Denmark and re-pointed it at remote roles that hire from India — after Naukri, LinkedIn, and Indeed all fought back.
> Scope: single · Mode: build-in-public (dominant) + case-study + hiring · Platforms: X, LinkedIn, blog, Instagram · Goals: validation, users, gigs
> Repo (public): https://github.com/pa1narendra/ai-job-search · Upstream: github.com/MadsLorentzen/ai-job-search
> Handles: X @pa1narendra · LinkedIn /in/pavan-narendra · GitHub /pa1narendra

## Honest claim boundary (resolved)
- **What's mine:** the India / remote-global retarget — swapping the search side from Danish portals to remote-hiring boards that hire from anywhere, filtering for roles not locked to a specific region, and adding a **most-recent-posts filter** to dodge stale, over-applied listings.
- **What's upstream (credit MadsLorentzen):** the application *engine* — fit evaluation, CV/cover-letter tailoring, the drafter→reviewer loop, the PDF-verification step. Reference these as the framework's features, not "I built."
- **Framing:** "a simple, useful customization of an existing project." Post under my own name — fine with signaling a job switch.

## What it is
A Claude Code agent that runs a job search end-to-end (evaluate fit → tailor a LaTeX CV + cover letter → review → compile/verify the PDF). I adapted the **search** half to work for someone job-hunting from India.

## The real journey (this is the story)
1. **Forked it to use it.** Found it was built for the **Danish** market (Jobindex, Jobnet, Akademikernes Jobbank). I'm in India and don't speak Danish.
2. **Tried the obvious Indian sites.** Re-pointed scraping at **Naukri, LinkedIn, Indeed**:
   - LinkedIn **blocked** scraping.
   - Naukri **blocked** it too.
   - Indeed returned **stale listings — 2–3 years old**, some no longer real.
3. **The pivot.** While browsing LinkedIn for jobs, I noticed a bunch of **remote-hiring portals**. Quick Google to check they allow scraping → they do. So I re-pointed the agent at remote boards and tuned the filter to keep roles open to **anywhere in the world** (not region-locked to US/EU). **It worked — real results.**
4. **The finishing touch.** Results weren't recent, so I added a **most-recent-posts filter** — apply early, before a listing has hundreds of applicants.

## Why I'm sharing it
Built it purely for my own hunt. Seeing others on LinkedIn/X struggling with the same India-remote problem, I made the repo public — happy to help anyone job-hunting from India adapt it.

## What makes the contribution worth a post
It's small but genuinely useful, and the *process* is relatable: the Indian-portal route is a dead end (anti-bot + stale data), and remote-global boards + a recency filter are a working alternative. That's a real, repeatable lesson for any India-based job seeker.

## Story Hooks inventory
| # | Hook | Payoff | Best platforms | Verified? |
|---|------|--------|----------------|-----------|
| 1 | "I forked an AI job-search agent. Turns out it was built for Denmark. I'm in India." | the retarget journey | X, LinkedIn, IG, blog | yes |
| 2 | "LinkedIn blocked it. Naukri blocked it. Indeed gave me posts from 2022." | why Indian-portal scraping fails | X, LinkedIn, blog | yes |
| 3 | "So I pointed it at remote boards that hire from anywhere — and it worked." | the working alternative | all | yes |
| 4 | "Then I filtered for only the freshest posts, to apply before the crowd." | the recency-filter edge | X, blog | yes |

## Asset needed
- `[ASSET: screenshot of /scrape returning recent remote-global roles open to India]` — the proof shot. A small before/after (stale Indeed result vs. fresh remote-global result) would be even stronger.
