# {TEAM_NAME} | Monthly Review | {MONTH} {YEAR}

<!-- 👉 PLACEHOLDERS TO REPLACE:
  {TEAM_NAME} - Your team name
  {MONTH} - Month name (e.g., "March")
  {YEAR} - Year (e.g., "2026")
  {GO_LINK} - Team go link
  {EXEC_SUMMARY} - 2-3 sentences summarizing the month
  {ACCOMPLISHMENTS} - Major wins with business impact
  {METRICS} - Monthly KPI summary with trends
  {CHALLENGES} - What didn't go well + learnings
  {NEXT_MONTH} - Focus areas for next month
-->

📪 **Feedback or Questions?** [Click here](mailto:team@company.com)
**Monthly Reviews:** {GO_LINK}
**Metrics Dashboard:** {DASHBOARD_LINK}

---

## 📈 Executive Summary

{EXEC_SUMMARY}

**Key Highlights:**
- {HIGHLIGHT_1}
- {HIGHLIGHT_2}
- {HIGHLIGHT_3}

---

## 🏆 {MONTH} Accomplishments

<!-- 👉 CUSTOMIZE with your major launches/wins -->

### Major Launches

| Feature | Launch Date | Status | Customer Impact |
|---------|-------------|--------|-----------------|
| {LAUNCH_1_NAME} | {LAUNCH_1_DATE} | {LAUNCH_1_STATUS} | {LAUNCH_1_IMPACT} |
| {LAUNCH_2_NAME} | {LAUNCH_2_DATE} | {LAUNCH_2_STATUS} | {LAUNCH_2_IMPACT} |

### Customer Wins
<!-- 👉 ADD specific customer successes -->
- **{CUSTOMER_1}:** {WIN_DESCRIPTION_1}
- **{CUSTOMER_2}:** {WIN_DESCRIPTION_2}

### Technical Achievements
<!-- 👉 ADD engineering milestones -->
- {TECH_ACHIEVEMENT_1}
- {TECH_ACHIEVEMENT_2}
- {TECH_ACHIEVEMENT_3}

---

## 📊 Monthly Metrics

### Delivery Metrics

| Metric | {MONTH} {YEAR} | {PREV_MONTH} {YEAR} | Change |
|--------|----------------|---------------------|--------|
| Sprint Points Completed | {CURRENT_POINTS} | {PREV_POINTS} | {CHANGE_POINTS} |
| Features Shipped | {CURRENT_FEATURES} | {PREV_FEATURES} | {CHANGE_FEATURES} |
| Bugs Closed | {CURRENT_BUGS} | {PREV_BUGS} | {CHANGE_BUGS} |
| Velocity (per sprint) | {CURRENT_VELOCITY} | {PREV_VELOCITY} | {CHANGE_VELOCITY} |

<!-- 👉 Use ↑ X% or ↓ X% for changes -->

### Quality Metrics

| Metric | {MONTH} {YEAR} | {PREV_MONTH} {YEAR} | Target |
|--------|----------------|---------------------|--------|
| P0 Incidents | {CURRENT_P0} | {PREV_P0} | 0 |
| API Uptime | {CURRENT_UPTIME}% | {PREV_UPTIME}% | 99.9% |
| Mean Time to Resolution | {CURRENT_MTTR} | {PREV_MTTR} | < 4 hours |

### Customer Metrics

| Metric | {MONTH} {YEAR} | {PREV_MONTH} {YEAR} | Change |
|--------|----------------|---------------------|--------|
| Daily Active Users | {CURRENT_DAU} | {PREV_DAU} | {CHANGE_DAU} |
| Weekly Active Customers | {CURRENT_WAC} | {PREV_WAC} | {CHANGE_WAC} |
| Support Tickets | {CURRENT_TICKETS} | {PREV_TICKETS} | {CHANGE_TICKETS} |
| NPS Score | {CURRENT_NPS} | {PREV_NPS} | {CHANGE_NPS} |

---

## 🚧 Challenges & Learnings

<!-- 👉 Be honest about what didn't go well -->

### Challenge 1: {CHALLENGE_1_TITLE}
**Issue:** {CHALLENGE_1_DESCRIPTION}

**Impact:** {CHALLENGE_1_IMPACT}

**Learning:** {CHALLENGE_1_LEARNING}

**Mitigation Applied:**
- {MITIGATION_1A}
- {MITIGATION_1B}

---

### Challenge 2: {CHALLENGE_2_TITLE}
**Issue:** {CHALLENGE_2_DESCRIPTION}

**Impact:** {CHALLENGE_2_IMPACT}

**Learning:** {CHALLENGE_2_LEARNING}

