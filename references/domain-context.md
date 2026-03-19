# CXI Team - Domain Context

## Team Overview
**CXI** = **C**ustomer E**x**perience **I**ntelligence Team

**Mission:** Turn Support from a function that scales with case volume into a system that gets smarter with every case - eliminating whole categories of issues while up-leveling support engineers to do work that compounds.

**Team Size:** 5 engineers, 3 product specialists, 1 TPM

**Stakeholders:**
- Chief Operating Officer: hatim@databricks.com
- SVP Engineering: vinod.marur@databricks.com
- VP Support: sam.shah@databricks.com

## Key Metrics to Track

### Velocity Metrics
- **Sprint points completed** - Target: 30-35 per 2-week sprint
- **Features shipped** - Major releases vs. incremental updates
- **Bugs closed** - High/Medium/Low priority breakdown

### Quality Metrics
- **Security audit findings** - Track critical/high/medium/low
- **API uptime** - SLA: 99.9%
- **P0 incidents** - Target: 0 per quarter

### Customer Metrics
- **New customers onboarded** - Enterprise tier
- **Support tickets** - Categorize by type (bug, feature request, question)
- **NPS score** - Track quarterly

## Writing Style Guide

### DO
- Lead with impact: "Reduced latency by 50%" not "Optimized database queries"
- Quantify: "12 bugs closed" not "Fixed several bugs"
- Use exec-friendly language: "Revenue-impacting blocker" not "Redis cache invalidation issue"
- Highlight wins: Start with accomplishments, blockers come second
- Be specific: "Launched feature X for 3 enterprise customers" not "Made progress on feature"
- **Bold key points** throughout - deliverable names, metric values, status labels, team names
- Use regular dashes (-) and semicolons (;) for punctuation breaks; never em dashes

### DON'T
- **Hallucinate or infer content not found in sources** - if data is unavailable, leave the section header with `CONFIRM MANUALLY - data not found in sources.` Never fabricate metrics, status updates, or progress claims
- Use emojis anywhere in the output - no emojis in headers, status indicators, tables, or body text
- Use em dashes - always use regular dashes or semicolons instead
- Use jargon without context: "Refactored the ORM layer" - instead say "Improved database performance"
- Bury the lede: Get to the point in the first sentence
- Overload with details: Execs want summary, not implementation details
- Write novels: Each section should be scannable in 30 seconds

## Common Acronyms

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
- **EM** - Escalation Management
- **NOC** - Network Operating Center
- **TSE** - Technical Solutions Engineer
- **SSO** - Single Sign-On
- **MFA** - Multi-Factor Authentication
- **P0/P1/P2** - Priority levels (0 = critical, 1 = high, 2 = medium)

## Executive Summary Writing Style Guidance

### Output Formatting Rules (mandatory)

These rules override any conflicting guidance elsewhere:

1. **Headers:** All section headers must be Heading 2, Arial, 16px, Bold
2. **No dividers:** No horizontal rules or visual separators between sections
3. **No emojis:** Zero emojis in the entire document - not in headers, TL;DR, tables, or body
4. **Bold key points:** Deliverable names, metric values, status labels, and important outcomes in **bold**
5. **No em dashes:** Use regular dashes (-) or semicolons (;) instead
6. **TL;DR status:** **On Track** / **Needs Attention** / **Off Track** (bold plain text, no emojis)
7. **Roadmap status:** **On Track** / **At Risk** / **Blocked** / **Deferred** (bold plain text, no emojis)

### Stakeholder Communication Patterns

**Sam Shah (VP Support) - PRIMARY AUDIENCE for exec biweekly.** The exec biweekly should be written for Sam first. His communication patterns will be refined over time as we learn what he responds to and asks about. Until then, optimize for clarity, conciseness, and operational relevance to Support leadership.

**Hatim (COO):** Action-oriented. Immediately asks for demos/recordings - wants to see the work. Responds with measurable targets ("let's set some targets on assignment and reassignment %"). Expects tight feedback loops and iteration. Asks probing questions about process and quality bar. Frame updates so they answer: "What can I see?" and "What are we measuring?"

