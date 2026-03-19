# MCP Integration Guide

<!-- 👉 This file shows how to use MCP tools for the newsletter workflow -->

## Overview

This skill uses MCP (Model Context Protocol) connections to integrate with:
- **Google MCP** - Calendar, Docs, Gmail
- **JIRA MCP** - Issue tracking
- **Slack MCP** - Team communications

All data fetching and document creation happens through MCP tools - no custom scripts needed.

**🚨 CRITICAL GLOBAL PREFERENCE:**
**Never use markdown for Google Docs.** Always either:
1. **Template-based:** Copy formatted template + `replaceAllText` (EASIEST)
2. **Programmatic:** Build rich text from scratch with proper formatting (ADVANCED)

**NEVER use:** `docs_document_create_from_markdown` - loses all formatting

---

## Phase 1: Gathering Context

### Google Calendar - Meeting Notes

**Tool:** `mcp__google__calendar_event_list`

**Example Usage:**
```python
# Get meetings from last 14 days
calendar_event_list(
    time_min="2026-03-05T00:00:00Z",
    time_max="2026-03-19T23:59:59Z",
    q="CXI Stand up OR CXI Sprint Planning",
    calendar_id="primary",
    max_results=50
)
```

**What to Extract:**
- Event title and date
- Description/notes from event
- Action items (look for keywords like "TODO", "Action:", "Decision:")
- Attendees for context

---

### Gmail - Gemini Meeting Summaries

**Tool:** `mcp__google__google_read_api_call`

Gemini generates meeting summary emails after CXI calls. These often end up in Trash, so always use `in:anywhere` to search all folders.

**Example Usage:**
```python
# Search for Gemini meeting notes (includes Trash and Spam)
google_read_api_call(
    endpoint="gmail/messages",
    params={
        "q": "in:anywhere from:me subject:(notes of CXI) newer_than:14d",
        "maxResults": 20
    }
)
```

**Gmail search query breakdown:**
- `in:anywhere` - searches all folders including Trash and Spam (default excludes these)
- `from:me` - Gemini summaries are sent from your own account
- `subject:(notes of CXI)` - matches Gemini's subject format for CXI meeting notes
- `newer_than:14d` - last 14 days to match the biweekly cycle

**What to Extract:**
- Key discussion points captured by Gemini
- Action items and owners
- Decisions made during the meeting
- Cross-reference with Calendar events to fill gaps

**Note:** After getting the message list, fetch individual message content using:
```python
google_read_api_call(
    endpoint="gmail/messages/{message_id}",
    params={"format": "full"}
)
```

---

### JIRA - Ticket Status

**Tool:** `mcp__jira__jira_read_api_call`

**Example Usage:**
```python
# First, get API info to understand parameters
jira_get_api_info(endpoint="issues.search")

# Then search for tickets
jira_read_api_call(
    endpoint="issues.search",
    params={
        "jql": "project = PLAT AND component = 'Support Platform' AND (status = 'In Progress' OR updated >= -14d)",
        "max_results": 50,
        "fields": ["summary", "status", "priority", "assignee", "updated"]
    }
)
```

**What to Extract:**
- Key (e.g., PLAT-156411)
- Summary (ticket title)
- Status (In Progress, Done, etc.)
- Priority (High, Medium, Low)
- Assignee
- Custom fields (e.g., Story Points)

**👉 CUSTOMIZE:** Update the JQL query in `config.yaml` for your project

---

### Slack - Team Updates

**Tool:** `mcp__slack__slack_read_api_call`

**Example Usage:**
```python
# First, get channel ID
slack_read_api_call(
    endpoint="conversations.list",
    params={"types": "public_channel,private_channel"}
)

# Then get messages from channel
slack_read_api_call(
    endpoint="conversations.history",
    params={
        "channel": "C1234567890",  # Channel ID
        "oldest": "1709769600",     # Unix timestamp (7 days ago)
        "limit": 100
    }
)
```

**What to Extract:**
- Messages with important reactions (🚀, 🎯, ⭐)
- Threads with high engagement
- Announcements or decisions
- Links to important documents

**Filtering by Reactions:**
```python
# Filter messages that have specific reactions
messages_with_reactions = [
    msg for msg in messages
    if 'reactions' in msg and
    any(r['name'] in ['rocket', 'dart', 'star'] for r in msg['reactions'])
]
```

---

## Phase 2: Creating Rich Formatted Google Docs

### Creating a Document with Rich Formatting

**Tool:** `mcp__google__docs_document_create_from_markdown`

