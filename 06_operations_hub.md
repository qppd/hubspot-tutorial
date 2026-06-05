# 6. Operations Hub

## What It Does
HubSpot Operations Hub connects HubSpot to your other business tools, syncs data bidirectionally, cleans and standardizes your CRM data, automates data management workflows, and provides programmable automation with custom-coded actions. It's the engine that keeps your revenue data accurate, consistent, and actionable across your entire tech stack.

## Key Features

### Data Sync
- **Bidirectional sync**: synchronize data between HubSpot and connected apps in real time or on schedule
- **Supported connectors**: Salesforce, Microsoft Dynamics 365, Mailchimp, Shopify, WooCommerce, QuickBooks Online, Xero, Zendesk, ServiceNow, Stripe, Google Sheets, Airtable, and 100+ others via custom + iPaaS connectors
- **Sync directions**: one-way or two-way, per-field configuration
- **Field mapping**: drag-and-drop mapping UI with transformation rules (picklist mapping, string formatting, number rounding)
- **Record matching**: match by email, domain, custom ID, or combination of fields
- **Conflict resolution rules**: HubSpot wins, connected app wins, most recently updated wins, or manual review
- **Sync history**: audit log of synced records, errors, and field conflicts
- **Sync monitoring**: dashboard showing sync status, error rate, records synced per connector
- **Re-sync**: full re-sync without duplicating records
- **Custom object sync**: sync custom objects between systems (Enterprise)
- **Sync trigger**: real-time (webhook-based) or scheduled intervals (every 5, 15, 30 min, hourly, daily)
- **HubSpot → Salesforce, Shopify, QuickBooks**: field-level mapping with conflict resolution

### Data Quality Automation
- **Data quality automation**: rules that auto-format, clean, and standardize data
- **Rule types**:
  - **Format**: phone numbers, URLs, email addresses, date formats, currency
  - **Standardize**: title case, capitalize, lowercase, remove extra spaces, strip HTML
  - **Enrich**: append firmographic data from Breeze Intelligence (industry, revenue range, employee count, technographics)
  - **Validate**: check email deliverability, phone number format, domain validity
  - **Custom**: write your own data transformation rules via the rule builder
- **Rule triggers**: on record create, on import, on property update, on schedule (daily/weekly)
- **Data quality dashboard**: score your CRM health — completeness, formatting errors, duplicate rate
- **Duplicate detection**: merge suggestions for contacts, companies, deals, tickets
- **Duplicate prevention**: block duplicates at import and creation time
- **Data quality score**: percentage of records meeting your quality criteria (dashboard trends over time)
- **Field completeness tracking**: % of required fields populated per object with drill-down
- **Error reporting**: log of failed data quality actions with retry option

### Breeze Intelligence Data Enrichment
- **Company enrichment**: auto-populate industry, revenue range, employee count, location, phone, and domain from 260M+ company profiles
- **Contact enrichment**: append job title, seniority, department, and work email from Breeze's B2B contact database
- **Technographic data**: see which technologies a company uses (CRM, ERP, marketing tools, analytics)
- **Intent signals**: identify accounts actively researching your product category
- **Behavioral scoring**: merge intent signals with CRM data for prioritization
- **Enrichment triggers**: on create, on import, or on schedule as a data quality rule
- **Usage**: available as a paid add-on; directly accessible through data quality automation rules

### Programmable Automation (Custom-Coded Workflows)
- **Custom-coded actions**: write your own workflow actions in Node.js or Python
- **Code action triggers**: contact-based, company-based, deal-based, ticket-based, custom object-based
- **Code execution**: serverless environment (10s timeout, 10MB response limit)
- **Input/output schemas**: define typed schemas for what your code receives and returns
- **Secrets management**: store API keys, tokens securely (encrypted at rest, not readable after save)
- **External API calls**: make HTTP/HTTPS requests to any third-party API
- **Error handling**: retry logic, error logging to workflow history, fallback actions
- **Testing**: inline code tester with sample input data
- **Versioning**: save and rollback code action versions
- **Custom-coded cards**: display custom UI cards on contact/company/deal records (Enterprise) — React or plain JS

### Datasets, Reporting & SQL
- **Custom datasets**: combine HubSpot CRM data with external data sources (CSV uploads, API data)
- **SQL query**: write `SELECT`, `JOIN`, `WHERE`, `GROUP BY` against datasets for custom reports
- **Dataset types**: HubSpot objects, custom objects, imported CSV/Excel, programmatic (API)
- **Dataset scheduling**: auto-refresh on schedule (hourly, daily, weekly)
- **Dataset joining**: join HubSpot objects to external data tables (e.g., join contacts to imported sales territory mapping)
- **Reporting from datasets**: build custom reports on top of datasets using the Custom Report Builder
- **Calculated properties**: create formula-based properties (e.g., "Days Since Last Contact", "Deal Velocity Score")
- **Rollup properties**: aggregate data from related objects (e.g., sum of all deal amounts for a company, count of open tickets per contact)
- **Text analytics**: sentiment analysis, keyword extraction, language detection on text properties

### Pre-built Connectors (Data Sync Hub)

| Connector Type | Examples |
|---|---|
| CRM | Salesforce, Microsoft Dynamics 365 |
| E-commerce | Shopify, WooCommerce, BigCommerce |
| Finance | QuickBooks Online, Xero, Stripe |
| Support | Zendesk, ServiceNow, Freshdesk |
| Marketing | Mailchimp, Constant Contact, Eventbrite |
| Productivity | Google Sheets, Airtable, Asana |
| Custom | Webhook triggers, REST API, Zapier, Make |