**Vinod (SVP Eng):** Brief, supportive. Notices team effort and cross-functional collaboration. Values concise acknowledgment of people and outcomes.

### Overall Tone
- Use **narrative paragraphs** for the main update, not just bullet lists - tell the story of what moved
- Frame impact as **"What this unlocks"** - not what was built, but what it enables
- Frame risks as **dependencies** and gaps, not failures - "Key dependencies: IT/BSE for Salesforce write integration"
- Always include **metrics with baselines and targets** - "5% improvement in DBSQL TTM; baseline is 5.1 days"
- Include **demo/recording links** when available - Hatim will ask for them if you don't

### Section: TL;DR
**What to include:**
- This is the 5-second read for leadership
- One status label: **On Track** / **Needs Attention** / **Off Track**
- One sentence explaining why - tie to the biggest signal (roadmap progress, a key blocker, or a pending ask)
- Derive from the aggregate state of the Roadmap table, Risks / Gaps, and Asks: if any roadmap item is **Blocked** or there is an unresolved ask blocking progress, status should reflect that

**Format:** Bold status label + one sentence

**Example:**
```
**On Track** - All roadmap items progressing; one ask pending from IT (Salesforce write access) but not blocking current sprint.
```
```
**Needs Attention** - Governed Execution Plane blocked on auth token exchange; ask to Eng submitted, awaiting response.
```

### Section: What Shipped (Progress Narrative)
**What to include:**
- 1-2 paragraphs on what moved this sprint, tied to the quarterly goal
- Specific deliverables (name the tools, workflows, integrations) in **bold**
- "What this unlocks" bullet list - impact framing
- **Add blank lines between paragraphs** for visual breathing room - each paragraph should be clearly separated

**Format:** Narrative paragraphs (spaced) + bullet list

**Example:**
```
Sprint 1 delivered the first usable version of agent-assisted DBSQL investigation.
Three core pieces are now live in initial form: **Merlin-based DBSQL diagnostic
auto-collection**, an **Isaac-based Support Agent workflow**, and an **evaluation setup
for Sherpa case-intelligence outputs**.

The integration enables TSEs to run diagnostic workflows directly from the agent
interface, closing the loop on the Q1 goal of making DBSQL support executable.

What this unlocks:
- Less manual diagnostic collection with better completeness and correctness
- A more repeatable Isaac-based debuggability workflow that we can measure and improve
- An initial way to assess which Sherpa outputs are useful enough to scale
```

