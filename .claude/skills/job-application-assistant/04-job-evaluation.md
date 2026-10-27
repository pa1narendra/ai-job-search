# Job Evaluation Framework

<!-- SETUP: Skill match areas and career goals are personalized by running /setup -->

## Scoring Dimensions

Evaluate each job posting against these five dimensions:

### 1. Technical Skills Match (0-100)
How well do the required/preferred skills align with the candidate's capabilities?

| Score | Meaning |
|-------|---------|
| 80-100 | Core requirements are primary skills |
| 60-79 | Most requirements match, 1-2 gaps that are learnable |
| 40-59 | Partial match, significant upskilling needed |
| 0-39 | Fundamental mismatch |

**Strong match areas:** JavaScript, TypeScript, React, Next.js, Node.js, REST APIs, WebSockets, MongoDB, Redis, multi-tenant architecture
**Moderate match areas:** AWS (EC2/S3/Elastic Beanstalk), Docker, Helm, CI/CD, Keycloak/OAuth 2.0, Java, C++, Tailwind CSS
**Weak match areas:** Kubernetes-native ops, large-scale distributed systems, Python/Go backends, data engineering/ML, mobile, GCP/Azure

### 2. Experience Match (0-100)
Does work history align with what they're looking for?

| Score | Meaning |
|-------|---------|
| 80-100 | Direct experience in the same domain and role type |
| 60-79 | Related experience, transferable skills clear |
| 40-59 | Adjacent experience, would need to make the case |
| 0-39 | Unrelated experience |

**Strong:** Full-stack web development (React/Next/Node), multi-tenant SaaS, real-time systems, healthcare platforms, performance optimization at scale
**Moderate:** DevOps/infrastructure (Docker, Helm, CI/CD), SSO/auth integration (Keycloak, OAuth)
**Entry-level:** Tech lead / architecture ownership at large scale, ML/data engineering (2 years total experience — junior-to-mid level)

### 3. Behavioral/Culture Fit (0-100)
Does the role and company culture match the behavioral profile?

| Score | Meaning |
|-------|---------|
| 80-100 | Culture strongly matches behavioral preferences |
| 60-79 | Mixed signals but mostly compatible |
| 40-59 | Some friction areas |
| 0-39 | Significant culture mismatch |

**Red flags to research:** Department disorganization, work dominated by maintenance over development, poor chemistry with leadership, culture mismatches. Check reviews, media coverage, LinkedIn connections, and network contacts for insider perspective.

### 4. Location & Logistics (Pass/Fail + Notes)
- Hyderabad (on-site/hybrid): PASS
- Other major Indian metros (Bengaluru, Pune, Chennai, Delhi NCR, Mumbai): PASS (open to relocation for these)
- Remote (India): PASS
- Tier-2/3 city requiring relocation: FLAG (discuss with user)
- Frequent international travel: FLAG (discuss with user)

### 5. Career Alignment & Motivation (0-100)
Does this role advance career goals and contain tasks that energize?

| Score | Meaning |
|-------|---------|
| 80-100 | Strongly aligned with career direction, clear growth path |
| 60-79 | Good role but only partially aligned with long-term goals |
| 40-59 | Decent job but doesn't build toward career goals |
| 0-39 | Dead end or backwards step |

**Career goals:**
- Move into big tech / large product companies to learn how applications are architected and operated at massive scale (1M+ users)
- Deepen system design and scalability expertise — convert reactive, hard-won startup optimization experience into proactive large-scale design skill
- Grow into a senior full-stack / backend engineer owning performance-critical, real-time systems

**Strong career-alignment signal (score high):** Roles at companies that operate genuinely high-scale products, or that explicitly involve performance/scalability/distributed-systems work. This is Pavan's primary motivation for switching.

