# Example: Simple Weekly Newsletter

This example shows a basic weekly update similar to the PDF format.

## Input
```
User: "Build this week's ABAC newsletter"
```

## Data Sources
- 2 sprint planning meetings
- 8 JIRA tickets (5 in progress, 3 completed)
- 23 relevant Slack messages

---

## Generated Output (Rich Format)

**Note:** This markdown shows the structure. When using `docs_document_create_from_markdown`, it will convert to a formatted Google Doc. For the exact PDF styling (colored tables, purple headers), use the template-based approach described in `references/mcp-integration.md`.

---

# ABAC + Permission Model | Weekly Update | Mar 7, 2026

📪 **Feedback or Questions?** Please [click here](mailto:team@company.com)
**Self-Link:** go/abac-update
**FAQs:** go/abac-faqs

ℹ️ Unity Catalog's attribute-based access controls (ABAC) will enable data teams to define access policies for workspaces based on Governed Tags. This provides a scalable access management framework and simplifies provisioning.

---

## Upcoming Launches

| Launch Stage | Status | Launch Date |
|-------------|--------|-------------|
| ABAC RLS/CM \| GA | 🟠 **At Risk** | End of March 2026 |
| Fine Grained DDL/DML \| Private Preview for Capital One | 🟢 **On Track** | Mid-March 2026 |
| DENY MANAGE GRANT \| Private Preview for JPMC | 🟢 **On Track** | April 30, 2026 |
| VIEW_ADMIN_METADATA \| Private Preview for JPMC | 🟢 **On Track** | April 30, 2026 |

---

## ⭐ Executive Summary

### ABAC RLS/CM GA
- ABAC GA is blocked on the following two decisions. We will close on the decision and provide an updated GA timeline by 3/13.
  - What is our acceptable UC Latency and policy quota limit at GA Time?
  - What is our complete rollout plan for Session Identity behavior change?

### Fine-Grained DDL/DML Permissions | CapOne Escalation
- Delivery on track for mid-March customer milestone (CapOne). Go/No-Go scheduled for March 9th.
- Bugbash was completed with no blockers.

### DENY_MANAGE_GRANT | JPMC Escalation
- ABAC DENY MANAGE_GRANT will be code complete by 03/10 with bug bash scheduled on 03/16.
- Broader DENY Private Preview (beyond the current JPMC escalation) is targeting late April or early May; UI work is needed to support non-JPMC customers.

### READ_METADATA | JPMC Escalation
- MANAGE_GRANT and VIEW_METADATA support is code-complete, and the bug bash is scheduled for 03/02. It is being deployed to production by 3/13 (behind the feature flag).

---

## 📊 ABAC PuPr - Customer Usage Metrics | [Link to Usage Dashboard](https://dashboard.example.com)

- **Daily Active Users:** 3,670 (as of 3/05)
- **Weekly Active Customers:** 651

---

## ⚠ Risks/Blockers

| Issue | Impacting Milestone | Mitigation/Next Steps | Owner | Notes |
|-------|--------------------|-----------------------|-------|-------|
| Session Identity behavior change rollout plan | ABAC GA | We will review the rollout plan and make the decision for cut line for GA by 3/13 | Corey Sunwold | Scope changes may further push the GA timeline |
| Decide the acceptable UC Latency and policy quota limit at GA Time | ABAC GA | We will review the 1DD and close on the decision by 3/13. | Corey Sunwold | If further improvements need to be made in order to safely raise the limits the GA timeline may need to be adjusted further. |

---

## 📅 Next Week's Focus

- Finalize UC Latency and policy quota limits decision (3/13)
- Complete Session Identity rollout plan (3/13)
- CapOne Go/No-Go meeting (3/09)
- READ_METADATA bug bash (3/02)

---

**Questions?** Reach out in [#abac-leadership](https://company.slack.com/archives/C123456) or reply to this thread.

---

## Customization Notes

### For Your Team:

**👉 Replace these placeholders:**
- Team name: "ABAC + Permission Model" → Your team name
- Links: go/abac-update → Your team's link
- Metrics: "Daily Active Users" → Your KPIs
- Launch items: Replace with your milestones
- Risks table: Update with your blockers

**👉 Add/Remove Sections:**
- If you don't have launches, remove that section
- Add "Customer Wins" if relevant
- Add "Team Highlights" for non-technical updates

**👉 For Rich Formatting (Purple Headers, Colored Status):**
See `references/mcp-integration.md#rich-formatting-reference` for:
- Creating a template Google Doc with exact formatting
- Using `drive_file_copy` + find/replace approach
- Color codes for status indicators
