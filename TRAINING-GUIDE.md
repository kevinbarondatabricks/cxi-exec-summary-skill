# ABAC Newsletter Skill - Training Guide

## 📦 What's Included

This is a **complete example skill** for your training program on building automated team newsletters with Claude Code.

### Complete File Structure

```
abac-newsletter-skill/
├── SKILL.md                                  ✅ Main skill definition
├── config.yaml                               ✅ Team configuration
├── README.md                                 ✅ Setup instructions
├── TRAINING-GUIDE.md                         ✅ This file
│
├── references/                               ✅ Extended documentation
│   ├── README.md                             ✅ Index
│   ├── domain-context.md                     ✅ Team context & style guide
│   ├── mcp-integration.md                    ✅ MCP tool examples
│   └── examples/
│       ├── simple-newsletter.md              ✅ Weekly example
│       └── quarterly-review.md               ✅ Quarterly example
│
├── assets/                                   ✅ Templates & resources
│   └── templates/
│       ├── weekly-template.md                ✅ Weekly template
│       └── monthly-template.md               ✅ Monthly template
│
└── scripts/                                  ✅ Explanation (uses MCP)
    └── README.md                             ✅ Why no scripts needed
```

**Total Files Created:** 11 files
**Based On:** Real ABAC team newsletter format with rich formatting

---

## 🎯 Training Objectives

Participants will learn:

1. **Progressive Disclosure Structure**
   - Core workflow in SKILL.md (< 5k tokens)
   - Extended docs in references/ (loaded on-demand)
   - Templates in assets/ (used during execution)

2. **MCP Integration**
   - Using Google Calendar, JIRA, Slack via MCP
   - No custom scripts needed
   - Tool discovery and usage patterns

3. **Rich Formatting**
   - Creating Google Docs with formatting
   - Template-based approach (recommended)
   - Color-coded tables and status indicators

4. **Skill Customization**
   - Clear 👉 markers for required changes
   - Config-driven behavior
   - Adapting for different teams/use cases

---

## 📝 Training Exercise

### Step 1: Review the Example (15 min)

**Have participants explore:**

1. Open `SKILL.md`
   - Review YAML frontmatter structure
   - Understand the 3-phase workflow
   - Note the MCP tool references

2. Open `config.yaml`
   - See all customization points (marked with 👉)
   - Understand data source configuration
   - Review output options

3. Open `assets/templates/weekly-template.md`
   - See placeholder structure
   - Note the validation checklist
   - Review rich formatting instructions

**Discussion Questions:**
- Why is SKILL.md kept under 5k tokens?
- What goes in references/ vs. assets/?
- Why use templates instead of building formatting from scratch?

---

### Step 2: Customize for Your Team (30 min)

**Each participant customizes the skill:**

**Required Changes:**
1. In `SKILL.md` frontmatter:
   ```yaml
   name: [your-team]-newsletter
   description: "When user says 'build [YOUR TEAM] newsletter'..."
   triggers:
     - [your team] newsletter
   author: [Your Name]
   ```

2. In `config.yaml`:
   - [ ] `team:` Your team name
   - [ ] `reviewers:` Your actual reviewers
   - [ ] `data_sources.meetings.calendar_id:` Your calendar
   - [ ] `data_sources.jira.project_key:` Your JIRA project
   - [ ] `data_sources.slack.channels:` Your Slack channels
   - [ ] `output.google_drive.folder_id:` Your Drive folder
   - [ ] `links:` Your go links and dashboards

3. In `references/domain-context.md`:
   - [ ] Team mission statement
   - [ ] Key metrics definitions
   - [ ] Writing style preferences
   - [ ] Acronyms used by your team

4. In `assets/templates/weekly-template.md`:
   - [ ] Update metrics section with your KPIs
   - [ ] Add/remove sections based on your needs
   - [ ] Customize validation checklist

