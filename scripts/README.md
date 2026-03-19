# Scripts Directory

**Note:** This directory is intentionally empty.

## Why No Scripts?

This skill uses **MCP (Model Context Protocol) connections** instead of custom scripts.

### Traditional Approach (Scripts)
```python
# scripts/fetch-jira.py
import jira
# ... 50 lines of code ...
```

### MCP Approach (This Skill)
```python
# Just use MCP tools directly
mcp__jira__jira_read_api_call(
    endpoint="issues.search",
    params={"jql": "project = ABAC"}
)
```

---

## Benefits of Using MCP

✅ **No maintenance:** MCP servers are maintained centrally
✅ **No authentication hassles:** MCP handles auth
✅ **No dependencies:** No need to install Python libraries
✅ **Consistent API:** Same pattern for all integrations
✅ **Better error handling:** MCP provides built-in retry logic

---

## If You Need Custom Scripts

**When to use scripts:**
- Complex data transformations
- Integration with non-MCP services
- Custom business logic
- Performance-critical operations

**How to add scripts:**
1. Create executable files in this directory
2. Reference them in `SKILL.md` workflow
3. Document usage in this README
4. Make sure they're self-contained (handle their own dependencies)

**Example:**
```bash
# scripts/analyze-velocity.py
"""
Analyzes sprint velocity trends from JIRA data.
Usage: python scripts/analyze-velocity.py --project ABAC --sprints 6
"""
```

---

## What This Skill Uses Instead

**Data Sources:**
- `mcp__google__calendar_event_list` - Get meeting notes
- `mcp__jira__jira_read_api_call` - Query JIRA tickets
- `mcp__slack__slack_read_api_call` - Scrape Slack messages

**Output Generation:**
- `mcp__google__docs_document_create_from_markdown` - Create formatted docs
- `mcp__google__drive_file_copy` - Copy template docs
- `mcp__slack__slack_write_api_call` - Post notifications

See `references/mcp-integration.md` for detailed usage examples.

---

## Migration from Scripts to MCP

If you have existing scripts you want to migrate:

**Before (Script):**
```python
# scripts/fetch-slack.py
from slack_sdk import WebClient
client = WebClient(token=os.getenv("SLACK_TOKEN"))
response = client.conversations_history(channel="C123", limit=100)
```

**After (MCP):**
```python
# In SKILL.md workflow
slack_read_api_call(
    endpoint="conversations.history",
    params={"channel": "C123", "limit": 100}
)
```

**Migration Steps:**
1. Identify which MCP server provides the functionality
2. Use `{service}_get_api_info` to understand the MCP tool
3. Replace script calls with MCP tool calls in `SKILL.md`
4. Remove the script file
5. Update documentation

---

## For Training Programs

**Key Learning:**
- Modern Claude Code skills use MCP, not custom scripts
- Scripts are for edge cases, not primary workflow
- Focus on orchestration, not implementation

**Discussion Questions:**
- When would you still need a custom script?
- What are the tradeoffs of MCP vs. scripts?
- How would you handle a service without an MCP server?
