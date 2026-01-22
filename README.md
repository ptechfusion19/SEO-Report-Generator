# SEO Reports Automation

Automated SEO reporting workflow that generates comprehensive SEO analysis reports using DataForSEO API and AI.

## Endpoints

### 1. Onboarding Report
**Path:** `/OnboardingReport`  
**Method:** `POST`

Generates an initial SEO audit report for a website.

**Parameters:**
- `target_url` (required) - Website URL to analyze
- `email` (required) - Email address to send report
- `location` (optional) - Location for analysis (default: "United Kingdom")
- `report_type` (optional) - Report type (default: "onboarding")
- `report_audience` (optional) - "client" or "internal" (default: "client")

**Example:**
```bash
curl -X POST "https://n8n.programmx.com/webhook/OnboardingReport" \
  -H "Content-Type: application/json" \
  -d '{
    "target_url": "https://www.example.com",
    "email": "user@example.com",
    "location": "United Kingdom",
    "report_type": "onboarding",
    "report_audience": "client"
  }'
```

### 2. Progress Report
**Path:** `/ProgressReport`  
**Method:** `POST`

Generates a performance report comparing current metrics with historical data.

**Parameters:**
- `target_url` (required) - Website URL to analyze
- `email` (required) - Email address to send report
- `location` (optional) - Location for analysis (default: "United Kingdom")
- `report_type` (optional) - Report type (default: "progress")
- `report_audience` (optional) - "client" or "internal" (default: "client")
- `date_from` (optional) - Start date (YYYY-MM-DD, default: 30 days ago)
- `date_to` (optional) - End date (YYYY-MM-DD, default: today)

**Example:**
```bash
curl -X POST "https://n8n.programmx.com/webhook/ProgressReport" \
  -H "Content-Type: application/json" \
  -d '{
    "target_url": "https://www.example.com",
    "email": "user@example.com",
    "location": "United Kingdom",
    "report_type": "progress",
    "report_audience": "client",
    "date_from": "2025-10-01",
    "date_to": "2026-01-07"
  }'
```

## What It Does

1. Collects SEO data from DataForSEO API:
   - Domain rank overview
   - Ranked keywords
   - Backlinks summary
   - On-page technical analysis

2. Generates AI-powered report using GPT-4.1 mini:
   - Client-facing: Optimistic, opportunity-focused
   - Internal: Honest, detailed technical analysis

3. Saves report to Google Drive and emails recipient

## Report Types

- **Client Reports** (`report_audience: "client"`): Positive, opportunity-focused reports
- **Internal Reports** (`report_audience: "internal"`): Detailed technical audits with all issues

## Processing Time

- OnPage analysis: ~5 minutes wait time
- Total workflow: ~5-10 minutes

