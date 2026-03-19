# CXI Team - Domain Context

<!-- 👉 CUSTOMIZE THIS ENTIRE FILE FOR YOUR TEAM -->

## Team Overview
**CXI** = **C**ustomer E**x**perience **I**ntelligence Team

<!-- 👉 REPLACE with your team's acronym and full name -->

**Mission:** Turn Support from a function that scales with case volume into a system that gets smarter with every case - eliminating whole categories of issues while up-leveling support engineers to do work that compounds.

<!-- 👉 REPLACE with your team's mission statement -->

**Team Size:** 5 engineers, 3 product specialists, 1 TPM

<!-- 👉 UPDATE with your actual team composition -->

**Stakeholders:**
<!-- 👉 UPDATE with your key stakeholders and their emails -->
- Chief Operating Officer: hatim@databricks.com
- SVP Engineering: vinod.marur@databricks.com
- VP Support: sam.shah@databricks.com

---

## Key Metrics to Track

<!-- 👉 CUSTOMIZE these sections based on what YOUR stakeholders care about -->

### Velocity Metrics
<!-- 👉 ADD/REMOVE metrics based on your team's KPIs -->
- **Sprint points completed** - Target: 30-35 per 2-week sprint
- **Features shipped** - Major releases vs. incremental updates
- **Bugs closed** - High/Medium/Low priority breakdown

### Quality Metrics
<!-- 👉 UPDATE with your quality standards -->
- **Security audit findings** - Track critical/high/medium/low
- **API uptime** - SLA: 99.9%
- **P0 incidents** - Target: 0 per quarter

### Customer Metrics
<!-- 👉 ADD customer-facing metrics if applicable -->
- **New customers onboarded** - Enterprise tier
- **Support tickets** - Categorize by type (bug, feature request, question)
- **NPS score** - Track quarterly

---

## Writing Style Guide

<!-- 👉 CUSTOMIZE based on your organization's communication style -->

### ✅ DO
- Lead with impact: "Reduced latency by 50%" not "Optimized database queries"
- Quantify: "12 bugs closed" not "Fixed several bugs"
- Use exec-friendly language: "Revenue-impacting blocker" not "Redis cache invalidation issue"
- Highlight wins: Start with accomplishments, blockers come second
- Be specific: "Launched feature X for 3 enterprise customers" not "Made progress on feature"

### ❌ DON'T
- Use jargon without context: "Refactored the ORM layer" → "Improved database performance"
- Bury the lede: Get to the point in the first sentence
- Overload with details: Execs want summary, not implementation details
- Write novels: Each section should be scannable in 30 seconds

---

## Common Acronyms

<!-- 👉 ADD your team/domain-specific acronyms -->

- **CXI** - Customer Experience Intelligence (our team!)
- **AI SAT** - AI Generated Customer Satisfaction Score
- **MCP** - Model Context Protocol
- **CLF** - Central Logfood
- **NBA** - Next Best Action
- **DBSQL** - Databricks SQL Product
- **Evals** - Evaluations
- **TTM** - Time to Mitigation
- **TTR** - Time to Resolution
- **FL** - Frontline Engineering
- **BL** - Backline Engineering
- **IM** - Incident Management
- **IM** - Escalation Management
- **NOC** - Network Operating Center
- **TSE** - Technical Solutions Engineer
- **SSO** - Single Sign-On
- **MFA** - Multi-Factor Authentication
- **P0/P1/P2** - Priority levels (0 = critical, 1 = high, 2 = medium)

---

## Executive Summary Writing Style Guidance

<!-- Derived from stakeholder email patterns (Hatim, Vinod, Sam) and Kevin's existing exec summary format -->

### Stakeholder Communication Patterns

**Sam Shah (VP Support) — PRIMARY AUDIENCE.** The exec summary should be written for Sam first. His communication patterns will be refined over time as we learn what he responds to and asks about. Until then, optimize for clarity, conciseness, and operational relevance to Support leadership.

**Hatim (COO):** Action-oriented. Immediately asks for demos/recordings — wants to see the work. Responds with measurable targets ("let's set some targets on assignment & reassignment %"). Expects tight feedback loops and iteration. Asks probing questions about process and quality bar. Frame updates so they answer: "What can I see?" and "What are we measuring?"

**Vinod (SVP Eng):** Brief, supportive. Notices team effort and cross-functional collaboration. Values concise acknowledgment of people and outcomes.

