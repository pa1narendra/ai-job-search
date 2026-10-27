---
title: "I made a Danish AI job search agent work from India"
slug: ai-job-search-india-remote-global
description: "I cloned an open source AI job search agent, found out it was built for Denmark, and after the Indian sites blocked scraping, I pointed it at remote sites that hire from anywhere."
date: [NEEDS INPUT: publish date]
canonical: [NEEDS INPUT: your blog URL — or omit if posting only on dev.to/Hashnode]
cover: [ASSET: screenshot of the remote-global results]
tags: [claude-code, ai-agents, job-search, india, web-scraping]
---

I came across this open source AI job search agent that runs on Claude Code, and I cloned it thinking it would help me land a job. It does the whole thing, it scores a job for fit, tailors a CV and cover letter, and even compiles and checks the PDF. But after going through the readme, I got to know it was actually built for the Danish market, sites like Jobindex and Jobnet. They said it would work the same for any country, but honestly I didn't think it would work for us.

## So I thought why not change it for our market

I pointed the scraping at Naukri, LinkedIn and Indeed, the major Indian sites Claude suggested. Tried it, and got no results. Turns out these sites don't allow scraping.

Claude then suggested building a Playwright script to scrape them, but that would risk getting my LinkedIn account banned, and I didn't want to risk my account for this, so I dropped that idea.

## The alternate that actually worked

So I searched for another way, and found that some remote sites allow scraping. I went with those, with a filter that the role should be open to work from anywhere in the world, not the ones that say remote but are actually only for US/EU. First it gave some older posts that weren't even related, so I added one more filter for the most recent ones. And it worked, I got some posts that are somewhat related 🙂

## What is mine and what is not

Just to be clear, the application engine, the fit scoring, the CV and cover letter tailoring, the draft and review step, and the PDF checks, all of that is MadsLorentzen's open source framework. My part is just the search side for India, the remote sites, the work-from-anywhere filter, and the recency filter.

## If you are job hunting remote from India

The big Indian portals are mostly a dead end, between the scraping blocks and the old data. The remote sites that hire from anywhere, filtered for recent posts, worked better for me, and the agent does the boring parts while you focus on the actual applications.

## Links
- Repo: https://github.com/pa1narendra/ai-job-search
- Forked from: github.com/MadsLorentzen/ai-job-search
- Built on: [Claude Code](https://claude.com/claude-code)

---
*I'm Pavan, a full-stack engineer (React/Next.js/Node) from India. I made this public so it can help others hunting remote from here, try it out and let me know how it feels.*
