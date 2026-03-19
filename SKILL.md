---
name: cxi-exec-summary
# 👉 CUSTOMIZE: Update the description to match YOUR team's workflow
# Be specific and "pushy" so Claude triggers this skill automatically
description: >
  IMMEDIATELY activate when user says "build CXI exec summary", "create CXI biweekly update",
  "generate exec summary for CXI", or mentions CXI executive updates. Automatically
  aggregate context from Google Docs, JIRA tickets, meetings, and Slack without asking for
  confirmation. This is a recurring workflow—be proactive.
# 👉 CUSTOMIZE: Add trigger phrases your team uses
triggers:
  - CXI Executive Summary
  - CXI exec summary
  - CXI biweekly update
version: 1.0.0
author: Kevin Baron-Quijano <kevin.baron@databricks.com>
---

# CXI Executive Summary Builder

## What This Skill Does
Automatically generates executive-ready newsletter summaries by aggregating updates from:
- Team Notes (from Goole Suite via MCP)
- 🎫 JIRA tickets (via MCP JIRA connection)
- 📅 Meeting notes (from Google Calendar via MCP)
- 💬 Slack discussions (via MCP Slack connection)

**Output:** Formatted Google Doc or email draft ready for review.

---

## When to Use
- User requests CXI Executive Summary
- Time for recurring newsletter (check `config.yaml` for schedule)
- Ad-hoc executive summary needed

---

## Workflow

### Phase 0: Quarterly Pre-Read
**Goal:** Establish strategic context before gathering updates

0. **Quarterly Roadmap**
   - Use: `mcp__google__google_read_api_call` with endpoint `docs/documents/1llPhMHPMy0OVqK7E-qZjEEXNwKDo5Ipf52kJqwq9q7U`
   - Read the Roadmap section of the CXI Quarterly Pre-Read
   - Extract: Current quarter goals, key milestones, strategic priorities, and OKRs
   - Use this as the lens for interpreting and prioritizing all subsequent data (JIRA, Slack, meetings)
   - Frame exec summary highlights in terms of roadmap progress

---

### Phase 1: Context Aggregation
**Goal:** Gather raw updates from all sources

1. **Meeting Notes**
   - Use: `mcp__google__calendar_event_list` tool
   - Query: Events from last 14 days matching configured keywords
   - Extract: Action items, decisions, key discussions

   ```
   # 👉 CUSTOMIZE in config.yaml:
   # - calendar_id: Your team's calendar
   # - keywords: Your meeting name patterns
   ```

