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
- **Hallucinate or infer content not found in sources** — if data is unavailable, leave the section header with `⚠️ CONFIRM MANUALLY — data not found in sources.` Never fabricate metrics, status updates, or progress claims
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

### Section: TL;DR
**What to include:**
- Immediately after Q1 Goal — this is the 5-second read for leadership
- One status indicator: 🟢 On Track / 🟡 Needs Attention / 🔴 Off Track
- One sentence explaining why — tie to the biggest signal (roadmap progress, a key blocker, or a pending ask)
- Derive from the aggregate state of the Roadmap table and Risks/Gaps/Asks: if any roadmap item is 🔴 or there's an unresolved ask blocking progress, status should reflect that

**Format:** Status emoji + one sentence

**Example:**
```
🟢 On Track — All roadmap items progressing; one ask pending from IT (Salesforce write access) but not blocking current sprint.
```
```
🟡 Needs Attention — Governed Execution Plane blocked on auth token exchange; ask to Eng submitted, awaiting response.
```

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

#### Subsection: From the Field (Aha! Ideas)
**Source:** [Support Aha! Ideas Portal](https://databrickinternal.ideas.aha.io/ideas?category=7603850531562979200)

**What to include:**
- A small table connecting Support IC requests to outcomes — show the feedback loop is real
- Structure each row as: what Support asked for → what CXI shipped or decided
- For items not prioritized, include the reason and note it will be revisited in the next quarterly prioritization cycle
- **Spotlight contributors:** Call out teams or individuals whose input changed the design

**Format:** Table + contributor callout

**Note:** Aha! data cannot be scraped automatically. When generating the exec summary, always include this subsection header and table structure, populated with: `⚠️ TODO: Review Aha! ideas portal and fill in before sending.` This signals the need for manual input before distribution.

**Example:**
```
Ideas around Innovation from Support

| Idea | Submitted By | Outcome |
|------|-------------|---------|
| Auto-collect DBSQL query plans on case creation | @jane-doe (FL DBSQL) | ✅ Shipped in Merlin v2 — now triggers on DBSQL case attach |
| Slack integration for case escalation alerts | @platform-team | 🔜 Prioritized for next sprint |
| Custom diagnostic templates per product area | @john-smith (BL) | ⏸️ Not now — scope too broad for Q1; revisit in Q2 prioritization |

Spotlight: @jane-doe (FL DBSQL) flagged the query plan gap that shaped
Merlin's auto-collection logic. @platform-team's input on auth flow
changed how we scoped the Salesforce integration.
```

---

### Section: Risks / Gaps / Asks
**What to include:**
- Frame as "no material blockers" or "key dependencies" — not alarmist
- List specific team/system dependencies with names
- Note compliance or architectural constraints matter-of-factly
- Each risk should have a clear owner or next step
- Surface explicit **asks** — things CXI needs from cross-functional partners (Support, Eng, IT) to unblock or accelerate work. Frame as actionable requests with a who, what, and when

**Limit:** 0-3 items

**Example:**
```
There are no material blockers at this stage. Key dependencies:
- IT / BSE for Salesforce write integration
- SDR for Salesforce auth token exchange

Asks:
- Ask (IT): Prioritize Salesforce write access by April 1 for Phase 2 rollout
- Ask (Eng): Allocate review bandwidth for MCP integration PR by end of sprint
```

---

### Section: Impact Signal
**What to include:**
- Explicit targets with baselines (e.g., "5% improvement in TTM, baseline is 5.1 days")
- Acknowledge when it's too early to measure — that's fine, but state the goal
- Include operational metrics Hatim cares about (assignment %, reassignment %, SLA adherence)

**Format:** Bullet points with numbers and baselines

> **Note:** Keep this section's content guidance minimal until the "Key Metrics to Track" section (above) is updated with the metrics CXI is actively tracking. Once that section is populated, expand this guidance to reference those specific metrics, usability/eval data (e.g., AI SAT scores, eval pass rates), and metric movement trends.

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

### Section: Roadmap
**What to include:**
- A table with one row per roadmap objective from the Quarterly Pre-Read
- **Status** and **Progress** columns must be updated each cycle based on JIRA epic state (use `roadmap_to_epic_mapping` in config.yaml to connect objectives to epics)
- This keeps expectation management visible — stakeholders can see what's moving, what's blocked, and what was deprioritized
- Makes prioritization criteria explicit: if something was cut or deferred, say why

**Columns:** Roadmap Objective | Status | Progress

**Status values:**
- 🟢 On Track — progressing as planned
- 🟡 At Risk — may slip without intervention
- 🔴 Blocked — cannot proceed
- ⏸️ Deferred — deprioritized this quarter (include reason)

**How to derive Status and Progress:**
- Pull JIRA tickets grouped by epic (via `roadmap_to_epic_mapping`)
- Status = worst-case across tickets in the epic (any blocker → 🔴, any at-risk → 🟡, else 🟢)
- Progress = summary of what moved this sprint for that objective (1 sentence)
- If an objective has no JIRA activity, flag it — either it's deferred or the mapping needs updating

**Example:**
```
| Roadmap Objective | Status | Progress |
|-------------------|--------|----------|
| Automatic Diagnostic Collection (DBSQL) | 🟢 On Track | Merlin v2 shipped; auto-collection live for DBSQL workspaces |
| Governed Execution Plane | 🟡 At Risk | MCP integration PR in review; blocked on auth token exchange |
| Isaac Investigation Surface | 🟢 On Track | Support Agent workflow measurable end-to-end |
| Support Tooling Backend Service | ⏸️ Deferred | Deprioritized to focus on DBSQL — revisit Q2 |
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