**Optional:**
- Create a Google Doc template with your formatting
- Add custom sections (e.g., "Customer Wins", "Tech Debt")
- Modify for monthly instead of weekly

---

### Step 3: Test the Skill (15 min)

**Testing workflow:**

1. Copy skill to Claude skills directory:
   ```bash
   cp -r abac-newsletter-skill ~/.claude/skills/[your-team]-newsletter
   ```

2. Ensure MCP connections are set up:
   - ✅ Google MCP (Calendar, Docs, Drive)
   - ✅ JIRA MCP
   - ✅ Slack MCP

3. Test trigger in Claude Code:
   ```
   "Build this week's [YOUR TEAM] newsletter"
   ```

4. Verify Claude:
   - ✅ Automatically triggered the skill (no confirmation asked)
   - ✅ Started gathering data from sources
   - ✅ Used correct JIRA project, Slack channels, calendar

5. Review generated output:
   - ✅ Includes data from all sources
   - ✅ Follows template structure
   - ✅ Formatting is acceptable

**Troubleshooting:**
- If skill doesn't trigger → Make description more "pushy"
- If no data found → Check IDs in config.yaml
- If formatting wrong → Use template-based approach

---

### Step 4: Add Rich Formatting (20 min)

**Creating a template document:**

1. Open Google Docs and create a new document