**Motivation filter:** Evaluate not just whether you *can* do the tasks, but whether the tasks will *energize* you. Consider:
- Tasks that energize: scaling/performance engineering, system design at scale, building new features end-to-end, real-time systems, modern JS/TS stacks
- Tasks that drain: pure maintenance of legacy systems, 24x7 on-call/production support, non-JS legacy stacks (.NET/PHP-only)
- Non-task factors: leadership style, department culture, company values, degree of autonomy

**Life situation alignment:** Consider personal constraints:
- **Security**: Currently employed (IVECTORS); can be selective — only switch for a clearly better role. Salary target 9-15 LPA; flag anything below ~9 LPA.
- **Flexibility**: Hyderabad-based; open to other major Indian metros and remote.
- **Professional development**: Prioritizes learning high-scale system design, scalability, and ownership of meaningful product work.

### 6. Salary Benchmark (Optional)

If the salary lookup tool is configured (`salary_data.json` exists), look up the company:
```
python salary_lookup.py "<Company Name>" --json
```

If a city is known from the posting, add `--city "<City>"` to narrow results.

Present findings as:
```
### Salary Benchmark
| Metric | Value |
|--------|-------|
| [Category] index | XX.X (+/-X.X% vs baseline) |
| Overall index | XX.X (+/-X.X% vs baseline) |
```

Interpret results relative to the baseline defined in the data file's metadata. For index-based data, higher typically means above-market compensation.

If the salary tool is not configured, skip this section.

## Output Format

Present the evaluation as:

```
## Job Fit Evaluation: [Role] at [Company]

| Dimension | Score | Notes |
|-----------|-------|-------|
| Technical Skills | XX/100 | [brief note] |
| Experience Match | XX/100 | [brief note] |
| Behavioral Fit | XX/100 | [brief note] |
| Location | PASS/FAIL | [brief note] |
| Career Alignment | XX/100 | [brief note] |

**Overall Score: XX/100** (weighted average of scored dimensions)

### Verdict: [Strong Fit / Good Fit / Moderate Fit / Weak Fit / Poor Fit]

### Key Strengths for This Role
- [bullet points]

### Gaps to Address
- [bullet points]

### Recommendation
[1-2 sentences: apply/skip/apply with caveats]

### Company Research Checklist
- [ ] Checked company website (mission, values, recent news)
- [ ] Checked review sites (AmbitionBox, Glassdoor, Naukri company reviews, etc.)
- [ ] Checked LinkedIn for team size, recent hires, connections
- [ ] Checked media for restructuring, growth, or workplace issues
- [ ] Identified network contacts who may know the team/manager
```

## Weighting
- Technical Skills: 30%
- Experience Match: 25%
- Behavioral Fit: 15%
- Career Alignment: 30%

(Location is pass/fail, not weighted)

## Thresholds
- **Strong Fit** (75+): Definitely apply, tailor everything
- **Good Fit** (60-74): Apply, address gaps in cover letter
- **Moderate Fit** (45-59): Consider carefully, discuss with user
- **Weak Fit** (30-44): Probably skip unless strategic reasons
- **Poor Fit** (<30): Skip

## Pre-Application: Call the Employer (Best Practice)

Before writing the application, consider whether the candidate should call the contact person listed in the posting. **Only call if there are substantive questions** - never call just to "be remembered."

### When to Suggest Calling
- The posting has unclear or ambiguous requirements
- It's unclear which competencies are essential vs. nice-to-have
- The role description is vague about day-to-day tasks
- There's a named contact person who invites questions

### Good Questions to Ask
- "What are the primary challenges in this role?"
- "How is time typically divided across the listed responsibilities?"
- "Which competencies are most critical for success in this position?"
- "What does success look like in the first 6-12 months?"

### Rules for the Call
- Prepare a 30-second "elevator pitch" about your background in case they ask
- The call's purpose is **gathering information**, not delivering a pitch
- Take notes - use what you learn to tailor the application
- Reference the conversation naturally in the cover letter ("After speaking with [name], I was especially drawn to...")
