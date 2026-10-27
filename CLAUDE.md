# Job Application Assistant for [YOUR_NAME]

<!-- SETUP: This file is populated by running /setup -->
<!-- After running /setup, all [PLACEHOLDER] tokens will be replaced with your actual information -->

## Role
This repo is a job application workspace. Claude acts as a career advisor and application assistant for [YOUR_NAME], helping with:
1. **Job fit evaluation** - Assess job postings against your profile (skills, experience, behavioral traits)
2. **CV tailoring** - Adapt existing CV templates (LaTeX/moderncv) to target specific roles
3. **Cover letter writing** - Draft targeted cover letters using existing templates (LaTeX)
4. **Interview preparation** - Prepare answers, questions, and talking points for interviews
5. **Career strategy** - Advise on positioning and personal branding

## Candidate Profile

<!-- This section is auto-populated by /setup. You can also fill it in manually. -->

### Identity
- **Name:** Pavan Narendra Peela
- **Location:** Hyderabad, India (open to Hyderabad on-site/hybrid; also open to other Indian metros and remote — *assumed, confirm*)
- **Languages:** English (primary — used for work, interviews, and applications). Also comfortable in Telugu and Hindi if a role specifically requires them.
- **Status:** Employed — Software Engineer at IVECTORS; open to new opportunities. Notice period: 15 days.
- **LinkedIn headline:** "Software Engineer (React • Next.js • Node.js)"
- **Phone:** +91-9381974822
- **Email:** pavannarendra2002@gmail.com
- **LinkedIn:** https://www.linkedin.com/in/pavan-narendra/
- **GitHub:** https://github.com/pa1narendra/

### Education
- **B.Tech in Computer Science and Engineering** (2020-2024) - KKR & KSR Institute of Technology and Sciences
  - CGPA: 7.57

### Professional Experience
- **Software Engineer** (Jan 2025 - Present) - **IVECTORS** (Hyderabad, India)
  - Built a real-time internal messaging system from scratch for a healthcare platform; Redis caching + pagination cut fetch times from 2-3s to under 500ms and scaled capacity from 5,000 to 1M+ messages (40% overall performance improvement)
  - Developed Node.js REST APIs for a multi-tenant patient management app serving 5 clinics and 200+ users across roles (doctors, clinicians, billers, front desk); implemented isolated databases per org, tenant-specific feature configs, and RBAC
  - Built React/Next.js/TypeScript frontend components; wrote Jest unit tests and Playwright e2e tests; containerized services with Docker/Docker Compose; designed indexed MongoDB schemas for high-volume access
- **Software Engineer** (Jul 2024 - Jan 2025) - **Flying Fox Labs** (Hyderabad, India)
  - Integrated Keycloak SSO with OAuth 2.0 authorization-code flow enabling single sign-on and automated role assignment across client apps
  - Deployed/managed Helm charts (n8n, Bedrock, WordPress); set up CI/CD pipelines (build, lint, deploy) across dev/staging/prod; improved shared error handling and logging with Pino

### Technical Skills
- **Primary:** JavaScript, TypeScript, React, Next.js, Node.js, REST APIs, WebSockets
- **Secondary:** MongoDB, Redis, Java, C++, Tailwind CSS
- **Domain:** Full-stack web development, multi-tenant SaaS, real-time systems, healthcare platforms
- **Software:** AWS (EC2, S3, Elastic Beanstalk), Docker, Helm, CI/CD, Keycloak, Jest, Playwright, Pino, Git

### Projects
- **Multiplayer Real-time Chess (2024)** - Next.js, WebSockets, MongoDB, Redis. Real-time move sync between concurrent players, server-side move validation, persistent game state, and reconnection/recovery logic.

### Certifications
- *None listed on CV — add if you have any.*

### Publications
- *None.*

### Awards
- *None listed on CV — add if you have any (hackathons, competitions).*

### Behavioral Profile
<!-- 16Personalities (MBTI-style self-report): ENTJ-A "Commander". Full detail in 02-behavioral-profile.md. -->
- **Type:** ENTJ-A "Commander" — 77% Extraverted, 70% Intuitive, 61% Thinking, 85% Judging, 74% Assertive
- **Builder / ownership-driven** - Repeatedly builds systems "from scratch" and owns them end-to-end (messaging system, multi-tenant architecture)
- **Results- and performance-oriented** - Frames work in measurable impact (sub-500ms latency, 1M+ scale, 40% improvement)
- **Quality-minded** - Writes unit + e2e tests, reviews PRs, improves shared error handling/logging standards
- **Curious about scale** - Has hit real scaling walls at startups (apps fast at 100 users, slow at 500, "a snail" at 20K under load test) and wants to learn how systems are engineered for 1M+ users
- **Strengths:** Full-stack delivery, performance optimization, systems thinking, raising team code quality
- **Growth areas:** Large-scale system design and the operational practices behind high-scale apps — the main thing he wants to learn next
- **Thrives in:** Product teams with real ownership and room to build, ideally where he can learn high-scale engineering

### What Excites You
- Learning how big tech / large companies design and operate products at massive scale (1M+ users)
- Performance and scalability engineering — diagnosing and fixing the bottlenecks that startups hit as they grow
- Building real-time, performance-critical systems end-to-end across the full stack with modern JS/TS tooling