2. Format it with your branding:
   - Add company logo
   - Set font styles
   - Create table with purple header (#5B3A8F)
   - Add section dividers

3. Add placeholder text:
   ```
   {DATE}
   {TEAM_NAME}
   {HIGHLIGHTS}
   {METRICS}
   {BLOCKERS}
   {NEXT_WEEK}
   ```

4. Get the template ID from the URL:
   ```
   docs.google.com/document/d/[TEMPLATE_ID]/edit
   ```

5. Update `config.yaml`:
   ```yaml
   output:
     google_drive:
       template_id: "[TEMPLATE_ID]"
   ```

6. Update `SKILL.md` to use copy & replace:
   ```markdown
   1. **Copy Template**
      - Use: `mcp__google__drive_file_copy`
      - Template ID from config.yaml

   2. **Replace Placeholders**
      - Use: `mcp__google__docs_document_batch_update`
      - Operation: find_replace
   ```

7. Test again and verify formatting is preserved

---

## 💡 Advanced Topics

### Breaking Into Smaller Skills (Composability)

**Instead of one large skill, create:**

1. **`fetch-jira-updates` skill:**
   - Just gets JIRA data
   - Reusable by other workflows
   - Outputs JSON

2. **`scrape-slack-messages` skill:**
   - Just gets Slack data
   - Can filter by reactions
   - Outputs JSON

3. **`format-newsletter` skill:**
   - Takes JSON input
   - Generates formatted doc
   - Uses templates

4. **`abac-newsletter` skill (orchestrator):**
   - Calls the 3 smaller skills
   - Coordinates the workflow
   - Very lightweight

**Benefits:**
- Easier to test each piece
- Reusable across workflows
- Clearer separation of concerns
- Can mix and match for different outputs

---

### Different Output Formats

**Email Newsletter:**
```yaml
output:
  format: email
  email:
    subject_format: "{team} Update - {date}"
    from_name: "Your Team"
```

**Slack Message:**
```markdown
In SKILL.md, use:
`mcp__slack__slack_write_api_call` to post formatted message
```

**Both Google Doc + Email:**
```markdown
Phase 3: Create doc AND send email summary
```

---

### Handling Multiple Audiences

**Create audience-specific templates:**

```yaml
# config.yaml
templates:
  executive: "assets/templates/executive-template.md"
  engineering: "assets/templates/engineering-template.md"
  customer: "assets/templates/customer-template.md"
```

**Trigger with different phrases:**
- "Build executive update" → Uses executive template
- "Build engineering update" → Uses engineering template

**Or create separate skills:**
- `executive-update` skill
- `engineering-update` skill
- Both reuse the same data-fetching logic

---

## 🎓 Discussion Topics

### 1. Progressive Disclosure Trade-offs

**Question:** What are the downsides of splitting docs across multiple files?

**Pros:**
- SKILL.md stays under token limit
- Faster initial loading
- Easier to maintain

**Cons:**
- More files to keep in sync
- Claude needs to know when to load references
- Harder to see full picture at once

**When to use:**
- Complex workflows with lots of detail
- When SKILL.md would exceed 5k tokens
- Shareable context across multiple skills

---

### 2. MCP vs. Custom Scripts

**Question:** When would you still write a custom script?

**Use MCP when:**
- Integration already exists as MCP server
- Standard CRUD operations
- Authentication is complex

**Use Scripts when:**
- Complex data transformations
- Performance-critical operations
- Custom business logic
- Service doesn't have MCP server

**Example:**
- ✅ MCP: Fetching JIRA tickets (standard query)
- ✅ Script: Analyzing velocity trends with ML model

---

### 3. Template vs. Programmatic Formatting

**Question:** Why is the template approach recommended?

**Template Approach (Recommended):**
- Create formatted doc once
- Copy and replace placeholders
- Easy to modify (anyone can edit template)
- Consistent output
- **CRITICAL:** Use plain text only in `replaceAllText` - NO HTML tags!

**Programmatic Approach:**
- Build formatting with API calls
- Complex code
- Hard to modify (need to update code)
- Fragile (API changes break things)

**⚠️ CRITICAL LESSON LEARNED:**
```python
# ❌ WRONG - HTML tags render as literal text
{"replaceText": "🟠 <b>At Risk</b>"}  # Shows: 🟠 <b>At Risk</b>

# ✅ CORRECT - Template already has formatting
{"replaceText": "🟠 At Risk"}  # Shows: 🟠 At Risk (bold from template)
```

**Best Practice:**
- Use templates for complex formatting (purple headers, colored tables)
- Use `replaceAllText` with plain text only (preserves template formatting)
- Never use HTML/markup tags in `replaceAllText` - they're literal characters

---

## 🔍 Common Mistakes & Solutions

### Mistake 1: Making SKILL.md Too Long

**Problem:** Including all context in SKILL.md (> 5k tokens)

**Solution:**
- Keep workflow in SKILL.md
- Move "why" and examples to references/
- Move templates to assets/

---

### Mistake 2: Hardcoding Values

**Problem:**
```markdown
channels:
  - abac-engineering  # Hardcoded in SKILL.md
```

**Solution:**
```markdown
channels: From config.yaml
```

Make everything configurable in config.yaml!

---

### Mistake 3: Not Providing Examples

**Problem:** Users don't know how to customize

**Solution:**
- Include real examples (like the PDF)
- Show before/after
- Provide templates with placeholders
- Add validation checklists

---

### Mistake 4: Using HTML Tags in replaceAllText

**Problem:**
```python
# This shows literal HTML in the doc!
{"replaceText": "🟠 <b>At Risk</b>"}
```

**Why it happens:**
- Thinking `replaceAllText` interprets HTML like a browser
- Google Docs API treats it as plain text

**Solution:**
```python
# Template already has bold formatting
{"replaceText": "🟠 At Risk"}  # Text inherits template's bold style
```

**Key insight:** When using template-based approach:
1. Format the template document manually (purple headers, bold text, etc.)
2. Use `replaceAllText` with **plain text only**
3. All formatting is preserved from template structure

---

### Mistake 5: Ignoring Error Handling

**Problem:** Skill fails silently when data source unavailable

**Solution:**
```markdown
In SKILL.md workflow:
- If no calendar events found, use last week's highlights
- If JIRA fails, pull from Slack updates only
- Always generate *something* even with partial data
```

---

## 📊 Success Metrics

How to measure if your skill is working:

**Adoption:**
- [ ] Team uses skill weekly without prompting
- [ ] Reviewers find format acceptable
- [ ] Stakeholders read the updates

**Quality:**
- [ ] 90%+ of data is accurate
- [ ] Formatting is consistent
- [ ] No placeholder text in output

**Efficiency:**
- [ ] Reduces newsletter creation time by 50%+
- [ ] Eliminates manual copy-paste from sources
- [ ] Fewer back-and-forth edits needed

**Maintainability:**
- [ ] New team members can customize it
- [ ] Changes to config don't require code updates
- [ ] Works after JIRA/Slack/Calendar schema changes

---

## 🚀 Next Steps After Training

**For Participants:**

1. **Deploy your customized skill:**
   ```bash
   cp -r [your-team]-newsletter ~/.claude/skills/
   ```

2. **Run it weekly for 1 month:**
   - Gather feedback from stakeholders
   - Iterate on formatting and content
   - Document learnings in references/

3. **Share learnings:**
   - What worked well?
   - What was hard to customize?
   - Ideas for improvement?

4. **Expand the skill:**
   - Add more data sources (Confluence, GitHub)
   - Create monthly/quarterly variants
   - Build related skills (team dashboard, OKR tracker)

---

## 📚 Additional Resources

**From This Example:**
- `README.md` - Setup and quick start
- `SKILL.md` - Main workflow reference
- `references/mcp-integration.md` - MCP tool examples
- `references/domain-context.md` - Customization guide

**External:**
- Claude Code Skills Docs: https://docs.claude.com/skills
- MCP Protocol: https://modelcontextprotocol.io
- Google Docs API: https://developers.google.com/docs/api

---

## ❓ FAQ

### Q: Can I use this for non-newsletter workflows?

**A:** Absolutely! The same structure works for:
- Incident reports (gather alerts, logs, metrics)
- Customer health reports (usage data, support tickets)
- Release notes (commits, PRs, deployments)
- OKR tracking (JIRA progress, metrics dashboards)

Adapt the data sources and templates to your use case.

---

### Q: Do I need all the data sources?

**A:** No! Customize based on what you have:
- Just JIRA? Remove calendar and Slack sections
- Just Slack? Make it a "weekly highlights" digest
- Just Google Docs? Use it to compile team RFCs

Update `config.yaml` and `SKILL.md` accordingly.

---

### Q: How do I handle authentication?

**A:** MCP handles it!
- MCP servers manage OAuth flows
- Claude Code prompts you to authenticate once
- Tokens are cached and refreshed automatically

No need to handle auth in your skill.

---

### Q: Can I schedule this to run automatically?

**A:** Not yet, but you can:
1. Set a calendar reminder to run it weekly
2. Create a Slack workflow that reminds you
3. Use a cron job to trigger Claude Code CLI (if available)

Future enhancement: Add scheduling to Claude Code.

---

### Q: What if my organization doesn't use JIRA?

**A:** Replace with your issue tracker:
- **GitHub Issues:** Use GitHub MCP
- **Linear:** Create Linear MCP or use API
- **Asana:** Use Asana API
- **Spreadsheet:** Pull from Google Sheets MCP

Update `data_sources.jira` in config.yaml and SKILL.md.

---

## 🎉 Conclusion

You now have a **complete, working example** of a Claude Code skill that:

✅ Uses progressive disclosure (< 5k tokens in SKILL.md)
✅ Integrates via MCP (no custom scripts needed)
✅ Generates rich formatted output (Google Docs)
✅ Is highly customizable (config-driven)
✅ Includes training materials and examples

**Key Takeaways:**
1. Break complex skills into layers (SKILL.md → references/ → assets/)
2. Use MCP instead of custom scripts when possible
3. Templates > Programmatic formatting for complex layouts
4. Make everything configurable (avoid hardcoding)
5. Provide examples and validation checklists

**Next:** Customize for your team and deploy! 🚀

---

**Questions?** Review:
- `README.md` for setup help
- `references/mcp-integration.md` for MCP examples
- `SKILL.md` for workflow details