This is the RECOMMENDED approach for rich formatting. Write content in markdown, and it automatically converts to a formatted Google Doc.

**Example:**
```python
docs_document_create_from_markdown(
    title="CXI Executive Summary - March 19, 2026",
    markdown_file_path="/path/to/newsletter.md"
)
```

---

### Advanced: Using HTML-like Formatting with Batch Updates

For the EXACT formatting style shown in the PDF example, use `docs_document_batch_update` with Atlassian Document Format (ADF) style requests.

**Step 1: Create blank document**
```python
result = mcp__google__docs_document_create(
    title="CXI Executive Summary - March 19, 2026"
)
document_id = result['documentId']
```

**Step 2: Add formatted content**

Here's how to recreate the PDF example formatting:

#### Header Section (with colored background)
```python
# Create colored header box (like the blue info box in PDF)
docs_document_batch_update(
    document_id=document_id,
    operation_type="modify_text",
    start_index=1,
    text="📪 Feedback or Questions? Please click here\nSelf-Link: go/cxi\nFAQs: go/cxi\n\n",
    font_size=10,
    background_color={"red": 0.85, "green": 0.92, "blue": 0.97}  # Light blue
)
```

#### Upcoming Launches Table (Purple Header)
```python
# Create table with data
docs_document_batch_update(
    document_id=document_id,
    operation_type="create_table_with_data",
    index=1,  # Insert at beginning
    table_data=[
        ["Launch Stage", "Status", "Launch Date"],  # Header row
        ["Support Agent MVP | DBSQL", "🟢 On Track", "End of Q1 2026"],
        ["Case Summarization + NBA Evals", "🟢 On Track", "Mid-March 2026"],
        ["Merlin DBSQL Auto-Collection", "🟢 On Track", "Delivered"]
    ],
    bold_headers=True
)

# Then format the header row with purple background
# Note: This requires additional batch update requests to:
# 1. Set header row background color to purple (#5B3A8F)
# 2. Set header row text color to white
# 3. Add borders to table
```

#### Risks/Blockers Table (Detailed)
```python
table_data = [
    ["Issue", "Impacting Milestone", "Mitigation/Next Steps", "Owner", "Notes"],
    ["Salesforce write integration dependency", "Support Agent MVP", "IT/BSE dependency for near-real-time case data", "Kevin Baron", "Partial manual entry required until resolved"]
]

docs_document_batch_update(
    document_id=document_id,
    operation_type="create_table_with_data",
    index=100,  # Insert after other content
    table_data=table_data,
    bold_headers=True
)
```

**Recommended Template Approach:**
Instead of building complex formatting programmatically, create a **template Google Doc** with your desired formatting, then:
1. Copy it using `mcp__google__drive_file_copy`
2. Update the content using find/replace with `docs_document_batch_update`

---

### Template-Based Approach (RECOMMENDED - EASIEST)

**This is the BEST approach for rich formatting like purple headers, colored tables, etc.**

