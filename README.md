# ABAC Newsletter Skill

**Example skill for building automated team newsletters using Claude Code Skills.**

This skill demonstrates progressive disclosure structure and uses MCP (Model Context Protocol) connections to aggregate updates from meetings, JIRA tickets, and Slack, then generates a formatted newsletter.

---

## 📁 Directory Structure

```
abac-newsletter-skill/
├── SKILL.md                      # Main skill definition (< 5k tokens)
├── config.yaml                   # Team-specific configuration
├── README.md                     # This file
│
├── references/                   # Extended documentation (lazy-loaded)
│   ├── README.md                 # Index of reference docs
│   ├── domain-context.md         # Team background & style guide
│   ├── mcp-integration.md        # MCP tool usage examples
│   └── examples/
│       ├── simple-newsletter.md  # Basic weekly example
│       └── quarterly-review.md   # Extended quarterly example
│
├── assets/                       # Static resources
│   └── templates/
│       ├── weekly-template.md    # Weekly newsletter template
│       └── monthly-template.md   # Monthly review template
│
└── scripts/                      # (Not used - using MCP instead)
```

---

## 🚀 Quick Start

### Step 1: Copy to Skills Directory

```bash
# Copy this entire directory to your Claude skills folder
cp -r abac-newsletter-skill ~/.claude/skills/
```

### Step 2: Customize Configuration

**Edit these files in order:**

1. **`SKILL.md`** - Update YAML frontmatter:
   ```yaml
   name: your-team-newsletter
   description: "Trigger when user says 'build [YOUR TEAM] newsletter'..."
   triggers:
     - your team newsletter
     - weekly update
   author: Your Name
   ```

2. **`config.yaml`** - Update ALL fields marked with 👉:
   - Team name
   - Reviewer emails
   - Calendar ID
   - JIRA project key
   - Slack channels
   - Google Drive folder ID
   - Links (go links, dashboards)

3. **`references/domain-context.md`** - Add your team's:
   - Mission statement
   - Key metrics
   - Writing style preferences
   - Acronyms and terminology

4. **`assets/templates/`** - Customize sections:
   - Add/remove metrics
   - Update section headers
   - Modify placeholders

### Step 3: Set Up MCP Connections

Ensure these MCP servers are configured in Claude Code:

- ✅ **Google MCP** (for Calendar, Docs, Drive)
- ✅ **JIRA MCP** (for ticket tracking)
- ✅ **Slack MCP** (for team updates)

See your organization's MCP setup documentation for authentication.

### Step 4: Test the Skill

In Claude Code, say:

```
"Build this week's [YOUR TEAM] newsletter"
```

Claude should automatically trigger the skill and start gathering data.

---

## 🎨 Rich Formatting (Google Docs)