### Data Management
- **Import**: CSV/Excel import with field mapping, deduplication, and automation triggers
- **Export**: export any object, list, or report to CSV
- **Bulk operations**: update, delete, or reassign records in bulk
- **Object management**: create/edit custom objects, properties, associations
- **Property management**: create, edit, archive, and organize properties
- **Record merging**: merge duplicate contacts, companies, deals, tickets
- **Trash/recycle bin**: recover deleted records (30 days for paid tiers)
- **Audit log**: track property changes, user actions, API calls (available in Settings)

## Step-by-Step: Setting Up Data Sync with Salesforce

1. Settings > Integrations > Data Sync
2. Click "Connect app" → select Salesforce
3. Authenticate with Salesforce OAuth
4. Choose sync direction per object:
   - Contacts: Bidirectional
   - Companies: Salesforce → HubSpot only
   - Deals: HubSpot → Salesforce only
5. Configure field mappings for each object:
   - Drag to match HubSpot fields to Salesforce fields
   - Set transformation rules (e.g., Salesforce picklist → HubSpot dropdown)
6. Set conflict resolution:
   - "Most recently updated wins" for contacts
   - "HubSpot wins" for companies
7. Set sync frequency: Real-time or every 15 minutes
8. Initial sync: triggers full sync for existing records
9. Monitor: Dashboard shows sync status, errors, records synced

## Step-by-Step: Creating a Data Quality Rule

1. Settings > Data Management > Data Quality
2. Click "Create rule"
3. Choose object: Contact, Company, Deal, Ticket, Custom Object
4. Choose rule type:
   - **Format phone**: +63-xxx-xxx-xxxx format
   - **Format URL**: ensure https:// prefix
   - **Standardize name**: Capitalize first letter of each word
   - **Enrich with Breeze**: Append industry, revenue range from Breeze Intelligence
   - **Validate email**: mark invalid emails
5. Set trigger:
   - When record is created
   - When property changes
   - On import
   - On schedule (daily/weekly)
6. Configure: e.g., "Format phone number on create"
7. Save and activate
8. View impact in Data Quality Dashboard (score improvement over time)

## Step-by-Step: Creating a Custom-Coded Workflow Action

1. Automation > Workflows > Actions library > Create custom-coded action
2. Name the action (e.g., "Create Invoice in Stripe")
3. Choose runtime: Node.js (default) or Python
4. Define input schema:
   ```json
   {
     "type": "object",
     "properties": {
       "deal_amount": { "type": "number" },
       "contact_email": { "type": "string" }
     },
     "required": ["deal_amount", "contact_email"]
   }
   ```
5. Define output schema:
   ```json
   {
     "type": "object",
     "properties": {
       "invoice_id": { "type": "string" },
       "status": { "type": "string" }
     }
   }
   ```
6. Write code (Node.js example):
   ```javascript
   exports.main = async (event, callback) => {
     const { deal_amount, contact_email } = event.inputFields;
     const response = await fetch('https://api.stripe.com/v1/invoices', {
       method: 'POST',
       headers: {
         'Authorization': `Bearer ${event.secrets.STRIPE_SECRET_KEY}`,
         'Content-Type': 'application/x-www-form-urlencoded',
       },
       body: `customer_email=${contact_email}&amount=${deal_amount * 100}`
     });
     const data = await response.json();
     callback({ outputFields: { invoice_id: data.id, status: data.status } });
   };
   ```
7. Configure secrets: Add `STRIPE_SECRET_KEY` encrypted storage
8. Test with sample data
9. Save → Use in workflow as an action step

## Limits That Matter

| Resource | Pro | Enterprise |
|----------|-----|------------|
| Data sync objects | 100k/month | 500k/month |
| Data sync connectors | 5 | Unlimited |
| Data quality rules | 50 | 200 |
| Custom-coded actions | 10 | 200 |
| Custom-coded action executions | 100k/month | 1M/month |
| Action timeout | 10 seconds | 10 seconds |
| Action response size | 10MB | 10MB |
| Datasets | 5 (10k rows each) | Unlimited (100k rows each) |
| SQL queries per minute | 20 | 50 |
| Calculated properties | 500 | 5,000 |
| Rollup properties | 20 | 200 |
| API rate limits | 100 req/10s per app | 200 req/10s per app |
| Sync frequency | Scheduled | Real-time + Scheduled |

## Use Cases

- Keep HubSpot and Salesforce in sync without manual data entry
- Clean and standardize phone numbers, emails, and names automatically
- Build custom integrations with any REST API using code actions
- Enrich company/contact records with Breeze Intelligence firmographics and intent signals
- Calculate rollups (e.g., total revenue per account across all deals)
- Create datasets combining HubSpot data with external spreadsheets
- Automate data quality checks on every new record import
- Build custom cards on CRM records displaying real-time data from external systems

## Common Gotchas

- Data sync conflict resolution settings are per-object, not per-field — apply carefully
- Custom-coded actions have no external package manager (npm) — code must be self-contained
- Secrets in code actions cannot be read back after saving (store them externally)
- Deleting a rollup property doesn't recalculate until next sync cycle
- Data quality rules run on trigger — existing records aren't retroactively cleaned (run a manual bulk fix)
- Datasets imported via CSV are static snapshots until next scheduled refresh
- Real-time sync (Enterprise) creates more API calls → watch rate limits
- Rollup properties over large datasets can slow down page load
- Custom objects synced via Data Sync need identical field definitions on both ends
- Data Sync with Salesforce may require field-level security permissions in SF
- Breeze Intelligence enrichment is a separate paid add-on — not included in base Operations Hub pricing