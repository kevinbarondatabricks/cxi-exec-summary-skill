# {TEAM_NAME} | Biweekly Executive Summary | {DATE}

<!-- TODO: This template's sections need to be updated to match the domain-context.md structure:
  Q1 Goal → Progress Narrative → What this unlocks → Risks/Gaps → Metrics → Highlights
  See references/domain-context.md#executive-summary-writing-style-guidance for details.
-->

<!-- 👉 PLACEHOLDERS TO REPLACE:
  {TEAM_NAME} - Your team name (e.g., "ABAC + Permission Model")
  {DATE} - Current date (e.g., "March 7, 2026")
  {GO_LINK} - Your team's go link (e.g., "go/abac-update")
  {FAQ_LINK} - FAQ link (e.g., "go/abac-faqs")
  {TEAM_DESCRIPTION} - One-sentence description of what your team does
  {HIGHLIGHTS} - 3-5 bullet points of key accomplishments
  {METRICS} - Your team's KPIs (e.g., velocity, uptime, customers)
  {BLOCKERS} - Current blockers (or "No blockers this sprint")
  {NEXT_WEEK} - Upcoming milestones and focus areas
  {SLACK_CHANNEL} - Your team's Slack channel for questions
-->

📪 **Feedback or Questions?** Please [click here](mailto:team@company.com)
**Self-Link:** {GO_LINK}
**FAQs:** {FAQ_LINK}

ℹ️ {TEAM_DESCRIPTION}

---

## Upcoming Launches

<!-- 👉 CUSTOMIZE THIS TABLE with your launches/milestones -->

| Launch Stage | Status | Launch Date |
|-------------|--------|-------------|
| {LAUNCH_1_NAME} | {STATUS_1} | {LAUNCH_1_DATE} |
| {LAUNCH_2_NAME} | {STATUS_2} | {LAUNCH_2_DATE} |
| {LAUNCH_3_NAME} | {STATUS_3} | {LAUNCH_3_DATE} |

<!-- Status options: 🟢 On Track, 🟠 At Risk, 🔴 Blocked -->

---

## ⭐ Executive Summary

<!-- 👉 REPLACE with 3-5 key updates -->

{HIGHLIGHTS}

<!--
Example format:
### Feature X Launch
- Delivered on time with zero P0 bugs
- Onboarded 3 enterprise customers

### Performance Improvements
- Reduced latency by 40% (200ms → 120ms p95)
- Achieved 99.95% uptime this week
-->

---

## 📊 This Sprint's Metrics | [Dashboard Link]({DASHBOARD_LINK})

<!-- 👉 CUSTOMIZE with your KPIs -->

- **Sprint Points Completed:** {SPRINT_POINTS}
- **Features Shipped:** {FEATURES_SHIPPED}
- **Bugs Closed:** {BUGS_CLOSED}
- **System Uptime:** {UPTIME}%
- **Active Users:** {ACTIVE_USERS}
- **Support Tickets:** {SUPPORT_TICKETS}

<!-- 👉 ADD/REMOVE metrics based on what your stakeholders care about -->

---

## ⚠ Risks/Blockers

<!-- 👉 If NO blockers, replace table with: "No blockers this sprint ✅" -->

| Issue | Impacting Milestone | Mitigation/Next Steps | Owner | Notes |
|-------|--------------------|-----------------------|-------|-------|
| {BLOCKER_1_ISSUE} | {BLOCKER_1_MILESTONE} | {BLOCKER_1_MITIGATION} | {BLOCKER_1_OWNER} | {BLOCKER_1_NOTES} |
| {BLOCKER_2_ISSUE} | {BLOCKER_2_MILESTONE} | {BLOCKER_2_MITIGATION} | {BLOCKER_2_OWNER} | {BLOCKER_2_NOTES} |

<!-- Format: Each blocker MUST have owner and mitigation plan -->

---

## 📅 Next Sprint's Focus

<!-- 👉 REPLACE with upcoming milestones -->

{NEXT_WEEK}

<!--
Example format:
- Launch feature X (Monday)
- Sprint planning session (Wednesday)
- Customer demo with Acme Corp (Friday)
- Bug bash for upcoming release
-->

---

**Questions?** Reach out in [{SLACK_CHANNEL}](https://company.slack.com/archives/CHANNEL_ID) or reply to this thread.

---

## 📝 Template Usage Instructions

### Step 1: Copy this template
When generating a newsletter, copy this entire template as the starting point.

### Step 2: Replace ALL placeholders
Search for `{` and replace every `{PLACEHOLDER}` with actual data from:
- Google Calendar (for highlights and next week)
- JIRA (for metrics and launches)
- Slack (for team updates)

### Step 3: Remove unused sections
- If no launches, delete "Upcoming Launches" table
- If no blockers, replace table with "No blockers this sprint ✅"
- If certain metrics don't apply, remove those rows

### Step 4: Format for output
- **For Google Docs:** Use `mcp__google__docs_document_create_from_markdown`
- **For email:** Use `mcp__google__gmail_message_send` with body as HTML
- **For Slack:** Post summary with link to full doc

### Step 5: Add rich formatting (optional)
For the exact PDF-style formatting (purple table headers, colored status, etc.):
1. Create a template Google Doc with your desired formatting once
2. Save the template ID in `config.yaml`
3. Use `drive_file_copy` to duplicate the template
4. Use `docs_document_batch_update` with `find_replace` to update placeholders

See `references/mcp-integration.md#template-based-approach` for details.

---

## Color Coding Guide (for rich formatting)

**Status Indicators:**
- 🟢 **On Track** - Green (#00CC00) - Everything going as planned
- 🟠 **At Risk** - Orange (#FF9900) - May slip without intervention
- 🔴 **Blocked** - Red (#FF0000) - Critical blocker preventing progress

**Table Headers:**
- Background: Purple (#5B3A8F)
- Text: White (#FFFFFF)
- Font: Bold

**Section Icons:**
- ⭐ Executive Summary (Yellow)
- 📊 Metrics (Blue)
- ⚠ Risks/Blockers (Orange/Red)
- 📅 Next Week (Green)

---

## Validation Checklist

Before sending, verify:
- [ ] All `{PLACEHOLDERS}` replaced with actual data
- [ ] No "TBD" or empty values
- [ ] Each blocker has owner + mitigation
- [ ] Links work (go links, dashboards, Slack channels)
- [ ] Metrics are up-to-date (from this sprint, not last sprint)
- [ ] Next sprint section has concrete items (not vague goals)
- [ ] Reviewed by primary stakeholder
- [ ] Spell check passed
