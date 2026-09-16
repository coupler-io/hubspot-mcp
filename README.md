<div align="center">

# HubSpot MCP Server by Coupler.io

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Transport](https://img.shields.io/badge/Transport-Streamable_HTTP-blue.svg)](#)
[![Auth](https://img.shields.io/badge/Auth-OAuth_2.0-green.svg)](#)

Connect HubSpot data to AI with the Coupler.io MCP server. Ask natural-language questions about contacts, companies, deals, sales pipelines, activities, marketing performance, and other CRM data in ChatGPT, Claude, Gemini, Cursor, and other MCP-compatible AI tools. Requires a Coupler.io account.

[Landing page](https://www.coupler.io/mcp/hubspot) · [Documentation](https://docs.coupler.io/ai/mcp) · [All Coupler.io MCP integrations](https://github.com/coupler-io)

</div>

## What you can ask

- Which deals are most likely to close this month?
- How has pipeline value changed quarter over quarter?
- Which sales reps generate the most revenue?
- Compare marketing email engagement by campaign.
- Which industries generate our highest-value customers?

## How it works

This repository documents the HubSpot integration for the Coupler.io MCP server.

1. Connect HubSpot to Coupler.io.
2. Select your AI tool as the destination.
3. Connect your AI client to Coupler.io MCP.
4. Ask questions about your HubSpot data in natural language.

Coupler.io sits between HubSpot and your AI client. It holds the HubSpot credential, imports the data on a schedule, and exposes the result as a data set the AI can query. Your AI client never calls the HubSpot API itself.

```
  HubSpot
      |        credential held by Coupler.io
      v
  Coupler.io          import, transform, store on a schedule
      |
      v
  MCP server          schema, SQL query execution
      |
      v
  Your AI client      your question, in plain language
```

When you ask a question, the AI reads the data set's schema, writes SQL, and Coupler.io runs that query on its own side. Only the result comes back to the AI, so a large data set does not have to fit into the model's context window.

| | |
|---|---|
| **MCP endpoint** | `https://mcp.coupler.io/mcp` |
| **Transport** | Streamable HTTP |
| **Authentication** | OAuth 2.0 |
| **Query language** | SQL, executed by Coupler.io |
| **Refresh schedule** | From monthly to every 15 minutes, depending on your plan |

## Get started

*Note: You will need to set up a data flow in Coupler.io with HubSpot as a source and the AI tool of your choice as the destination.*

### Claude

Use with Claude Web, Desktop, Chat, Cowork, or Claude Code.

**Via Web/Desktop:** Go to **Customize**->**Connectors**->**Connect your tools**, search for Coupler.io and add it.

**Via Claude Code CLI:**

```bash
claude mcp add coupler-io --transport streamable-http https://mcp.coupler.io/mcp
```

### ChatGPT

Install the [Coupler.io ChatGPT app](https://l.rw.rw/couplerio-chatgpt-app) and complete the authentication. You can also find it by searching for "Coupler.io" in the **Apps** section of **Settings**.

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

## Data you can access

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

Coupler.io imports only the entities and fields you select in the data flow, including any custom properties you add to the source configuration.

## Example questions

### Pipeline

- How has total pipeline value changed quarter over quarter by stage?
- Which deals are scheduled to close this month, and what is their combined value?
- Where is the biggest conversion drop between deal stages?

### Reps and sources

- Which owners closed the most revenue last quarter?
- Compare win rate and average deal size by owner.
- Which industries produce our highest-value customers?

### Marketing and service

- Compare marketing email open and click rates by campaign.
- How many contacts moved from MQL to SQL last month?
- What is our ticket volume and resolution trend by month?

## Security and permissions

Your AI client never connects to HubSpot directly. Coupler.io holds the HubSpot credential, imports the data, and exposes only the resulting data set over MCP.

- **Your HubSpot data is never modified.** Coupler.io only reads from HubSpot. The AI queries the copy Coupler.io imported and cannot edit, delete, or overwrite it, let alone write anything back to your HubSpot account.
- **Visibility is scoped per AI tool.** An AI client sees only the data sets from data flows that have *that client* set as a destination. Adding Claude as a destination does not expose the data flow to ChatGPT, though one flow can name both.
- **Configuration changes are possible, and confirmed first.** With the full tool set available, the AI can create data flows, add sources and destinations, change a schedule, or trigger a run. Those are real changes to your workspace, so the server instructs the AI to confirm before making one you did not ask for.
- **Nothing else is reachable.** The MCP server exposes the data sets described above and nothing more. It cannot reach your other accounts or your machine.
- **Disconnect at any time** by removing the connector in your AI client, or by deleting the credential or the data flow in Coupler.io.

Coupler.io is SOC 2 certified and compliant with GDPR and HIPAA.

## Troubleshooting

**The AI cannot find my HubSpot data set.**
Usually you have not added that AI tool as a destination yet. Open the data flow in Coupler.io and add your AI client. One data flow can have several AI tools as destinations at the same time, so adding ChatGPT does not displace Claude. Each tool sees only the flows it is named on.

**The numbers look out of date.**
The AI reads the last imported snapshot, not HubSpot live. Check the data flow's refresh schedule, or ask your AI client to run the data flow now.

**A field I need is missing.**
Coupler.io imports only the fields you select in the data flow's source. Add the missing fields and re-run the flow.

**The AI misreads a metric.**
Save the business context on the data set: what a metric means, which currency it is in, which rows to exclude. You do not have to leave your AI tool to do it, just tell the assistant to update the data set context and it saves it for you. The AI reads that context before it queries, so the next conversation uses your definitions instead of guessing.

**The connector does not appear in my AI client.**
Availability differs by AI client and subscription plan. Follow the client-specific steps under [Get started](#get-started), and check the [AI destination docs](https://docs.coupler.io/destinations/categories/ai) for that tool.

## Related Coupler.io MCP integrations

- [Google Ads MCP](https://github.com/coupler-io/google-ads-mcp) — connect paid search campaigns with leads and deals
- [Facebook Ads MCP](https://github.com/coupler-io/facebook-ads-mcp) — analyze paid social campaigns alongside CRM performance
- [Google Analytics 4 MCP](https://github.com/coupler-io/google-analytics-4-mcp) — connect website acquisition and behavior with CRM outcomes
- [Google BigQuery MCP](https://github.com/coupler-io/google-bigquery-mcp) — analyze CRM data together with other business datasets

[Explore all Coupler.io MCP integrations](https://github.com/coupler-io)

## FAQ

### What is the HubSpot MCP server?

It is the HubSpot integration for the Coupler.io MCP server, an endpoint that lets AI clients query your HubSpot data in plain language. Coupler.io imports the data, stores it, and answers the AI's SQL queries on its own infrastructure.

### Do I need a Coupler.io account?

Yes. The MCP server serves data from your Coupler.io workspace, so you need an account with a data flow that has HubSpot as a source and your AI tool as a destination.

### Does this connect directly to my HubSpot account?

No. Coupler.io connects to HubSpot, imports the data, and exposes the resulting data set over MCP. Your AI client talks to Coupler.io, never to HubSpot.

### Which HubSpot data can AI access?

Whatever your data flow imports. See [Data you can access](#data-you-can-access) for the full catalog of report types and fields. The AI reaches only the data sets in flows that name your AI tool as a destination.

### Is the integration read-only?

Yes. Nothing you or your AI client does through Coupler.io changes your HubSpot data. Coupler.io only reads from HubSpot, and the AI only queries the copy Coupler.io imported. It cannot edit, delete, or write anything back to your HubSpot account.

### Which AI assistants can I use?

Claude, ChatGPT, Cursor, Gemini CLI, OpenClaw, Perplexity, and any client that speaks MCP through the Custom MCP destination. Setup steps for the clients above are under [Get started](#get-started); for the rest, see the [AI destination docs](https://docs.coupler.io/destinations/categories/ai).

### Do I need to write SQL or code?

No. You ask in plain language; the AI writes the SQL and Coupler.io runs it. Writing SQL yourself stays an option if you want a specific transformation.

### How fresh is the data?

As fresh as the last data flow run. Schedules range from monthly to every 15 minutes depending on your plan, and you can ask your AI client to refresh the flow on demand.

## Links

- **Landing page:** [HubSpot MCP by Coupler.io](https://www.coupler.io/mcp/hubspot)
- **Documentation:** [Coupler.io MCP](https://docs.coupler.io/ai/mcp)
- **Coupler.io:** [https://coupler.io](https://coupler.io)
- **MCP Server endpoint:** `https://mcp.coupler.io/mcp`
- **All Coupler.io MCP integrations:** [https://github.com/coupler-io](https://github.com/coupler-io)