2. **JIRA Tickets**
   - Use: `mcp__jira__jira_read_api_call` with endpoint `issues.search`
   - Query: `project = PLAT AND component = 'Support Platform' AND (status IN ("To Do","In Progress","In Review") OR updated >= -14d)`
   - Board: [Support Platform (board 6475)](https://databricks.atlassian.net/jira/software/c/projects/PLAT/boards/6475)
   - Prioritize: High-priority items, blockers

   ```
   # 👉 CUSTOMIZE in config.yaml:
   # - project_key: Your JIRA project (e.g., PLATFORM, DATA)
   # - custom_jql: Your team's specific query
   ```

3. **Slack Updates**
   - Use: `mcp__slack__slack_read_api_call` with endpoint `search.messages`
   - Strategy: Keyword-based search ("CXI", "support automation", "Isaac") across all channels, supplemented by `conversations.history` on configured channels
   - Channels: `#support-automation`, `#support-agent-internal`, `#eng-support-automation`, `#allhands-support`
   - Filter: Prioritize message content and relevance over reactions. Emoji reactions are a supplementary signal only — do not use them as a primary filter for inclusion

   ```
   # 👉 CUSTOMIZE in config.yaml:
   # - channels: Your team's Slack channels
   # - reaction_filter: Emojis that indicate important updates
   ```

**Output:** Aggregated data structured by source

---

### Phase 2: Content Structuring
**Goal:** Transform raw data into narrative format

1. **Apply Template**
   - Use: `assets/templates/biweekly-template.md`
   - Sections: Q1 Goal, Progress Narrative, What this unlocks, Risks/Gaps, Metrics, Highlights
   - See `references/domain-context.md` for writing style guidance per section

   ```
   # 👉 CUSTOMIZE templates in assets/templates/:
   # - Add/remove sections based on your team's needs
   # - Update metrics to track what matters to your stakeholders
   ```

2. **Follow Best Practices**
   - See: `references/domain-context.md#writing-style`
   - Exec-friendly: Focus on impact, not implementation details
   - Quantify results where possible

3. **Format for Medium**
   - **Google Doc (RECOMMENDED):** Use template-based approach
     1. Copy pre-formatted template: `mcp__google__drive_file_copy`
     2. Replace content: `mcp__google__docs_document_batch_update` with `replaceAllText` requests
     3. IMPORTANT: Use plain text only - NO HTML tags (they render as literal text)
   - **Email:** Use `mcp__google__gmail_message_send`

   ```
   # 👉 CUSTOMIZE in config.yaml:
   # - output.format: Choose google_doc, email, or markdown
   # - output.google_drive.template_id: Your formatted template doc ID
   # - google_drive_folder_id: Where to save newsletters
   ```

**Output:** Structured draft with all sections populated

---

### Phase 3: Review & Delivery
**Goal:** Finalize and distribute

1. **Generate Draft Using Template**
   - Copy template: `mcp__google__drive_file_copy` with `template_id` from config.yaml
   - Update title: Use `replaceAllText` to set date/week
   - Replace content sections: Use multiple `replaceAllText` requests (NO HTML tags!)
   - All formatting (purple headers, colored tables, etc.) is preserved from template

   ```
   # 👉 CUSTOMIZE in config.yaml:
   # - output.google_drive.template_id: Your formatted template Google Doc ID
   # - google_drive_folder_id: Your team's newsletter folder
   ```

   **CRITICAL:** Never use HTML tags like `<b>`, `<table>`, etc. in `replaceAllText`
   - They render as literal text, not formatting
   - Template already has all formatting - just replace text content

2. **Tag Reviewers**
   - Add reviewers using `mcp__google__drive_comment_create` or sharing permissions
   - Primary: kevin.baron@databricks.com (from `config.yaml`)
   - Secondary: samira.emmerson@databricks.com

   ```
   # 👉 CUSTOMIZE in config.yaml:
   # - reviewers.primary: Your primary reviewer's email
   # - reviewers.secondary: Your secondary reviewer's email
   ```

3. **Send Notification**
   - Post to Slack using `mcp__slack__slack_write_api_call` with endpoint `chat.postMessage`
   - Channel: From `config.yaml` (e.g., `#support-automation`)
   - Format: "📰 CXI Executive Summary draft ready for review: {LINK}"

   ```
   # 👉 CUSTOMIZE in config.yaml:
   # - slack_notification_channel: Where to post completion notice
   ```

**Output:** Published draft URL + confirmation

---

## Success Criteria

### Example Input
```
User: "Build the CXI exec summary"
```

### Expected Output
1. ✅ Google Doc created with title "CXI Executive Summary - [date range]"
2. ✅ Contains:
   - Q1 Goal — one sentence anchoring the quarterly objective
   - Progress Narrative — what moved this sprint, tied to the Q1 goal
   - What this unlocks — impact framing (bullet list)
   - Risks / Gaps — dependencies and constraints, not alarmist
   - Metrics — explicit targets with baselines
   - Highlights — demos, deliverables, recordings/links
3. ✅ Reviewers tagged and notified
4. ✅ Link shared in Slack

### Sample Generated Content
```markdown
# CXI Executive Summary - March 19, 2026

## 🎯 Key Highlights
- Shipped support automation pipeline v2 (30% faster resolution)
- Completed sprint review with zero critical bugs
- Onboarded 3 new internal teams to Isaac

## 📊 This Sprint's Metrics
- Features shipped: 4
- Bugs closed: 12
- Sprint velocity: 34 points (↑ 15% vs. last sprint)

## 🚧 Blockers & Risks
- Dependency on platform team for API changes (Owner: @kevin, ETA: next sprint)

## 📅 Next Sprint
- Isaac agent rollout to tier-2 support
- Q1 metrics review with leadership
```

---

## Configuration

### Required MCP Connections
Ensure these MCP servers are configured in your Claude Code settings:

```bash
# Google MCP (for Calendar, Docs, Gmail)
# See: https://github.com/anthropics/mcp-servers/google

# JIRA MCP
# See: Your organization's JIRA MCP documentation

# Slack MCP
# See: Your organization's Slack MCP documentation
```

### Skill Configuration
**👉 EDIT `config.yaml` with your team's details:**

```yaml
team: CXI
schedule: biweekly

reviewers:
  primary: kevin.baron@databricks.com
  secondary: samira.emmerson@databricks.com

data_sources:
  meetings:
    calendar_id: "kevin.baron@databricks.com"
    keywords:
      - "CXI Stand up"
      - "CXI Sprint Planning"
      - "CXI Sprint Review"
      - CXI
  jira:
    project_key: PLAT
    custom_jql: "project = PLAT AND component = 'Support Platform' AND (status = 'In Progress' OR updated >= -14d) ORDER BY priority DESC"
  slack:
    channels:
      - support-automation
      - support-agent-internal
      - eng-support-automation
      - allhands-support

output:
  format: google_doc
  google_drive_folder_id: "15N7jxMSBzLpqVb92TxxZbTneCQUm9-tD"
  slack_notification_channel: "#support-automation"
```

---

## Troubleshooting

### Common Issues
- **"No meeting notes found"** → Check `calendar_id` in `config.yaml`
- **"JIRA query returned 0 tickets"** → Verify `project_key` matches your JIRA project
- **"Slack scraper failed"** → Ensure MCP Slack connection is authenticated

See `references/mcp-integration.md#troubleshooting` for detailed solutions.

---

## Extending This Skill

### Add New Data Source
1. Identify the MCP tool (e.g., `mcp__confluence__search_confluence_pages`)
2. Add configuration to `config.yaml`
3. Update Phase 1 in this file with the new tool call
4. Modify template to include new section

### Change Output Format
1. Duplicate template: `assets/templates/custom-template.md`
2. Update Phase 2 to reference new template
3. Update `config.yaml` to point to new template
4. Test with: "Build CXI exec summary using custom template"

---

## Quick Start Customization Checklist

Before using this skill, update:

- [x] YAML frontmatter: `name`, `description`, `triggers`, `author`
- [x] `config.yaml`: All team-specific values (see 👉 markers)
- [ ] `assets/templates/`: Customize sections and metrics
- [ ] `references/domain-context.md`: Add your team's context
- [ ] Test: Say "Build CXI exec summary" and verify it triggers

---

## References
- 📚 Team context & style guide: `references/domain-context.md`
- 🔌 MCP tool usage guide: `references/mcp-integration.md`
- 📝 More examples: `references/examples/`