**Mitigation Applied:**
- {MITIGATION_2A}
- {MITIGATION_2B}

---

## 🎯 {NEXT_MONTH} Priorities

<!-- 👉 CUSTOMIZE with next month's goals -->

**Top 3 Goals:**
1. **{GOAL_1_TITLE}**
   - {GOAL_1_DESCRIPTION}
   - Target: {GOAL_1_DATE}

2. **{GOAL_2_TITLE}**
   - {GOAL_2_DESCRIPTION}
   - Target: {GOAL_2_DATE}

3. **{GOAL_3_TITLE}**
   - {GOAL_3_DESCRIPTION}
   - Target: {GOAL_3_DATE}

**Secondary Goals:**
- {SECONDARY_GOAL_1}
- {SECONDARY_GOAL_2}
- {SECONDARY_GOAL_3}

---

## 📅 {NEXT_MONTH} Milestones

| Milestone | Target Date | Owner | Dependencies |
|-----------|-------------|-------|--------------|
| {MILESTONE_1} | {DATE_1} | {OWNER_1} | {DEPS_1} |
| {MILESTONE_2} | {DATE_2} | {OWNER_2} | {DEPS_2} |
| {MILESTONE_3} | {DATE_3} | {OWNER_3} | {DEPS_3} |

---

## 👏 Team Highlights

<!-- 👉 RECOGNIZE individual/team achievements -->

- **{PERSON_1}** {ACHIEVEMENT_1}
- **{PERSON_2}** {ACHIEVEMENT_2}
- **Team:** {TEAM_ACHIEVEMENT}

---

## 📝 Appendix

### Detailed Timeline
<!-- 👉 OPTIONAL: Add key dates -->
- **{DATE_A}:** {EVENT_A}
- **{DATE_B}:** {EVENT_B}
- **{DATE_C}:** {EVENT_C}

### Customer Feedback Highlights
<!-- 👉 OPTIONAL: Add customer quotes -->
> "{QUOTE_1}" - {CUSTOMER_1}

> "{QUOTE_2}" - {CUSTOMER_2}

### Links & Resources
- [Metrics Dashboard]({DASHBOARD_LINK})
- [Customer Tracker]({TRACKER_LINK})
- [Roadmap]({ROADMAP_LINK})

---

**Questions or Feedback?** Reach out in [{SLACK_CHANNEL}](https://slack.com/channels/{CHANNEL_ID}) or email {TEAM_EMAIL}

---

## 📝 Template Usage Instructions

### When to Use Monthly Template

Use this template for:
- **Monthly reviews** sent to leadership
- **End of sprint summaries** (if sprints are monthly)
- **Board updates** or investor reports

### Data Collection for Monthly

Gather data from:
1. **JIRA:** Query all tickets updated in the month
   ```
   updated >= startOfMonth() AND updated <= endOfMonth()
   ```

2. **Google Calendar:** All team meetings in the month

3. **Metrics Dashboard:** Export monthly aggregates

4. **Slack:** Search for announcements and wins

5. **Customer Feedback:** NPS surveys, support tickets

### Customization Guide

**For Engineering Leadership:**
- Keep "Technical Achievements" detailed
- Add "Tech Debt Addressed" section
- Include architecture decision records (ADRs)

**For Executive Audience:**
- Lead with business impact (revenue, customers)
- Minimize technical jargon
- Focus on OKR progress
- Add financial metrics if relevant

**For Cross-Functional Teams:**
- Balance technical and business language
- Highlight cross-team collaborations
- Include "How We Can Help You" section

### Metrics Best Practices

**Always show trends:**
- ↑ X% (green) for positive changes
- ↓ X% (red) for negative changes
- → (neutral) for no change

**Compare to:**
- Previous month (short-term trend)
- Same month last year (seasonal comparison)
- Target/goal (progress tracking)

**Use charts/graphs:**
- Line charts for trends over time
- Bar charts for comparisons
- Pie charts for breakdowns

### Rich Formatting Tips

**For Google Docs output:**
1. Create template doc with:
   - Purple table headers (#5B3A8F)
   - Colored status indicators
   - Section dividers
   - Company logo/branding

2. Use `drive_file_copy` + `batch_update`

3. See `references/mcp-integration.md` for details

---

## Validation Checklist

Before publishing, verify:
- [ ] All placeholders replaced
- [ ] Metrics include month-over-month comparison
- [ ] Challenges section is honest (not just wins)
- [ ] Next month priorities are SMART goals
- [ ] Team highlights recognize specific contributions
- [ ] Links work and are accessible to audience
- [ ] Executive summary is ≤3 sentences
- [ ] Reviewed by primary stakeholder
- [ ] Charts/graphs embedded (if applicable)
