# {TEAM_NAME} | Biweekly Executive Summary | {DATE}

<!-- 👉 PLACEHOLDERS TO REPLACE:
  {TEAM_NAME} - Your team name (e.g., "CXI")
  {DATE} - Current date (e.g., "March 19, 2026")
  {GO_LINK} - Your team's go link (e.g., "go/cxi")
  {FAQ_LINK} - FAQ link (e.g., "go/cxi")
  {TEAM_DESCRIPTION} - One-sentence description of what your team does
  {Q1_GOAL} - One sentence: the quarterly goal this work ladders to
  {WHAT_SHIPPED} - Narrative paragraph on what moved this sprint
  {WHAT_THIS_UNLOCKS} - Bullet list of impact framing
  {IMPACT_SIGNAL} - Metrics with baselines and targets, usability/eval data
  {RISKS_GAPS_ASKS} - Dependencies, constraints, and cross-functional requests
  {HIGHLIGHTS} - Demos, deliverables, recordings/links
  {WHATS_NEXT} - Concrete next-sprint items with dates
  {SLACK_CHANNEL} - Your team's Slack channel for questions
-->

📪 **Feedback or Questions?** Please [click here](mailto:team@company.com)
**Self-Link:** {GO_LINK}
**FAQs:** {FAQ_LINK}

ℹ️ {TEAM_DESCRIPTION}

---

## 🎯 Q1 Goal

{Q1_GOAL}

<!-- Keep this stable sprint-to-sprint — this is the anchor for the whole summary -->

---

## TL;DR

{TLDR_STATUS}

<!-- One status indicator + one sentence.
     🟢 On Track / 🟡 Needs Attention / 🔴 Off Track
     Derive from Roadmap table + Risks/Gaps/Asks state. -->

---

## What Shipped

{WHAT_SHIPPED}

**What this unlocks:**
{WHAT_THIS_UNLOCKS}

<!-- Narrative paragraph on what moved this sprint, tied to the Q1 goal.
     Follow with bullet list of what it enables — impact framing, not feature listing. -->

### Ideas around Innovation from Support

<!-- Source: https://databrickinternal.ideas.aha.io/ideas?category=7603850531562979200 -->

| Idea | Submitted By | Outcome |
|------|-------------|---------|
| {IDEA_1} | {IDEA_1_SUBMITTED_BY} | {IDEA_1_OUTCOME} |
| {IDEA_2} | {IDEA_2_SUBMITTED_BY} | {IDEA_2_OUTCOME} |
| {IDEA_3} | {IDEA_3_SUBMITTED_BY} | {IDEA_3_OUTCOME} |

<!-- Outcome format:
     ✅ Shipped — brief description
     🔜 Prioritized for next sprint
     ⏸️ Not now — reason; revisit in next quarterly prioritization cycle
-->

**Spotlight contributors:** {SPOTLIGHT_CONTRIBUTORS}

<!-- Call out teams/individuals whose input changed the design.
     If no Aha! data is available, keep this subsection header and note:
     "⚠️ TODO: Review Aha! ideas portal and fill in before sending." -->

---

## 📊 Impact Signal

{IMPACT_SIGNAL}

<!-- Metrics with baselines and targets (e.g., "5% improvement in TTM, baseline is 5.1 days").
     Include usability/eval data when available (AI SAT scores, eval pass rates).
     Acknowledge when it's too early to measure — state the goal instead. -->

---

## ⚠ Risks / Gaps / Asks

{RISKS_GAPS_ASKS}

<!-- Frame as "no material blockers" or "key dependencies" — not alarmist.
     List specific team/system dependencies with names.
     Surface explicit asks from Support/Eng/IT with who, what, and when.
     Each item should have a clear owner or next step.
     Limit: 0-3 items.

     Example:
     No material blockers. Key dependencies:
     - IT / BSE for Salesforce write integration

     Asks:
     - Ask (IT): Prioritize Salesforce write access by April 1 for Phase 2 rollout
-->

---

## ⭐ Highlights

{HIGHLIGHTS}

<!-- Upcoming demos with dates, deliverable names in plain language,
     links to recordings/docs/dashboards. Short paragraphs with bold deliverable names. -->

---

## 📅 What's Next

{WHATS_NEXT}

<!-- Concrete items planned for next sprint, tied to roadmap objectives.
     Include dates or milestones where available.
     If no data is available, keep this section header and note:
     "⚠️ TODO: Fill in before sending." -->

---

## 🗺️ Roadmap

| Roadmap Objective | Status | Progress |
|-------------------|--------|----------|
| {ROADMAP_1_OBJECTIVE} | {ROADMAP_1_STATUS} | {ROADMAP_1_PROGRESS} |
| {ROADMAP_2_OBJECTIVE} | {ROADMAP_2_STATUS} | {ROADMAP_2_PROGRESS} |
| {ROADMAP_3_OBJECTIVE} | {ROADMAP_3_STATUS} | {ROADMAP_3_PROGRESS} |
| {ROADMAP_4_OBJECTIVE} | {ROADMAP_4_STATUS} | {ROADMAP_4_PROGRESS} |

<!-- Derive from Quarterly Pre-Read + JIRA epic state (via roadmap_to_epic_mapping in config.yaml).
     Status: 🟢 On Track | 🟡 At Risk | 🔴 Blocked | ⏸️ Deferred (include reason)
     Progress: 1 sentence on what moved this sprint for that objective.
     If an objective has no JIRA activity, flag it. -->

---

**Questions?** Reach out in [{SLACK_CHANNEL}](https://company.slack.com/archives/CHANNEL_ID) or reply to this thread.

---

## Validation Checklist

Before sending, verify:
- [ ] All `{PLACEHOLDERS}` replaced with actual data
- [ ] No "TBD" or empty values
- [ ] Q1 Goal matches current quarterly objective
- [ ] What Shipped is tied to Q1 Goal, not a generic feature list
- [ ] Each risk/ask has owner + next step
- [ ] Impact Signal includes baselines where available
- [ ] What's Next has concrete items (not vague goals)
- [ ] Links work (go links, dashboards, Slack channels)
- [ ] Reviewed by primary stakeholder