### Career Motivation (use in cover letters & "why switch" answers)
Pavan has worked at small startups where scaling was a recurring struggle: apps that are the fastest on the internet at ~100 users start slowing at ~500, and crawl under a 20K-user load test until heavy optimization is applied. He wants to move into an environment (big tech / large product companies) where he can learn how applications are architected and operated reliably at 1M+ users — turning hard-won, reactive optimization experience into proactive, large-scale system design skill.

### Target Sectors
- **Big tech / large product companies** (primary motivation: learn engineering at scale)
- Mid-size product companies and tech-forward enterprises with real scale challenges
- Product startups & SaaS (current background; consider for strong scale/ownership roles)

### Deal-breakers
- **Salary:** target range 9-15 LPA; treat below ~9 LPA as a floor to flag
- **No 24x7 on-call / production-support-centric roles**
- **No primarily non-JS legacy stacks** (.NET-only, PHP-only, legacy-Java-only with no React/Node)

## Repo Structure
- `cv/` - LaTeX CV variants (moderncv template, banking style)
- `cover_letters/` - LaTeX cover letters (custom cover.cls template)
- `.claude/skills/` - AI skill definitions for the application workflow
- `.agents/skills/` - Danish job-portal CLI tools, RETAINED AS REFERENCE ONLY (inactive). This workspace targets the **Indian job market**.

## Job Market
**Primary focus: REMOTE-GLOBAL roles open to India** (good pay, English, hire worldwide).
`/scrape` defaults to remote-first boards with open APIs/RSS — **RemoteOK, Remotive, We Work
Remotely, Himalayas, HN "Who is Hiring"** — fetched directly (full JDs, no anti-bot blocking).
The critical filter is **India eligibility**: keep "Anywhere/Worldwide/India/Asia" roles, skip
US-only/EU-only/region-locked ones.

**Secondary: Indian portals** (Naukri, LinkedIn, Wellfound, Instahyre) via `/scrape india` —
discovery works through `WebSearch`, but their full JDs are fetch-blocked, so the user pastes the
JD to deep-dive a role.

**Vetting-marketplace track** (apply once, get matched into US/EU-remote contracts): Lemon.io,
Arc.dev, Turing, Braintrust, Gun.io. Ready-to-use profile in `marketplace_profile.md`.

Search strategy and endpoints live in `.claude/skills/job-scraper/search-queries.md`. The Danish
CLIs in `.agents/skills/` are inactive reference only.

## Workflow for New Job Applications
1. User provides a job posting (URL or text)
2. **Always evaluate fit first**: skills match, experience match, behavioral/culture match. Present this assessment to the user before proceeding.
3. If good fit: create targeted CV (`cv/main_<company>.tex`) and cover letter (`cover_letters/cover_<company>_<role>.tex`)
4. **Verify both documents** (see Verification Checklist below)
5. Prepare interview talking points based on the role requirements and your strengths

**Important:** When mentioning agentic coding or AI tooling in CVs/cover letters, explicitly reference **Claude Code** by name.

## Verification Checklist
After creating or updating a CV or cover letter, re-read the generated file and verify **all** of the following before presenting to the user. Report the results as a pass/fail checklist.

### Factual accuracy
- [ ] All claims match actual profile (CLAUDE.md / candidate profile) - no fabricated skills, experience, or achievements
- [ ] Job titles, dates, company names, and locations are correct
- [ ] Contact details are correct
- [ ] All company-specific claims (partnerships, products, technology, expansions) have been independently verified via WebFetch/WebSearch - do not trust reviewer agent research without verification

### Targeting
- [ ] Profile statement / opening paragraph is tailored to the specific role (not generic)
- [ ] Skills and experience bullets are reframed to match the job requirements
- [ ] Key job requirements are addressed (with gaps acknowledged where relevant)
- [ ] Nice-to-have requirements are highlighted where there is a match

### Consistency
- [ ] CV follows the standard 2-page moderncv/banking format
- [ ] Cover letter uses cover.cls template and established structure
- [ ] Tone is consistent across CV and cover letter
- [ ] No contradictions between CV and cover letter content

### Quality
- [ ] No LaTeX syntax errors (balanced braces, correct commands)
- [ ] No spelling or grammar errors
- [ ] Agentic coding / AI tooling references mention **Claude Code** by name
- [ ] Cover letter is addressed to the correct person (or "Dear Hiring Manager" if unknown)
- [ ] Cover letter fits approximately one page

### Compiled PDF verification (MANDATORY - never skip)
Both documents MUST be compiled and visually inspected via the Read tool on the PDF output. "Looks fine in the .tex" is not acceptable - LaTeX page-break decisions are unpredictable. Iterate until these all pass:
- [ ] CV compiled with **lualatex** (pdflatex often fails on modern MiKTeX with fontawesome5 font-expansion errors). Cover letter compiled with **xelatex** (cover.cls requires fontspec).
- [ ] **CV is exactly 2 pages** - not 1, not 3
- [ ] **No orphaned `\cventry` titles** - a job/education title must never sit at the bottom of a page with its bullets spilling to the next page. Use `\needspace{5\baselineskip}` before each `\cventry` to prevent this, and `\enlargethispage{2-3\baselineskip}` to rescue a trailing section that just barely spills
- [ ] **Cover letter is exactly 1 page** - signature block must fit with the body, never overflow
- [ ] **Cover letter bullet font matches body font** - `\lettercontent{}` must not wrap `\begin{itemize}...\end{itemize}` (the command's trailing `\\` errors on `\end{itemize}`, and moving itemize outside loses the Raleway font). Standard pattern: close `\lettercontent{}`, then wrap the list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`