### Overall Tone
- Open with the **quarterly goal** — one clear, measurable sentence that anchors everything
- Use **narrative paragraphs** for the main update, not just bullet lists — tell the story of what moved
- Frame impact as **"What this unlocks"** — not what was built, but what it enables
- Frame risks as **dependencies** and gaps, not failures — "Key dependencies: IT/BSE for Salesforce write integration"
- Always include **metrics with baselines and targets** — "5% improvement in DBSQL TTM, baseline is 5.1 days"
- Include **demo/recording links** when available — Hatim will ask for them if you don't

### Section: Q1 Goal (opening)
**What to include:**
- One sentence: the quarterly goal this work ladders to
- Keep it stable sprint-to-sprint — this is the anchor

**Example:**
- ✅ "Make DBSQL support executable: deliver the first usable, measurable agent-assisted investigation workflow for DBSQL that improves TSE productivity, reduces customer back-and-forth, and gives Support leadership better operational visibility."

---

### Section: Progress Narrative
**What to include:**
- 1-2 paragraphs on what moved this sprint, tied to the Q1 goal
- Specific deliverables (name the tools, workflows, integrations)
- "What this unlocks" bullet list — impact framing

**Format:** Narrative paragraph + bullet list

**Example:**
```
Sprint 1 delivered the first usable version of agent-assisted DBSQL investigation.
Three core pieces are now live in initial form: Merlin-based DBSQL diagnostic
auto-collection, an Isaac-based Support Agent workflow, and an evaluation setup
for Sherpa case-intelligence outputs.

What this unlocks:
- Less manual diagnostic collection with better completeness and correctness
- A more repeatable Isaac-based debuggability workflow that we can measure and improve
- An initial way to assess which Sherpa outputs are useful enough to scale
```

---

### Section: Risks / Gaps
**What to include:**
- Frame as "no material blockers" or "key dependencies" — not alarmist
- List specific team/system dependencies with names
- Note compliance or architectural constraints matter-of-factly
- Each risk should have a clear owner or next step

**Limit:** 0-3 items

**Example:**
```
There are no material blockers at this stage. Key dependencies:
- IT / BSE for Salesforce write integration
- SDR for Salesforce auth token exchange
```

---

### Section: Metrics
**What to include:**
- Explicit targets with baselines (e.g., "5% improvement in TTM, baseline is 5.1 days")
- Acknowledge when it's too early to measure — that's fine, but state the goal
- Include operational metrics Hatim cares about (assignment %, reassignment %, SLA adherence)

**Format:** Bullet points with numbers and baselines

---

### Section: Highlights
**What to include:**
- Upcoming demos with dates (Hatim will want to attend or see recordings)
- Specific deliverable names and what they do in plain language
- Links to recordings, docs, or dashboards when available

**Format:** Short paragraphs with bold deliverable names

**Example:**
```
March 16 demo with TSEs: Demo Support Agent and a TSE-facing UI for human
evaluation of NBA, case summarization, similar cases and AI-SAT.

Merlin DBSQL Auto-Collection: The first version of DBSQL diagnostic collection
is now live from minimal customer input.
```

---

## Team-Specific Customizations

<!-- 👉 ADD any unique aspects of your workflow -->

### Meeting Patterns
<!-- Example: Your team has specific meeting types to track -->
- **Standups:** Daily, keyword "CXI Stand up"
- **Sprint Planning:** Every 2 weeks, keyword "CXI Sprint Planning"
- **Retros:** End of sprint, keyword "CXI Sprint Review"

### JIRA Workflow
<!-- Example: Your team uses specific JIRA statuses -->
- **To Do:** Not started
- **In Progress:** Actively being worked on
- **In Review:** Code review or testing
- **Done:** Shipped to production

### Slack Conventions
<!-- Example: Your team uses specific emoji reactions -->
- 🚀 = Launched to production
- 🎯 = Important decision made
- 🚧 = Blocker identified

---

## Template Customization Examples

<!-- 👉 OPTIONAL: Add examples of how to customize templates for different audiences -->

### For Executive Audience
- Focus on business impact and customer value
- Minimize technical jargon
- Lead with numbers and outcomes

### For Engineering Leadership
- Include technical details in "deep dive" section
- Show velocity trends and sprint health
- Highlight technical debt or architecture decisions

### For Cross-Functional Teams
- Balance technical and business language
- Highlight dependencies and collaboration points
- Include "How to Help" section if needed