**Step 1:** Create a template document once with all formatting
- Purple table headers (#5B3A8F with white text)
- Colored cell backgrounds
- Section formatting, fonts, styles
- All visual elements you want preserved

**Step 2:** Copy and update content (NOT formatting!)

```python
# Copy the template
new_doc = mcp__google__drive_file_copy(
    file_id="YOUR_TEMPLATE_DOC_ID",  # From config.yaml
    name=f"CXI Executive Summary - {today_date}"
)

# Update content using replaceAllText requests
# CRITICAL: Use PLAIN TEXT only - NO HTML tags!
docs_document_batch_update(
    document_id=new_doc['id'],
    requests=[
        {
            "replaceAllText": {
                "containsText": {"text": "PLACEHOLDER_DATE", "matchCase": False},
                "replaceText": "March 7, 2026"
            }
        },
        {
            "replaceAllText": {
                "containsText": {"text": "PLACEHOLDER_HIGHLIGHTS", "matchCase": False},
                "replaceText": "Launched new feature X\nCompleted milestone Y"
            }
        },
        {
            "replaceAllText": {
                "containsText": {"text": "🟠 At Risk", "matchCase": False},
                "replaceText": "🟢 On Track"  # Plain text - NO <b>On Track</b>
            }
        }
    ]
)
```

**⚠️ CRITICAL LESSON: DO NOT USE HTML TAGS**

**WRONG:**
```python
"replaceText": "🟠 <b>At Risk</b>"  # ❌ HTML tags render as literal text!
```

**CORRECT:**
```python
"replaceText": "🟠 At Risk"  # ✅ Template already has bold formatting
```

**Why this works:**
- Template has all formatting (bold, colors, tables) baked in
- `replaceAllText` only changes text content, preserves formatting
- HTML tags in `replaceAllText` are treated as literal characters, not markup

**👉 ACTION ITEM:**
1. Create a formatted Google Doc template with your exact styling
2. Add placeholder text like "PLACEHOLDER_DATE", "PLACEHOLDER_HIGHLIGHTS"
3. Save template ID in `config.yaml` → `output.google_drive.template_id`
4. Use `replaceAllText` to swap placeholders with actual content (plain text only!)

---

### Programmatic Approach (ADVANCED)

**When to use:** Building documents from scratch without a template, or when you need full control over structure.

**🚨 CRITICAL FORMATTING RULES:**

These rules apply to ALL Google Docs creation (newsletters, reports, templates, etc.):

#### 1. No Empty Separator Paragraphs
**❌ WRONG:**
```python
# Don't insert empty paragraphs for spacing
{"insertText": {"location": {"index": 1}, "text": "\n\n\n"}}
```

**✅ CORRECT:**
```python
# Use paragraph spacing styles instead
{"updateParagraphStyle": {
    "range": {"startIndex": 1, "endIndex": 50},
    "paragraphStyle": {
        "spaceAbove": {"magnitude": 12, "unit": "PT"},
        "spaceBelow": {"magnitude": 12, "unit": "PT"}
    },
    "fields": "spaceAbove,spaceBelow"
}}
```

#### 2. Reset Bullet Paragraphs to NORMAL_TEXT
**After applying bullets, reset the named style:**
```python
# First apply bullets
{"createParagraphBullets": {
    "range": {"startIndex": 10, "endIndex": 100},
    "bulletPreset": "BULLET_DISC_CIRCLE_SQUARE"
}},
# Then reset to NORMAL_TEXT
{"updateParagraphStyle": {
    "range": {"startIndex": 10, "endIndex": 100},
    "paragraphStyle": {"namedStyleType": "NORMAL_TEXT"},
    "fields": "namedStyleType"
}}
```

#### 3. Collapse Undeletable Table-Adjacent Paragraphs
**Google Docs inserts paragraphs before/after tables that can't be deleted:**
```python
# Collapse them to 1pt with lineSpacing 10
{"updateParagraphStyle": {
    "range": {"startIndex": table_start - 1, "endIndex": table_start},
    "paragraphStyle": {
        "lineSpacing": 10,
        "spaceAbove": {"magnitude": 1, "unit": "PT"},
        "spaceBelow": {"magnitude": 1, "unit": "PT"}
    },
    "fields": "lineSpacing,spaceAbove,spaceBelow"
}}
```

#### 4. Use Raw insertTable + Backwards Population
**❌ DON'T use `operation_type="create_table_with_data"`**

**✅ DO use raw `insertTable` and populate backwards:**
```python
# Step 1: Insert empty table
{"insertTable": {
    "rows": 5,
    "columns": 3,
    "location": {"index": 1}
}}

# Step 2: Populate cells BACKWARDS (last to first)
# This avoids index shifting issues
{"insertText": {
    "location": {"index": cell_5_3_start},
    "text": "Last cell content"
}},
{"insertText": {
    "location": {"index": cell_5_2_start},
    "text": "Second to last"
}},
# ... continue backwards to first cell
{"insertText": {
    "location": {"index": cell_1_1_start},
    "text": "First cell content"
}}
```

#### 5. Table Styling via Row/Column Indices
**Style tables by row/column index, not cell-by-cell:**
```python
# Purple header row (#5B3A8F with white text)
{"updateTableCellStyle": {
    "tableStartLocation": {"index": table_start},
    "tableRange": {
        "tableCellLocation": {"tableStartLocation": {"index": table_start}, "rowIndex": 0, "columnIndex": 0},
        "rowSpan": 1,
        "columnSpan": 3  # All columns in header row
    },
    "tableCellStyle": {
        "backgroundColor": {
            "color": {"rgbColor": {"red": 0.357, "green": 0.227, "blue": 0.561}}  # #5B3A8F
        }
    },
    "fields": "backgroundColor"
}},
# White text for header row
{"updateTextStyle": {
    "range": {"startIndex": header_row_start, "endIndex": header_row_end},
    "textStyle": {
        "foregroundColor": {"color": {"rgbColor": {"red": 1.0, "green": 1.0, "blue": 1.0}}},
        "bold": True
    },
    "fields": "foregroundColor,bold"
}}
```

#### 6. Explicit Formatting Reference Table

**Always define colors and sizes explicitly:**

```python
# Color Palette
COLORS = {
    "purple_header": {"red": 0.357, "green": 0.227, "blue": 0.561},  # #5B3A8F
    "light_blue_bg": {"red": 0.898, "green": 0.949, "blue": 0.980},  # #E5F2FA
    "white": {"red": 1.0, "green": 1.0, "blue": 1.0},
    "black": {"red": 0.0, "green": 0.0, "blue": 0.0}
}

# Font Sizes (in PT)
SIZES = {
    "heading_1": 20,
    "heading_3": 14,
    "body": 11,
    "small": 9
}

# Example usage
{"updateTextStyle": {
    "textStyle": {
        "fontSize": {"magnitude": SIZES["heading_3"], "unit": "PT"},
        "foregroundColor": {"color": {"rgbColor": COLORS["purple_header"]}},
        "bold": True
    }
}}
```

#### Complete Example: Building CXI Executive Summary from Scratch

```python
# 1. Create blank document
doc = mcp__google__docs_document_create(title="CXI Executive Summary - March 19, 2026")
doc_id = doc['documentId']

# 2. Build requests array (all batched together)
requests = []

# Insert title
requests.append({"insertText": {"location": {"index": 1}, "text": "CXI | Biweekly Executive Summary | March 19, 2026\n"}})

# Style title
requests.append({"updateTextStyle": {
    "range": {"startIndex": 1, "endIndex": 58},
    "textStyle": {
        "fontSize": {"magnitude": 16, "unit": "PT"},
        "bold": True
    },
    "fields": "fontSize,bold"
}})

# Insert info box paragraph
requests.append({"insertText": {"location": {"index": 59}, "text": "📪 Feedback or Questions? Please click here\nSelf-Link: go/cxi\nFAQs: go/cxi\n"}})

# Style info box with light blue background
requests.append({"updateParagraphStyle": {
    "range": {"startIndex": 59, "endIndex": 150},
    "paragraphStyle": {
        "backgroundColor": {"color": {"rgbColor": {"red": 0.898, "green": 0.949, "blue": 0.980}}}
    },
    "fields": "backgroundColor"
}})

# Collapse paragraph before table
next_index = 151
requests.append({"updateParagraphStyle": {
    "range": {"startIndex": next_index, "endIndex": next_index + 1},
    "paragraphStyle": {
        "lineSpacing": 10,
        "spaceAbove": {"magnitude": 1, "unit": "PT"}
    },
    "fields": "lineSpacing,spaceAbove"
}})

# Insert table
table_index = next_index + 1
requests.append({"insertTable": {
    "rows": 5,
    "columns": 3,
    "location": {"index": table_index}
}})

# Populate table cells BACKWARDS
# (Calculate indices after table insertion)
# ... cell population code ...

# Style header row purple
requests.append({"updateTableCellStyle": {
    "tableStartLocation": {"index": table_index},
    "tableRange": {
        "tableCellLocation": {"tableStartLocation": {"index": table_index}, "rowIndex": 0},
        "rowSpan": 1,
        "columnSpan": 3
    },
    "tableCellStyle": {
        "backgroundColor": {"color": {"rgbColor": {"red": 0.357, "green": 0.227, "blue": 0.561}}}
    },
    "fields": "backgroundColor"
}})

# Execute all requests in one batch
mcp__google__docs_document_batch_update(
    document_id=doc_id,
    requests=requests
)
```

**⚠️ Key Takeaways:**
1. **Spacing:** Use paragraph styles, not empty paragraphs
2. **Bullets:** Reset to NORMAL_TEXT after applying
3. **Tables:** Use `insertTable` + backwards population
4. **Table styling:** Row/column indices, not individual cells
5. **Colors:** Explicit RGB values in reference table
6. **Never use markdown** for Google Docs - always programmatic or template-based

---

## Phase 3: Sharing and Notifications

### Adding Reviewers to Google Doc

**Method 1: Add as commenters**
```python
# Share doc with reviewer
# (Currently done through Drive sharing UI or API)
# Add comment to notify them
mcp__google__drive_comment_create(
    file_id=document_id,
    content="@sam.shah Please review this sprint's exec biweekly by EOD Friday"
)
```

**Method 2: Email the link**
```python
gmail_message_send(
    to="sam.shah@databricks.com",
    subject="CXI Executive Summary - Ready for Review",
    body=f"""
Hi Sam,

The CXI executive summary is ready for your review:
{doc_url}

Please provide feedback by EOD Friday.

Thanks!
    """
)
```

---

### Posting to Slack

**Tool:** `mcp__slack__slack_write_api_call`

```python
slack_write_api_call(
    endpoint="chat.postMessage",
    params={
        "channel": "#support-automation",
        "text": f"📰 CXI Executive Summary draft ready for review: {doc_url}",
        "unfurl_links": True  # Shows preview of the Google Doc
    }
)
```

**👉 CUSTOMIZE:** Update channel name in `config.yaml`

---

## Troubleshooting

### Issue: "Calendar events not found"
**Cause:** Incorrect calendar ID or insufficient permissions

**Fix:**
1. List available calendars: `calendar_calendar_list()`
2. Find the correct calendar ID
3. Update `config.yaml` with the correct ID

---

### Issue: "JIRA search returns empty"
**Cause:** Invalid JQL or project key

**Fix:**
1. Test your JQL in JIRA web interface first
2. Verify project key exists
3. Check date range (use relative dates like `-7d`)

---

### Issue: "Slack channel not found"
**Cause:** Bot not added to channel or wrong channel name

**Fix:**
1. List channels: `slack_read_api_call(endpoint="conversations.list")`
2. Ensure your MCP Slack bot is added to the channel
3. Use channel ID instead of name if needed

---

### Issue: "Google Doc formatting looks wrong"
**Cause:** Complex formatting via API is difficult

**Solution:** Use the **template-based approach** (see above)
1. Create a beautifully formatted template once
2. Copy it and update placeholders
3. Much easier than building formatting from scratch

---

## Example: Complete Newsletter Generation

```python
# 1. Gather data from all sources
calendar_events = calendar_event_list(
    time_min="2026-03-05T00:00:00Z",
    time_max="2026-03-19T23:59:59Z",
    q="CXI"
)

gemini_notes = google_read_api_call(
    endpoint="gmail/messages",
    params={
        "q": "in:anywhere from:me subject:(notes of CXI) newer_than:14d",
        "maxResults": 20
    }
)

jira_tickets = jira_read_api_call(
    endpoint="issues.search",
    params={"jql": "project = PLAT AND component = 'Support Platform' AND updated >= -14d"}
)

slack_messages = slack_read_api_call(
    endpoint="conversations.history",
    params={"channel": "C1234567890", "oldest": "1709769600"}
)

# 2. Create content (use template from assets/templates/biweekly-template.md)
newsletter_content = generate_newsletter(
    meetings=calendar_events,
    tickets=jira_tickets,
    slack=slack_messages
)

# 3. Create Google Doc from markdown
doc = docs_document_create_from_markdown(
    title=f"CXI Executive Summary - {today}",
    file_content=newsletter_content
)

# 4. Notify reviewers
slack_write_api_call(
    endpoint="chat.postMessage",
    params={
        "channel": "#support-automation",
        "text": f"📰 CXI Executive Summary ready: {doc['web_view_link']}"
    }
)
```

---

## Rich Formatting Reference (Based on PDF Example)

### Color Palette
```python
# Header background (light blue)
header_bg = {"red": 0.85, "green": 0.92, "blue": 0.97}

# Table header (purple)
table_header_bg = {"red": 0.36, "green": 0.23, "blue": 0.56}  # #5B3A8F
table_header_text = {"red": 1.0, "green": 1.0, "blue": 1.0}   # White

# Status colors
status_at_risk = {"red": 1.0, "green": 0.6, "blue": 0.0}      # Orange
status_on_track = {"red": 0.0, "green": 0.8, "blue": 0.0}     # Green

# Light row backgrounds (alternating)
row_light = {"red": 0.95, "green": 0.95, "blue": 1.0}         # Very light purple
```

### Section Headers
```markdown
⭐ Executive Summary
📊 Metrics
⚠ Risks/Blockers
```

### Table Structure
- **Header row:** Purple background (#5B3A8F), white text, bold
- **Data rows:** Alternating white and light purple
- **Borders:** All cells
- **Status indicators:** Colored circles (🟠🟢) with text

**👉 RECOMMENDATION:** Create a template doc with this exact formatting, then use the copy & replace method rather than building it programmatically.

---

## Template Document ID Storage

**Add to `config.yaml`:**
```yaml
templates:
  google_doc_template_id: "1_Wqcl7rmWHME4vGkKiCLs-3BXIdYE7gH7wbxuzW27ys"
```

Then reference it in your workflow:
```python
template_id = config['templates']['google_doc_template_id']
new_doc = drive_file_copy(file_id=template_id, name=new_title)
```
