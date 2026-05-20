# 6. Operations Hub

## What It Does
HubSpot Operations Hub connects HubSpot to your other business tools, syncs data bidirectionally, cleans and standardizes your CRM data, automates data management workflows, and provides programmable automation with custom-coded actions.

## Key Features

### Data Sync
- **Bidirectional sync**: synchronize data between HubSpot and connected apps in real time or on schedule
- **Supported connectors**: Salesforce, Microsoft Dynamics 365, Mailchimp, Shopify, QuickBooks, Zendesk, ServiceNow, Stripe, Google Sheets, and 100+ others via custom + IPaaS
- **Sync directions**: one-way or two-way, per field configuration
- **Field mapping**: map fields between systems (drag-and-drop mapping UI)
- **Record matching**: match by email, domain, custom ID, or combination
- **Conflict resolution rules**: HubSpot wins, connected app wins, most recently updated wins
- **Sync history**: audit log of synced records, errors, field conflicts
- **Sync monitoring**: dashboard showing sync status, error rate, records synced
- **Re-sync**: full re-sync without duplicate creation
- **Custom object sync**: sync custom objects between systems (Enterprise)
- **Sync trigger**: real-time (webhook-based) or scheduled intervals (every 5, 15, 30 min, hourly, daily)

### Data Quality
- **Data quality automation**: rules that auto-format, clean, and standardize data
- **Rule types**:
  - **Format**: phone numbers, URLs, email addresses, date formats
  - **Standardize**: title case, capitalize, lowercase, remove extra spaces
  - **Enrich**: append data from HubSpot’s company firmographic database
  - **Validate**: check email deliverability, phone number format
  - **Custom**: write your own data transformation rules
- **Rule triggers**: on create, on import, on property update, on schedule
- **Data quality dashboard**: score your CRM health (completeness, formatting errors, duplicates)
- **Duplicate detection**: merge suggestions for contacts, companies, deals, tickets
- **Duplicate prevention**: prevent duplicates at import/creation
- **Data quality score**: percentage of records meeting your quality criteria
- **Field completeness tracking**: % of required fields populated per object
- **Error reporting**: log of failed data quality actions

### Programmable Automation (Custom-Coded Workflows)
- **Custom-coded actions**: write your own workflow actions in Node.js or Python
- **Code action triggers**: contact-based, company-based, deal-based, ticket-based, custom object-based
- **Code execution**: serverless environment (10s timeout, 10MB response limit)
- **Input/output schemas**: define what data your code receives and sends
- **Secrets**: store API keys, tokens securely (encrypted at rest)
- **External API calls**: make HTTP requests to any third-party API
- **Error handling**: retry logic, error logging, fallback actions
- **Testing**: inline code tester with sample data
- **Versioning**: save and rollback code action versions
- **Custom-coded cards**: display custom UI cards on contact/company/deal records (Enterprise)

### Datasets & Reporting
- **Custom datasets**: combine HubSpot data with external data sources
- **SQL query**: write SQL against datasets for custom reporting
- **Dataset types**: HubSpot objects, custom objects, imported data (CSV), programmatic (API)
- **Dataset scheduling**: auto-refresh on schedule
- **Dataset joining**: join HubSpot objects to external data tables
- **Reporting from datasets**: build custom reports on top of datasets
- **Calculated properties**: create formula-based properties (e.g., "Days Since Last Contact")
- **Rollup properties**: aggregate data from related objects (e.g., sum of all deal amounts for a company)
- **Text analytics**: sentiment analysis, keyword extraction, language detection on text properties

### Data Sync Hub (Pre-built Connectors)
| Connector Type | Examples |
|---|---|
| CRM | Salesforce, Dynamics 365 |
| E-commerce | Shopify, WooCommerce, BigCommerce |
| Finance | QuickBooks, Xero, Stripe |
| Support | Zendesk, ServiceNow, Freshdesk |
| Marketing | Mailchimp, Constant Contact |
| Productivity | Google Sheets, Airtable |
| Custom | Webhook triggers, REST API, IPaaS (Zapier, Make) |

### Data Management
- **Import**: CSV/Excel import with field mapping, dedup, automation
- **Export**: export any object, list, or report to CSV
- **Bulk operations**: update, delete, or reassign records in bulk
- **Object management**: create/edit custom objects, properties, associations
- **Property management**: create, edit, archive, and organize properties
- **Record merging**: merge duplicate contacts, companies, deals, tickets
- **Trash/recycle bin**: recover deleted records (30 days for paid tiers)
- **Audit log**: track property changes, user actions, API calls

## Step-by-Step: Setting Up Data Sync with Salesforce

1. Settings > Integrations > Data Sync
2. Click "Connect app" → select Salesforce
3. Authenticate with Salesforce OAuth
4. Choose sync direction per object:
   - Contacts: Bidirectional
   - Companies: Salesforce to HubSpot only
   - Deals: HubSpot to Salesforce only
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
   - **Enrich company**: Append industry, revenue range from HubSpot database
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

- Data sync objects: 100k/month (Pro), 500k/month (Enterprise)
- Data sync connectors: Pro (5), Enterprise (unlimited)
- Data quality rules: 50 (Pro), 200 (Enterprise)
- Custom-coded actions: 10 (Pro), 200 (Enterprise)
- Custom-coded action execution: 100k/month (Pro), 1M/month (Enterprise)
- Action timeout: 10 seconds
- Action response size: 10MB
- Datasets: Pro (5 datasets, 10k rows each), Enterprise (unlimited, up to 100k rows)
- SQL queries per minute: 20
- Calculated properties: 500 (Pro), 5,000 (Enterprise)
- Rollup properties: 20 (Pro), 200 (Enterprise)
- API rate limits: 100 requests per 10 seconds per app
- Sync frequency: Real-time (Enterprise only), Scheduled (Pro)

## Use Cases

- Keep HubSpot and Salesforce in sync without manual data entry
- Clean and standardize phone numbers, emails, and names automatically
- Build custom integrations with any REST API using code actions
- Enrich company records with industry, revenue, and technographic data
- Calculate rollups (e.g., total revenue per account across all deals)
- Create datasets combining HubSpot data with external spreadsheets
- Automate data quality checks on every new record import
- Build custom cards on CRM records displaying real-time data from external systems

## Common Gotchas

- Data sync conflict resolution settings are per-object, not per-field — apply carefully
- Custom-coded actions have no external package manager (npm) — code must be self-contained
- Secrets in code actions cannot be read back after saving (write them down)
- Deleting a rollup property doesn't recalculate until next sync cycle
- Data quality rules run on trigger — existing records aren't retroactively cleaned (run a manual bulk fix)
- Datasets imported via CSV are static snapshots until next scheduled refresh
- Real-time sync (Enterprise) creates more API calls → watch rate limits
- Rollup properties over large datasets can slow down page load
- Custom objects synced via Data Sync need identical field definitions on both ends
- Data Sync with Salesforce may require field-level security permissions in SF