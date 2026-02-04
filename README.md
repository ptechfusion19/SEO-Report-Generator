## SEO Reports Automation – Website Health, Strategy & Performance

**Note:** This workflow was created for Wajahat bhai and PM Sehar.

### Overview

This project automates SEO reporting using n8n, DataForSEO, OpenAI (`gpt-4.1-mini`), Google Drive, and email. It generates two main types of reports for any target website over a selected date range.

### Workflows

- **Website Health & SEO Strategy Report**
  - Validates input (target URL, email, location, date range).
  - Calls DataForSEO OnPage API to crawl up to 30 pages and collect technical SEO metrics (on-page score, broken links, duplicates, indexability checks, etc.).
  - Builds a structured JSON summary of technical health and crawl status.
  - Sends this data to an LLM prompt to generate a human-readable Website Health & SEO Strategy report.
  - Saves the report as a Markdown file in Google Drive and emails a link / copy to the recipient.

- **SEO Performance Report**
  - Validates input (target URL, email, location, audience type, date range).
  - Calls DataForSEO Labs APIs:
    - Historical Rank Overview (keyword positions, traffic value over time).
    - Ranked Keywords (top-performing and opportunity keywords).
    - Backlinks History (backlink and referring domain growth).
  - Aggregates all datasets into a single JSON object (domain rank, keywords, backlinks, optional previous report).
  - Uses an LLM prompt to generate a performance/progress report (client-focused tone by default).
  - Saves the Markdown report to Google Drive and emails it to the provided address.

### Web Interfaces

- **Website Health & SEO Strategy Report Interface**
  - Single-page HTML form (`Website Health and Strategy Report Interface.html`).
  - Inputs: target URL, email, location (default: United Kingdom), date range (last 30 days prefilled).
  - On submit, POSTs JSON to the `https://n8n.programmx.com/webhook/Website-Health-and-SEO-Strategy-Report` webhook.
  - Shows loading state, success message (report will arrive in 5–10 minutes), and error handling.

- **SEO Performance Report Interface**
  - Single-page HTML form (`performance Report Interface.html`).
  - Inputs: target URL, email, location (default: United Kingdom), report audience (client/internal), date range (last 30 days prefilled).
  - On submit, POSTs JSON to the `https://n8n.programmx.com/webhook/SEO-Performance-Report` webhook.
  - Includes loading indicator, validation for required fields and date range, and success/error messages.

### Tech & Dependencies (Conceptual)

- **n8n workflow file**: `Website-Health-SEO-Strategy-Report and Performance-Report.json` (DataForSEO HTTP nodes, Code nodes, Merge nodes, Langchain LLM chain, Google Drive, and email nodes).
- **APIs & services**:
  - DataForSEO OnPage, Labs (Historical Rank Overview, Ranked Keywords, Backlinks History).
  - OpenAI `gpt-4.1-mini` for report generation.
  - Google Drive for Markdown report storage.
  - Email delivery from n8n for sending report links/content.


