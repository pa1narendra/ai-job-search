# Interview Preparation Guide

<!-- SETUP: STAR examples are personalized by running /setup based on your actual experience -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

<!-- Drafted by /setup from Pavan's real experience. Refine wording in your own voice before interviews. -->

### 1. Real-time messaging performance (Scaling & optimization)
**S:** At IVECTORS, the healthcare platform's internal messaging system was slow (2-3s to fetch messages) and only handled around 5,000 messages, which would not scale as clinics grew.
**T:** I was responsible for building a real-time messaging system from scratch that was both fast and able to scale to high volume.
**A:** I implemented Redis caching for hot data and added pagination so the client only loaded what it needed; I designed indexed MongoDB schemas tuned for high-volume access patterns and profiled queries to remove bottlenecks.
**R:** Fetch times dropped from 2-3s to under 500ms, capacity scaled from 5,000 to 1M+ messages, and overall performance improved ~40%.
**Use for:** "Tell me about a performance problem you solved", "Describe a system you built from scratch", "How do you handle scale?"

### 2. Multi-tenant architecture (System design & ownership)
**S:** The patient-management application needed to serve multiple clinics (5 clinics, 200+ users) with strict data separation and different feature needs per organization.
**T:** I needed to design and build a multi-tenant architecture with proper data isolation and access control.
**A:** I implemented isolated databases per organization, tenant-specific feature configurations, and role-based access control across roles (doctors, clinicians, billers, front desk), exposed through Node.js REST APIs.
**R:** The platform safely served 5 clinics and 200+ users across multiple roles with tenant data isolation and per-tenant configurability.
**Use for:** "Describe a system you designed", "How do you handle data isolation/security?", "Tell me about a complex backend project"

### 3. Keycloak SSO integration (Learning new tech / integration)
**S:** At Flying Fox Labs, multiple client applications each handled authentication separately, creating friction and manual role management.
**T:** I was tasked with enabling single sign-on across these applications.
**A:** I integrated Keycloak SSO using the OAuth 2.0 authorization-code flow and set up automated role assignments across the client apps.
**R:** Users gained single sign-on across applications and role assignment became automated, removing manual setup overhead.
**Use for:** "Tell me about a time you learned a new technology fast", "Describe an integration you owned", "Auth/security experience"

### 4. Multiplayer real-time chess (Initiative / resilience)
**S:** I wanted to deepen my real-time systems skills, so I built a multiplayer chess platform as a personal project.
**T:** Build a working real-time multiplayer game with reliable state, even when players disconnect.
**A:** I used WebSockets for instant move synchronization, enforced rules with server-side move validation, persisted game state in MongoDB, managed active sessions in Redis, and added reconnection logic that recovers game state from the database.
**R:** A working multiplayer chess platform where concurrent players see instant moves and games survive disconnections.
**Use for:** "Tell me about a side project", "Show initiative/self-learning", "Real-time / WebSocket experience"

<!-- Add more STAR examples as your experience grows. Aim for 4-6 covering different competencies. -->

## Common Tough Questions

### "Why are you looking to leave / switch?"
> I've been working at startups, where I've learned a lot by owning real-time and multi-tenant systems end-to-end. But I've repeatedly hit the same wall: an app that's the fastest thing on the internet at 100 users starts slowing around 500, and under a 20,000-user load test it crawls until we apply a round of optimizations we'd been missing. We get it healthy again, but it's reactive. I want to work somewhere that operates products at 1M+ users so I can learn how systems are designed and run at that scale from the start, rather than firefighting it later. *(This is your real motivation — keep it; it's honest and forward-looking with no negativity.)*

### "You don't have experience with [specific skill, e.g. Kubernetes / large-scale distributed systems]."
> I acknowledge I haven't operated at that exact scale yet — that's actually a big part of why I want this role. But I've done the adjacent work the hard way: I scaled a messaging system from 5K to 1M+ messages and cut latency from 2-3s to under 500ms with Redis and indexed MongoDB, and I've run load tests that exposed bottlenecks at 20K users and fixed them. I pick up new tooling fast, as I did with Keycloak/OAuth and Helm. *(Bridge to the closest real experience for the specific gap.)*

### "Where do you see yourself in 5 years?"
> Growing into a senior engineer who designs performance-critical systems for large-scale products from the ground up — and mentoring others as I go. *(Align with the specific role's growth path.)*

### "What's your biggest weakness?"
> So far I've worked mostly at small-to-mid scale, so large distributed-systems design is something I'm still building depth in. I've been deliberate about it — I dig into how high-scale systems are built, and I push to load-test and optimize proactively rather than waiting for things to break — but operating at 1M+ users is exactly the experience I'm seeking next. *(Genuine, with mitigation, and ties back to your motivation.)*

### "What's your notice period?"
> 15 days.

### "Why this company specifically?"
> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

## Questions You Should Ask Interviewers

### About the Role
- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"

### About the Team
- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "How do you onboard new team members?"

### About Tech & Growth
- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"

### About Culture (use these to prevent disappointment)
- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips
- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette
- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes
- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines
When the user asks for interview practice:
1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