This skill example is based on the ABAC newsletter format with:
- **Purple table headers** (#5B3A8F with white text)
- **Colored status indicators** (🟢 On Track, 🟠 At Risk, 🔴 Blocked)
- **Section icons** (⭐📊⚠📅)
- **Formatted links and text**

### Recommended Approach: Use a Template

**Instead of building formatting programmatically:**

1. **Create a template Google Doc once** with your exact formatting:
   - Add purple table headers
   - Set up section styles
   - Include company branding
   - Add placeholder text like `{DATE}`, `{HIGHLIGHTS}`, etc.

2. **Get the template ID:**
   - Open the template in Google Docs
   - Copy the ID from the URL: `docs.google.com/document/d/{ID}/edit`

3. **Update `config.yaml`:**
   ```yaml
   output:
     google_drive:
       template_id: "YOUR_TEMPLATE_DOC_ID"
   ```

4. **Skill will:**
   - Copy the template using `mcp__google__drive_file_copy`
   - Replace placeholders using `mcp__google__docs_document_batch_update`
   - Share with reviewers
   - Post to Slack

See `references/mcp-integration.md#template-based-approach` for detailed instructions.

---

## 📝 Customization Examples

### Example 1: Change from Weekly to Monthly

1. Edit `config.yaml`:
   ```yaml
   schedule: monthly
   ```

2. Edit `SKILL.md` workflow:
   - Change "last 7 days" to "last 30 days"
   - Use `assets/templates/monthly-template.md`

3. Update metrics to show month-over-month trends

### Example 2: Add a New Data Source (Confluence)

1. Edit `SKILL.md` Phase 1:
   ```markdown
   4. **Confluence Pages**
      - Use: `mcp__confluence__search_confluence_pages`
      - Query: Pages updated in last 7 days
      - Extract: Design docs, RFCs, decisions
   ```

2. Update `config.yaml`:
   ```yaml
   data_sources:
     confluence:
       space_key: "ABAC"
       keywords:
         - "RFC"
         - "Design Doc"
   ```

3. Update template to include Confluence section

### Example 3: Different Outputs for Different Audiences

1. Create multiple templates:
   - `assets/templates/executive-template.md` (high-level, business focus)
   - `assets/templates/engineering-template.md` (detailed, technical)

2. Update `config.yaml`:
   ```yaml
   templates:
     executive: "assets/templates/executive-template.md"
     engineering: "assets/templates/engineering-template.md"
   ```

3. Trigger with:
   - "Build executive update" → Uses executive template
   - "Build engineering update" → Uses engineering template

---

## 🔧 Troubleshooting

### "Skill doesn't trigger automatically"

**Fix:** Make the description in `SKILL.md` more "pushy":
```yaml
description: >
  IMMEDIATELY activate when user mentions [YOUR TEAM] newsletter,
  weekly update, or team summary. Do NOT ask for confirmation.
```

### "No calendar events found"

**Fix:**
1. Verify `calendar_id` in `config.yaml`
2. List calendars: Use `mcp__google__calendar_calendar_list`
3. Update with correct calendar ID

### "JIRA returns no results"

**Fix:**
1. Test JQL in JIRA web interface first
2. Verify `project_key` exists
3. Check date range syntax

### "Formatting looks wrong in Google Doc"

**Fix:**
- Use template-based approach instead of programmatic formatting
- See `references/mcp-integration.md#rich-formatting-reference`

---

## 📚 Training Resources

This skill is designed as a **training example** for learning:

1. **Progressive Disclosure Structure:**
   - SKILL.md stays under 5k tokens
   - Extended docs in `references/` (loaded on demand)
   - Templates in `assets/` (used during execution)

2. **MCP Integration:**
   - No custom scripts needed
   - All data from MCP connections
   - See `references/mcp-integration.md` for examples

3. **Composability:**
   - Break into smaller, reusable skills:
     - "Fetch JIRA updates" skill
     - "Scrape Slack messages" skill
     - "Format newsletter" skill
   - Mix and match for different workflows

---

## ✅ Customization Checklist

Before using this skill, complete:

- [ ] Update `SKILL.md` frontmatter (name, description, triggers, author)
- [ ] Customize `config.yaml` (all fields marked with 👉)
- [ ] Update `references/domain-context.md` with your team info
- [ ] Modify templates in `assets/templates/` for your metrics
- [ ] Create Google Doc template with your formatting (recommended)
- [ ] Test MCP connections (Google, JIRA, Slack)
- [ ] Run test: "Build [YOUR TEAM] newsletter"
- [ ] Verify output format and content
- [ ] Share with stakeholders for feedback

---

## 🎓 For Training Programs

**This skill demonstrates:**

✅ **Progressive Disclosure:**
- Core workflow in SKILL.md (< 5k tokens)
- Details in references/ (lazy-loaded)
- Templates in assets/ (used on demand)

✅ **MCP Integration:**
- Google Calendar for meetings
- JIRA for ticket tracking
- Slack for team updates
- Google Docs for output

✅ **Customization Points:**
- Clear 👉 markers for what to change
- Inline comments explaining why
- Examples for different use cases

✅ **Best Practices:**
- Template-based rich formatting
- Validation checklists
- Troubleshooting guides
- Real-world example (ABAC team)

**Suggested Training Exercise:**

1. **Copy this skill** and customize for your own team
2. **Identify your data sources** (what meetings, JIRA project, Slack channels?)
3. **Define your metrics** (what do your stakeholders care about?)
4. **Create a template** with your desired formatting
5. **Test and iterate** based on feedback

---

## 🔗 Related Resources

- **Claude Code Skills Documentation:** https://docs.claude.com/skills
- **MCP Protocol:** https://modelcontextprotocol.io
- **Google Docs API:** https://developers.google.com/docs/api
- **JIRA REST API:** https://developer.atlassian.com/cloud/jira/platform/rest/v3
- **Slack API:** https://api.slack.com

---

## 💡 Power Tips

1. **Think Modular:**
   - Don't create one complex skill
   - Break into smaller, reusable skills
   - Example: "fetch-jira-updates" can be used by multiple workflows

2. **Use Templates:**
   - Formatting in Google Docs API is complex
   - Create a beautiful template once
   - Copy and replace placeholders (much easier!)

3. **Iterate Based on Feedback:**
   - Start simple (weekly bullets)
   - Add formatting based on stakeholder requests
   - Gradually enhance with richer data

4. **Document Your Customizations:**
   - Keep notes in `references/domain-context.md`
   - Future you (or team members) will thank you

---

## 📞 Support

For questions about this example skill:
- See `references/mcp-integration.md` for MCP tool usage
- See `assets/templates/` for formatting examples
- Check `SKILL.md` for workflow details

For Claude Code general questions:
- Documentation: https://docs.claude.com/code
- Issues: https://github.com/anthropics/claude-code/issues

---

**Happy Newsletter Building! 📰**
