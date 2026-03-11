<div align="center">

# HubSpot MCP Server by Coupler.io

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Transport](https://img.shields.io/badge/Transport-Streamable_HTTP-blue.svg)](#)
[![Auth](https://img.shields.io/badge/Auth-OAuth_2.0-green.svg)](#)

Coupler.io HubSpot MCP server for Claude, ChatGPT, Gemini, Cursor, n8n, OpenClaw, and other MCP clients. Query and analyze HubSpot data with natural language. Requires the Coupler.io account.

</div>

## Data Access

Access deals, contacts, companies, tickets, activity logs, marketing emails, email statistics, performance reports, and more from your HubSpot account.

<details>
<summary><strong>Entities and report types</strong></summary>

| Entity | Type | Key use case |
|---|---|---|
| Deals | CRM records | Pipeline tracking, revenue forecasting |
| Contacts | CRM records | Lead management, lifecycle analysis |
| Companies | CRM records | Account-based reporting |
| Tickets | CRM records | Support volume and resolution tracking |
| Calls, Emails, Meetings, Notes, Tasks | Activity logs | Rep activity and engagement reporting |
| Quotes, Line items, Products | Sales objects | Quote-to-close and product revenue analysis |
| Leads | Sales Hub | Prospecting pipeline |
| Owners | Reference data | User-to-record mapping |
| Marketing emails | Marketing | Campaign performance |
| Email statistics by period | Reports | Aggregated email metrics over time |
| Performance report | Reports | Website traffic and UTM attribution |
| Workflows | Automation | Workflow audit and metadata |
| Feedback submissions | Service | NPS and CSAT trends |

</details>

<details>
<summary><strong>Deals fields</strong></summary>

| Field | Description |
|---|---|
| Deal name | The name of the deal |
| Pipeline | The pipeline the deal belongs to |
| Deal stage | Current stage in the pipeline |
| Amount | Deal value |
| Close date | Expected or actual close date |
| Owner | Assigned HubSpot user |
| Create date | When the deal was created |
| Last modified date | When the deal was last updated |
| Deal type | Type classification (e.g., New Business) |

</details>

<details>
<summary><strong>Contacts fields</strong></summary>

| Field | Description |
|---|---|
| First name / Last name | Contact's name |
| Email | Primary email address |
| Phone | Phone number |
| Lifecycle stage | Lead, MQL, SQL, Customer, etc. |
| Lead status | Contact qualification status |
| Owner | Assigned HubSpot user |
| Create date | When the contact was created |
| Last modified date | When the contact was last updated |
| Company | Associated company name |

</details>

<details>
<summary><strong>Companies fields</strong></summary>

| Field | Description |
|---|---|
| Company name | Name of the company |
| Domain | Website domain |
| Industry | Industry classification |
| Number of employees | Company size |
| Annual revenue | Reported revenue |
| City / Country | Location data |
| Owner | Assigned HubSpot user |
| Create date | When the record was created |

</details>

<details>
<summary><strong>Email statistics by period</strong></summary>

| Field | Description |
|---|---|
| Period | Date or period bucket |
| Sent | Emails sent in the period |
| Delivered | Successfully delivered emails |
| Opens | Total opens |
| Clicks | Total link clicks |
| Unsubscribes | Unsubscribe events |
| Bounces | Bounce events |

</details>

<details>
<summary><strong>Performance report fields</strong></summary>

| Field | Description |
|---|---|
| Period | Date or period bucket |
| Sessions | Website sessions |
| Page views | Total page views |
| Contacts (new) | New contacts generated |
| Bounce rate | Session bounce rate |
| Breakdown dimension | Source, UTM, page, form, geolocation, etc. |

</details>


## Supported Clients

*Note: You will need to set up a data flow in Coupler.io with HubSpot as a source and the AI tool of your choice as the destination.*

### Claude

Use with Claude Web, Desktop, Chat, Cowork, or Claude Code.

**Via Web/Desktop:** Go to **Customize**->**Connectors**->**Connect your tools**, search for Coupler.io and add it.

**Via Claude Code CLI:**

```bash
claude mcp add coupler-io --transport streamable-http https://mcp.coupler.io/mcp
```

### ChatGPT

Install from the **ChatGPT Apps** directory — search for "Coupler.io" in the **Apps** section of **Settings**.

### Cursor

Find it on the [Cursor Directory](https://cursor.directory/mcp/coupler-io-official-remote-mcp).

### Gemini CLI

Go to the **AI integrations** -> **Gemini CLI** page in your Coupler.io account to copy the correct command (unique to each account). It will look like this:

```bash
gemini mcp add coupler --transport=http https://mcp.coupler.io/mcp/xxxxx
```

### OpenClaw

Use the **mcporter** skill to connect, or install the **coupler-io** skill from ClawHub.
Directly ask your OpenClaw agent to add the skill and execute it.

## Links

- **Landing page:** [HubSpot MCP by Coupler.io](https://www.coupler.io/mcp/hubspot)
- **Coupler.io:** [https://coupler.io](https://coupler.io)
- **MCP Server endpoint:** `https://mcp.coupler.io/mcp`