#### Subsection: From the Field (Aha! Ideas)
**Source:** [Support Aha! Ideas Portal](https://databrickinternal.ideas.aha.io/ideas?category=7603850531562979200)

**What to include:**
- A small table connecting Support IC requests to outcomes - show the feedback loop is real
- Structure each row as: what Support asked for - what CXI shipped or decided
- For items not prioritized, include the reason and note it will be revisited in the next quarterly prioritization cycle
- **Spotlight contributors:** Call out teams or individuals whose input changed the design

**Format:** Table + contributor callout

**Note:** Aha! data cannot be scraped automatically. When generating the exec biweekly, always include this subsection header and table structure, populated with: `CONFIRM MANUALLY - review Aha! ideas portal and fill in before sending.` This signals the need for manual input before distribution.

**Example:**
```
Ideas around Innovation from Support

| Idea | Submitted By | Outcome |
|------|-------------|---------|
| Auto-collect DBSQL query plans on case creation | @jane-doe (FL DBSQL) | Shipped in Merlin v2 - now triggers on DBSQL case attach |
| Slack integration for case escalation alerts | @platform-team | Prioritized for next sprint |
| Custom diagnostic templates per product area | @john-smith (BL) | Not now - scope too broad for Q1; revisit in Q2 prioritization |

Spotlight: @jane-doe (FL DBSQL) flagged the query plan gap that shaped
Merlin's auto-collection logic. @platform-team's input on auth flow
changed how we scoped the Salesforce integration.
```

### Section: Risks / Gaps
**What to include:**
- Frame as "no material blockers" or "key dependencies" - not alarmist
- List specific team/system dependencies with names
- Note compliance or architectural constraints matter-of-factly
- Each risk should have a clear owner or next step

**Limit:** 0-3 items

**Example:**
```
No material blockers. Key dependencies:
- IT / BSE for Salesforce write integration
- SDR for Salesforce auth token exchange
```

### Section: Asks
**What to include:**
- This is a standalone section - separate from Risks / Gaps
- Cross-functional requests - things CXI needs from partners (Support, Eng, IT) to unblock or accelerate work
- Frame as actionable requests with **who**, **what**, and **when**
- Each ask should be a single bullet with the team/org in parentheses

**Limit:** 0-3 items

**Example:**
```
- **Ask (IT):** Prioritize Salesforce write access by April 1 for Phase 2 rollout
- **Ask (Eng):** Allocate review bandwidth for MCP integration PR by end of sprint
```

### Section: Impact Signal
**What to include:**
- Explicit targets with baselines (e.g., "5% improvement in TTM; baseline is 5.1 days")
- Acknowledge when it is too early to measure - that is fine, but state the goal
- Include operational metrics Hatim cares about (assignment %, reassignment %, SLA adherence)
- **Bold** metric names and values

**Format:** Bullet points with numbers and baselines

> **Note:** Keep this section's content guidance minimal until the "Key Metrics to Track" section (above) is updated with the metrics CXI is actively tracking. Once that section is populated, expand this guidance to reference those specific metrics, usability/eval data (e.g., AI SAT scores, eval pass rates), and metric movement trends.

### Section: Highlights
**What to include:**
- Upcoming demos with dates (Hatim will want to attend or see recordings)
- Specific deliverable names and what they do in plain language
- Links to recordings, docs, or dashboards when available
- **Add blank lines between each highlight** for visual breathing room - each highlight should be its own spaced paragraph

**Format:** Short paragraphs with **bold deliverable names**, spaced apart

**Example:**
```
**March 16 demo with TSEs** - Demo Support Agent and a TSE-facing UI for human
evaluation of NBA, case summarization, similar cases and AI-SAT.

**Merlin DBSQL Auto-Collection** - The first version of DBSQL diagnostic collection
is now live from minimal customer input.

**Isaac Investigation Dashboard** - Live dashboard tracking investigation quality
metrics across DBSQL cases.
```

### Section: Roadmap
**What to include:**
- A table with one row per roadmap objective from the Quarterly Pre-Read
- **Status** and **Progress** columns must be updated each cycle based on JIRA epic state (use `roadmap_to_epic_mapping` in config.yaml to connect objectives to epics)
- This keeps expectation management visible - stakeholders can see what is moving, what is blocked, and what was deprioritized
- Makes prioritization criteria explicit: if something was cut or deferred, say why

**Columns:** Roadmap Objective | Status | Progress

**Status values:**
- **On Track** - progressing as planned
- **At Risk** - may slip without intervention
- **Blocked** - cannot proceed
- **Deferred** - deprioritized this quarter (include reason)

**How to derive Status and Progress:**
- Pull JIRA tickets grouped by epic (via `roadmap_to_epic_mapping`)
- Status = worst-case across tickets in the epic (any blocker = **Blocked**, any at-risk = **At Risk**, else **On Track**)
- Progress = summary of what moved this sprint for that objective (1 sentence)
- If an objective has no JIRA activity, flag it - either it is deferred or the mapping needs updating

**Example:**
```
| Roadmap Objective | Status | Progress |
|-------------------|--------|----------|
| Automatic Diagnostic Collection (DBSQL) | **On Track** | Merlin v2 shipped; auto-collection live for DBSQL workspaces |
| Governed Execution Plane | **At Risk** | MCP integration PR in review; blocked on auth token exchange |
| Isaac Investigation Surface | **On Track** | Support Agent workflow measurable end-to-end |
| Support Tooling Backend Service | **Deferred** | Deprioritized to focus on DBSQL - revisit Q2 |
```

## Weekly Support Update Writing Style Guidance

### Audience
**Directors, TSE Managers, Shift Leads, Tech Leads, TSEs.** These are practitioners and their managers. They care about what changed in their day-to-day workflow and how to use it. They do not need roadmap strategy, leadership asks, or metric baselines.

### Core Principles
- **Right message for the right audience:** Support leadership receives concise outcomes, trends, and asks (exec biweekly). Rest of Support receives what changes in workflows and how to try it (weekly support).
- **Low lift for Support leadership:** The same core content is reused across comms for different audiences. Support leadership is not asked to build decks or ad-hoc reports.
- **Consistent narrative:** Support hears a consistent story about automation without Support leaders needing to orchestrate it.

### Overall Tone
- Write like you are explaining to a colleague, not presenting to leadership
- Be direct and practical - "here's what changed and how to use it"
- Assume no prior context - a TSE reading this for the first time should understand what to do
- Acknowledge limitations honestly - practitioners trust updates that don't oversell
- Keep it short - the whole update should be readable in 2 minutes

### Section: What's New
**What to include:**
- Only items with a practitioner-facing impact - skip internal architecture, refactors, or leadership strategy
- Lead each item with the **tool or workflow name** in bold
- One spaced paragraph per item
- Describe what's different for the reader, not what CXI built

**What to skip:**
- Roadmap strategy or reprioritization decisions
- Cross-functional asks (those belong in the exec biweekly)
- Metric baselines or targets (practitioners don't need these)
- Items still in development with no user-facing change yet

**Example:**
```
**Merlin DBSQL Auto-Collection is live.** When a DBSQL case is created, Merlin now
automatically collects workspace diagnostics (query plans, cluster config, error logs).
You no longer need to manually request these from the customer.
```

### Section: How to Try It
**What to include:**
- One numbered list per tool/feature, with the **tool name bolded** as a sub-heading
- 3-5 steps max - if it takes more, link to a detailed doc instead
- Include direct links wherever possible (dashboards, tools, docs)
- Write for someone who has never used this tool before

**Example:**
```
**Merlin Auto-Collection:**
1. Open any new DBSQL case in Salesforce
2. Check the "Diagnostics" tab - Merlin-collected data appears automatically within 5 minutes
3. If data is missing, click "Request Collection" to trigger manually
```

### Section: Known Limitations
**What to include:**
- What doesn't work yet, what to expect, workarounds
- Bold the tool name, then state the limitation plainly
- If there is a workaround, include it
- If no limitations to report, say so

**Example:**
```
**Merlin auto-collection** currently supports DBSQL workspaces only; other product areas
are planned for Q2.
```

### Section: Questions / Feedback
**What to include:**
- Keep this section stable week to week
- Always include: Slack channel, Aha! Ideas portal link, direct contact email
- This is the same every week unless channels change

### Data Filtering from Shared Sources
The weekly support profile uses the same Phase 0 + Phase 1 data as the exec biweekly. When structuring content for this profile:
- **Include:** Shipped features, new tool capabilities, workflow changes, bug fixes that affect TSE experience
- **Exclude:** Roadmap status changes, leadership asks, metric targets, internal refactors, compliance/architecture decisions
- **Reframe:** Where the exec biweekly says "Merlin v2 shipped; auto-collection live" (outcome), the weekly support says "Merlin now auto-collects diagnostics on DBSQL cases - here's how to use it" (action)

## Team-Specific Customizations

### Meeting Patterns
- **Standups:** Daily, keyword "CXI Stand up"
- **Sprint Planning:** Every 2 weeks, keyword "CXI Sprint Planning"
- **Retros:** End of sprint, keyword "CXI Sprint Review"

### JIRA Workflow
- **To Do:** Not started
- **In Progress:** Actively being worked on
- **In Review:** Code review or testing
- **Done:** Shipped to production

### Slack Conventions
- Prioritize message content and relevance over reactions
- Emoji reactions are a supplementary signal only

## Template Customization Examples

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
