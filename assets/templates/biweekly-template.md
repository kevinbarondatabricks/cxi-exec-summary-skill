# {TEAM_NAME} | Biweekly Executive Summary | {DATE}

<!-- PLACEHOLDERS TO REPLACE:
  {TEAM_NAME} - Your team name (e.g., "CXI")
  {DATE} - Current date (e.g., "March 19, 2026")
  {GO_LINK} - Your team's go link (e.g., "go/cxi")
  {FAQ_LINK} - FAQ link (e.g., "go/cxi")
  {TEAM_DESCRIPTION} - One-sentence description of what your team does
  {WHAT_SHIPPED} - Narrative paragraph on what moved this sprint
  {WHAT_THIS_UNLOCKS} - Bullet list of impact framing
  {IMPACT_SIGNAL} - Metrics with baselines and targets, usability/eval data
  {RISKS_GAPS} - Dependencies and constraints
  {ASKS} - Cross-functional requests with who, what, and when
  {HIGHLIGHTS} - Demos, deliverables, recordings/links
  {WHATS_NEXT} - Concrete next-sprint items with dates
  {SLACK_CHANNEL} - Your team's Slack channel for questions

  FORMATTING RULES (for Google Doc output):
  - All section headers: Heading 2, Arial, 16px, Bold
  - No horizontal rules or dividers between sections
  - No emojis in headers or TL;DR status
  - Bold key points throughout (deliverable names, metrics, status labels)
  - No em dashes; use regular dashes (-) and semicolons (;)
-->

**Feedback or Questions?** Please [click here](mailto:team@company.com)
**Self-Link:** {GO_LINK}
**FAQs:** {FAQ_LINK}

{TEAM_DESCRIPTION}

## TL;DR

{TLDR_STATUS}

<!-- One status label + one sentence.
     **On Track** / **Needs Attention** / **Off Track**
     Derive from Roadmap table + Risks/Gaps/Asks state.
     No emojis - use plain text status labels in bold. -->

## What Shipped

{WHAT_SHIPPED}

**What this unlocks:**
{WHAT_THIS_UNLOCKS}

<!-- Narrative paragraph on what moved this sprint.
     Add blank lines between paragraphs for visual breathing room.
     Follow with bullet list of what it enables - impact framing, not feature listing.
     Bold key deliverable names and outcomes. -->

### Ideas around Innovation from Support

<!-- Source: https://databrickinternal.ideas.aha.io/ideas?category=7603850531562979200 -->

| Idea | Submitted By | Outcome |
|------|-------------|---------|
| {IDEA_1} | {IDEA_1_SUBMITTED_BY} | {IDEA_1_OUTCOME} |
| {IDEA_2} | {IDEA_2_SUBMITTED_BY} | {IDEA_2_OUTCOME} |
| {IDEA_3} | {IDEA_3_SUBMITTED_BY} | {IDEA_3_OUTCOME} |

<!-- Outcome format:
     Shipped - brief description
     Prioritized for next sprint
     Not now - reason; revisit in next quarterly prioritization cycle
-->

**Spotlight contributors:** {SPOTLIGHT_CONTRIBUTORS}

<!-- Call out teams/individuals whose input changed the design.
     If no Aha! data is available, keep this subsection header and note:
     "CONFIRM MANUALLY - data not found in sources." -->

## Impact Signal

{IMPACT_SIGNAL}

<!-- Metrics with baselines and targets (e.g., "5% improvement in TTM; baseline is 5.1 days").
     Include usability/eval data when available (AI SAT scores, eval pass rates).
     Acknowledge when it's too early to measure - state the goal instead.
     Bold metric names and values. -->

## Risks / Gaps

{RISKS_GAPS}

<!-- Frame as "no material blockers" or "key dependencies" - not alarmist.
     List specific team/system dependencies with names.
     Note compliance or architectural constraints matter-of-factly.
     Each risk should have a clear owner or next step.
     Limit: 0-3 items.

     Example:
     No material blockers. Key dependencies:
     - IT / BSE for Salesforce write integration
     - SDR for Salesforce auth token exchange
-->

## Asks

{ASKS}

<!-- Cross-functional requests - things CXI needs from partners (Support, Eng, IT)
     to unblock or accelerate work. Frame as actionable requests with who, what, and when.
     Limit: 0-3 items.

     Example:
     - **Ask (IT):** Prioritize Salesforce write access by April 1 for Phase 2 rollout
     - **Ask (Eng):** Allocate review bandwidth for MCP integration PR by end of sprint
-->

## Highlights

{HIGHLIGHTS}

<!-- Upcoming demos with dates, deliverable names in plain language,
     links to recordings/docs/dashboards. Short paragraphs with **bold deliverable names**.
     Add blank lines between each highlight paragraph for visual breathing room. -->

## What's Next

{WHATS_NEXT}

<!-- Concrete items planned for next sprint, tied to roadmap objectives.
     Include dates or milestones where available.
     If no data is available, keep this section header and note:
     "CONFIRM MANUALLY - fill in before sending." -->

## Roadmap

| Roadmap Objective | Status | Progress |
|-------------------|--------|----------|
| {ROADMAP_1_OBJECTIVE} | {ROADMAP_1_STATUS} | {ROADMAP_1_PROGRESS} |
| {ROADMAP_2_OBJECTIVE} | {ROADMAP_2_STATUS} | {ROADMAP_2_PROGRESS} |
| {ROADMAP_3_OBJECTIVE} | {ROADMAP_3_STATUS} | {ROADMAP_3_PROGRESS} |
| {ROADMAP_4_OBJECTIVE} | {ROADMAP_4_STATUS} | {ROADMAP_4_PROGRESS} |

<!-- Derive from Quarterly Pre-Read + JIRA epic state (via roadmap_to_epic_mapping in config.yaml).
     Status: **On Track** / **At Risk** / **Blocked** / **Deferred** (include reason)
     No emojis in status column - use bold plain text.
     Progress: 1 sentence on what moved this sprint for that objective.
     If an objective has no JIRA activity, flag it. -->

**Questions?** Reach out in [{SLACK_CHANNEL}](https://company.slack.com/archives/CHANNEL_ID) or reply to this thread.

## Validation Checklist

Before sending, verify:
- [ ] All `{PLACEHOLDERS}` replaced with actual data
- [ ] No "TBD" or empty values
- [ ] What Shipped is tied to quarterly goal, not a generic feature list
- [ ] Each risk/gap has owner + next step
- [ ] Each ask has who, what, and when
- [ ] Impact Signal includes baselines where available
- [ ] What's Next has concrete items (not vague goals)
- [ ] No emojis in TL;DR or section headers
- [ ] No em dashes anywhere; only regular dashes and semicolons
- [ ] Key points bolded throughout
- [ ] Links work (go links, dashboards, Slack channels)
- [ ] Reviewed by primary stakeholder
