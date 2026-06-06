# 6. Operations Hub — Complete Tutorial

## Table of Contents
1. [Introduction to Operations Hub](#introduction-to-operations-hub)
2. [Data Sync — Complete Guide](#data-sync--complete-guide)
3. [Data Quality — Complete Guide](#data-quality--complete-guide)
4. [Programmable Automation — Complete Guide](#programmable-automation--complete-guide)
5. [Datasets (SQL Querying) — Complete Guide](#datasets-sql-querying--complete-guide)
6. [Calculated Properties — Complete Guide](#calculated-properties--complete-guide)
7. [Data Pipeline — Complete Guide](#data-pipeline--complete-guide)
8. [Operations Automation — Complete Guide](#operations-automation--complete-guide)
9. [Limits That Matter](#limits-that-matter)
10. [Common Gotchas](#common-gotchas)
11. [Use Cases](#use-cases)

---

## Introduction to Operations Hub

Operations Hub is HubSpot's data infrastructure layer. It connects your tech stack, cleans your data, and enables custom automation that spans across hubs. If Marketing Hub is the engine and Sales Hub is the driver, Operations Hub is the wiring that connects everything.

### What You Get by Tier

| Feature | Free | Starter | Pro | Enterprise |
|---------|------|---------|-----|------------|
| Data sync | 1 connection | 5 connections | 10 connections | Unlimited |
| Data quality (dedup) | ✓ (basic) | ✓ | ✓ | ✓ |
| Data quality automation | ✗ | ✓ | ✓ | ✓ |
| Programmable automation | ✗ | ✗ | ✓ | ✓ |
| Datasets (SQL) | ✗ | ✗ | ✓ | ✓ |
| Calculated properties | ✗ | ✗ | ✓ | ✓ |
| Rollup properties | ✗ | ✗ | ✓ | ✓ |
| Data pipeline | ✗ | ✗ | ✗ | ✓ |
| Custom-coded actions | ✗ | ✗ | 10 | Unlimited |
| Webhook actions | ✓ | ✓ | ✓ | ✓ |

### Navigation

- **Settings** > **Data Management** — Properties, custom objects, data model
- **Automation** > **Workflows** — Including custom-coded actions
- **Reports** > **Datasets** — SQL query builder
- **Operations** > **Data Sync** — Sync connections and status
- **Operations** > **Data Quality** — Dedup rules, cleaning, formatting

---

## Data Sync — Complete Guide

Data Sync bi-directionally synchronizes data between HubSpot and other applications.

### What Data Sync Can Do

- **Bi-directional sync**: Changes in HubSpot → connected app and vice versa
- **Field mapping**: Map HubSpot properties to fields in the connected app
- **Conflict resolution**: Rules for when data differs between systems
- **Scheduled sync**: Continuous, or specific intervals
- **Selective sync**: Choose which objects and records to sync
- **History and audit trail**: See what was synced and when

### Supported Connections

| App | Objects Synced | Direction |
|-----|---------------|-----------|
| **Salesforce** | Contacts, Companies, Deals, Tasks, Custom Objects | Bi-directional |
| **Marketo** | Contacts, Companies | Bi-directional |
| **Mailchimp** | Contacts, Lists | Bi-directional |
| **Shopify** | Contacts, Companies, Orders | HubSpot ← Shopify |
| **QuickBooks Online** | Companies, Invoices, Customers | Bi-directional |
| **NetSuite** | Contacts, Companies, Invoices | Bi-directional |
| **Zendesk** | Contacts, Tickets | Bi-directional |
| **Jira** | Issues, Contacts | HubSpot ← Jira |

### Setting Up Data Sync — Step-by-Step

1. **Operations** > **Data Sync** > Create connection
2. Select the app (e.g., Salesforce)
3. **Authenticate**: Log in to the connected app, grant permissions
4. **Choose direction**:
   - **One-way**: HubSpot → App (write only)
   - **One-way**: App → HubSpot (read only)
   - **Bi-directional**: Both directions (requires conflict resolution)
5. **Select objects**: Which CRM objects to sync (Contacts, Companies, Deals, etc.)
6. **Field mapping**: Drag to connect fields:
   ```
   HubSpot Contact.FirstName  →  Salesforce Contact.FirstName
   HubSpot Contact.Email      →  Salesforce Contact.Email
   HubSpot Contact.Phone      →  Salesforce Contact.MobilePhone
   ```
7. **Sync filters**: Which records to include (e.g., only sync contacts with email)
8. **Conflict resolution**: When both systems have changes:
   - **HubSpot wins**: HubSpot value overwrites connected app
   - **Connected app wins**: Connected app value overwrites HubSpot
   - **Most recent wins**: Most recent timestamp value is kept
   - **Manual review**: Flag conflicts for human review
9. **Schedule**: Continuous sync (real-time) or scheduled (daily, hourly)
10. **Activate**

### Sync Monitoring

- **Sync status dashboard**: Last sync time, records synced, errors
- **Sync history**: Detailed log of individual record syncs
- **Error notifications**: Email alerts when sync fails
- **Retry**: Auto-retry failed syncs with backoff
- **Pause/Resume**: Temporarily stop sync without losing configuration

### Data Sync Best Practices

1. **Start small**: Sync one object, verify it works, then add more
2. **Map carefully**: Wrong field mapping can corrupt data in both systems
3. **Avoid circular syncs**: Don't sync the same field in both directions without a clear winner
4. **Monitor for first week**: Check sync logs daily to catch issues early
5. **Clean data first**: Deduplicate before syncing (duplicate records multiply when synced)

---

## Data Quality — Complete Guide

### Deduplication Rules

Find and merge duplicate records:

1. **Operations** > **Data Quality** > **Deduplication**
2. **Create dedup rule**:
   - **Object**: Contacts, Companies, Deals, or Custom Objects
   - **Match criteria**: Email (contacts), Domain (companies), Name (exact or fuzzy)
   - **Fuzzy matching**: Catches "Acme Corp" vs "Acme Corporation" vs "Acme Corp."
   - **Confidence threshold**: High (exact match) vs Low (loose match)
3. **Review duplicates**: Preview potential duplicates before merging
4. **Merge action**: Auto-merge or create review task
5. **Exclusion list**: Exclude specific records from dedup rules

**Deduplication example**:
| Record 1 | Record 2 | Match? |
|----------|----------|--------|
| jane@acme.com | jane@acme.com | ✓ Email exact match (100%) |
| Acme Corp | Acme Corporation | ✓ Fuzzy match (85%) |
| 123 Main St | 123 Main Street | ✓ Fuzzy address match (90%) |

### Data Property Standardization

Auto-format property values:

1. **Operations** > **Data Quality** > **Data Standardization**
2. Create rule:
   - **Phone numbers**: Format "(555) 123-4567" consistently
   - **Names**: Capitalize "JOHN DOE" → "John Doe"
   - **Countries**: "USA", "US", "United States" → "United States"
   - **URLs**: Remove trailing slash, add https://
   - **Emails**: Lowercase all email addresses
3. **Trigger**: Run once (fix existing data) or continuous (fix on entry)

### Data Quality Dashboard

- **Total duplicates found**: Current count and trend
- **Deduplication rate**: % of identified duplicates that were resolved
- **Data completeness**: % of required fields filled in
- **Field consistency**: % of values in standard format
- **Data quality score**: Overall health (0-100)

---

## Programmable Automation — Complete Guide

Programmable automation lets you write custom code that runs as workflow actions. This is Operations Hub's superpower — anything you can code, you can automate.

### Custom-Coded Actions

Custom-coded actions are Node.js or Python functions that run in HubSpot's automation engine.

**Creating a custom-coded action**:

1. **Automation** > **Workflows** > Create workflow
2. Add action: "Custom-coded action"
3. Choose language: JavaScript (Node.js 18) or Python 3.10
4. Write your code:

```javascript
// JavaScript custom-coded action
exports.main = async (event, callback) => {
  // event contains: objectId, portalId, properties, previousProperties
  const { objectId, properties } = event;
  
  // Access the HubSpot API client
  const hubspot = require('@hubspot/api-client');
  const client = new hubspot.Client({
    accessToken: process.env.PRIVATE_APP_TOKEN
  });
  
  // Get contact data
  const contactResponse = await client.crm.contacts.basicApi.getById(
    objectId,
    ['email', 'firstname', 'lastname']
  );
  
  const email = contactResponse.properties.email;
  const domain = email.split('@')[1];
  
  // Call external API for enrichment
  const apiResponse = await fetch(`https://api.clearbit.com/v2/company/find?domain=${domain}`, {
    headers: { 'Authorization': `Bearer ${process.env.CLEARBIT_KEY}` }
  });
  const companyData = await apiResponse.json();
  
  // Update contact properties
  await client.crm.contacts.basicApi.update(objectId, {
    properties: {
      company_name: companyData.name,
      company_industry: companyData.category?.industry,
      company_size: companyData.metrics?.employees?.toString()
    }
  });
  
  callback({ succeeded: true });
};
```

```python
# Python custom-coded action
def main(event):
    # event contains: objectId, portalId, properties
    object_id = event['objectId']
    properties = event['properties']
    
    # HubSpot API client
    import hubspot
    client = hubspot.Client.create(access_token=os.environ['PRIVATE_APP_TOKEN'])
    
    # Process the contact
    email = properties.get('email')
    if email and '@' in email:
        domain = email.split('@')[1]
        
        # Update a custom property
        api_response = client.crm.contacts.basic_api.update(
            object_id,
            {
                'properties': {
                    'email_domain': domain
                }
            }
        )
    
    return {'succeeded': True}
```

### Available in Custom-Coded Actions

- **Access to HubSpot API**: Full CRUD on contacts, companies, deals, tickets, custom objects
- **HTTP requests**: Call external APIs (within 20-second timeout)
- **Environment variables**: Store API keys, secrets securely
- **Logging**: `console.log()` output appears in workflow logs
- **Error handling**: `try/catch` blocks; failed actions can retry

### Limitations

- **Timeout**: 20 seconds maximum execution
- **Memory**: 256 MB
- **No file system**: Can't read/write local files
- **No npm/pip install**: Only standard library + `@hubspot/api-client` (JS) or `hubspot-api-client` (Python)
- **No external network to private subnets**: Can only access public internet endpoints
- **No state persistence**: Each invocation is stateless

### Webhook Actions

Call external systems without writing code:

1. In workflow builder, add action: "Trigger webhook"
2. Set URL: `https://your-system.com/webhook`
3. Choose method: POST, PUT, GET, PATCH
4. Set headers: API keys, content type
5. Define payload: Map HubSpot properties to JSON fields
6. Handle response: Parse response to update properties

**Example webhook payload**:
```json
{
  "contact": {
    "email": "{{ contact.email }}",
    "firstname": "{{ contact.firstname }}",
    "lastname": "{{ contact.lastname }}"
  },
  "deal": {
    "name": "{{ deal.dealname }}",
    "amount": {{ deal.amount }}
  }
}
```

---

## Datasets (SQL Querying) — Complete Guide

Datasets let you query HubSpot data using SQL. No more exporting to Excel just to join data across objects.

### What Datasets Can Do

- Write SQL SELECT queries against CRM data
- Join across objects (contacts + deals + companies)
- Aggregate (SUM, COUNT, AVG, MIN, MAX)
- Filter, group, sort
- Create custom reports from query results
- Schedule exports

### SQL Syntax Supported

```sql
-- Basic SELECT
SELECT 
  c.email,
  c.firstname,
  c.createdate,
  d.dealname,
  d.amount,
  d.dealstage
FROM contacts c
LEFT JOIN deals d ON c.id = d.associated_contact_id
WHERE d.createdate >= '2025-01-01'
  AND d.amount > 1000
ORDER BY d.amount DESC;

-- Aggregation
SELECT 
  company,
  COUNT(*) as contact_count,
  SUM(d.amount) as total_pipeline,
  AVG(d.amount) as avg_deal_size
FROM contacts c
LEFT JOIN deals d ON c.id = d.associated_contact_id
GROUP BY company
HAVING COUNT(*) > 5
ORDER BY total_pipeline DESC;

-- Date functions
SELECT 
  DATE_TRUNC('month', d.createdate) as month,
  COUNT(*) as deals_created,
  SUM(CASE WHEN d.dealstage = 'closedwon' THEN 1 ELSE 0 END) as deals_won
FROM deals d
GROUP BY DATE_TRUNC('month', d.createdate)
ORDER BY month;
```

### Creating a Dataset

1. **Reports** > **Datasets** > Create dataset
2. Write SQL query
3. Click "Run" to test
4. **Save** as a dataset
5. Use dataset in:
   - Custom report builder (as data source)
   - Dashboard (as chart/table)
   - Scheduled export (email CSV)

### Joins Available

| Object | Can Join With |
|--------|-------------|
| Contacts | Companies, Deals, Tickets, Products, Custom Objects |
| Companies | Contacts, Deals, Tickets, Products, Custom Objects |
| Deals | Contacts, Companies, Products, Line Items, Quote |
| Tickets | Contacts, Companies |
| Custom Objects | Any associated object |

### Scheduled Exports

1. Create a dataset
2. Click "Schedule export"
3. Set frequency: Daily, Weekly, Monthly
4. Set delivery: Email CSV to specific users
5. Optionally: Send to external storage (Google Sheets, Box, Dropbox via webhook)

### Dataset Use Cases

- **Pipeline velocity**: Average days in each deal stage per rep
- **Account health**: Deals + tickets + contact count per company
- **Churn analysis**: Customers who haven't purchased in 12 months
- **Lead source ROI**: Revenue by first-touch source
- **Sales activity**: Emails, calls, meetings per rep per week

---

## Calculated Properties — Complete Guide

Calculated properties compute values from other properties using formulas. Rollup properties aggregate data from associated records.

### Formula Syntax

**Arithmetic**:
```
commission = deal_amount * 0.10
total_price = unit_price * quantity
discounted_price = IF(coupon_applied, price * 0.8, price)
```

**Conditional**:
```
priority_score = IF(
  AND(deal_amount > 10000, lifecycle_stage = "opportunity"),
  100,
  IF(lifecycle_stage = "opportunity", 50, 0)
)
```

**Date calculations**:
```
days_since_last_activity = DATE_DIFF(last_activity_date, TODAY(), "day")
contract_end_soon = DATE_DIFF(TODAY(), contract_end_date, "day") < 30
```

**Text operations**:
```
full_name = firstname + " " + lastname
email_domain = SPLIT(email, "@")[1]
```

### Available Functions

| Function | Description | Example |
|----------|-------------|---------|
| IF(cond, t, f) | Conditional | IF(score > 50, "Hot", "Cold") |
| AND(a, b) | Logical AND | AND(is_customer, has_deal) |
| OR(a, b) | Logical OR | OR(is_prospect, is_lead) |
| NOT(a) | Logical NOT | NOT(is_deleted) |
| DATE_DIFF(d1, d2, unit) | Date difference in days | DATE_DIFF(createdate, TODAY(), "day") |
| TODAY() | Current date | TODAY() |
| NOW() | Current datetime | NOW() |
| CONTAINS(text, substr) | Text contains check | CONTAINS(industry, "Tech") |
| LENGTH(text) | String length | LENGTH(firstname) |
| ROUND(num, places) | Round to decimal | ROUND(amount, 2) |
| CONCAT(a, b) | Concatenate | CONCAT(city, ", ", state) |
| SPLIT(text, delim) | Split string | SPLIT(email, "@")[1] |
| UPPER(text) | Uppercase | UPPER(firstname) |
| LOWER(text) | Lowercase | LOWER(email) |

### Rollup Properties

Rollups aggregate values from associated records:

**Contact → Deals**:
```
SUM(associated_deals, amount)       — Total deal value
COUNT(associated_deals)              — Number of deals
AVG(associated_deals, amount)        — Average deal size
MAX(associated_deals, amount)        — Largest deal
MIN(associated_deals, amount)        — Smallest deal
LATEST(associated_deals, closedate)  — Most recent close
EARLIEST(associated_deals, createdate) — First deal date
```

**Company → Contacts**:
```
COUNT(associated_contacts)           — Number of employees/contacts
COUNT(associated_tickets)            — Open support tickets
COUNT(associated_deals)              — Active deals
SUM(associated_deals, amount)        — Total pipeline value
```

**Deal → Line Items**:
```
SUM(associated_line_items, quantity)   — Total units
SUM(associated_line_items, price)      — Total product value
```

**Use case example**: On a company record, show "Total Revenue" as a rollup of all closed-won deal amounts. This gives account managers instant visibility into account value.

---

## Data Pipeline — Complete Guide

Data Pipeline (Enterprise) syncs data from HubSpot to external data warehouses.

### Supported Destinations

- Snowflake
- Google BigQuery
- Amazon Redshift
- Microsoft Azure Synapse

### How It Works

1. Configure destination (Snowflake, BigQuery, Redshift, Synapse)
2. Select objects to sync (Contacts, Companies, Deals, Tickets, Custom Objects)
3. Choose sync frequency (every 1, 6, 12, or 24 hours)
4. Data is exported in raw or transformed format
5. Historical snapshots are maintained
6. Use your BI tool (Tableau, Looker, Power BI) to analyze HubSpot data alongside other data sources

### Data Pipeline vs Operations Hub Sync

| Feature | Operations Hub Sync | Data Pipeline |
|---------|-------------------|---------------|
| Direction | Bi-directional | HubSpot → Warehouse |
| Destination | Connected apps (Salesforce, Shopify) | Data warehouses (Snowflake, BigQuery) |
| Purpose | Keep CRMs in sync | Analytics and BI |
| Use case | Day-to-day operations | Reporting and analysis |

---

## Operations Automation — Complete Guide

Operations Hub enables automation patterns that span multiple systems and hubs.

### Cross-Object Workflow Patterns

**Pattern 1: Data Quality on Entry**
```
Trigger: New contact created
  → Standardize phone number format
  → Look up company by email domain
  → Auto-enrich with Breeze Intelligence
  → Check for duplicates → Flag if found
```

**Pattern 2: Account-Based Alerting**
```
Trigger: Company's number of open tickets > 5
  → Slack notification to account manager
  → Create high-priority task for CS team
  → Update company health score to "At Risk"
```

**Pattern 3: Lead-to-Account Matching**
```
Trigger: Contact created with company name
  → Search for existing company by name
  → If found: associate contact to company
  → If not found: create company, enrich with Breeze
```

**Pattern 4: Revenue Recognition**
```
Trigger: Deal stage becomes "Closed Won"
  → Create invoice in QuickBooks
  → Calculate commission using calculated property
  → Create commission record in custom object
  → Notify finance team via webhook
```

### Custom-Coded Action Examples

**Real-time Slack alerting**:
```javascript
exports.main = async (event, callback) => {
  const { properties } = event;
  
  await fetch(process.env.SLACK_WEBHOOK_URL, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      text: `🚨 Urgent ticket created: ${properties.ticket_name}\n` +
            `Priority: ${properties.ticket_priority}\n` +
            `Contact: ${properties.email}`,
      channel: '#support-urgent'
    })
  });
  
  callback({ succeeded: true });
};
```

**External data enrichment**:
```javascript
exports.main = async (event, callback) => {
  const { objectId } = event;
  
  const hubspot = require('@hubspot/api-client');
  const client = new hubspot.Client({ 
    accessToken: process.env.PRIVATE_APP_TOKEN 
  });
  
  const contact = await client.crm.contacts.basicApi.getById(objectId, ['email']);
  const domain = contact.properties.email.split('@')[1];
  
  // Enrich from Clearbit
  const response = await fetch(`https://company.clearbit.com/v2/companies/find?domain=${domain}`, {
    headers: { 'Authorization': `Bearer ${process.env.CLEARBIT_KEY}` }
  });
  const data = await response.json();
  
  if (data.name) {
    await client.crm.contacts.basicApi.update(objectId, {
      properties: {
        company_name: data.name,
        company_industry: data.category?.industry || '',
        company_revenue: data.metrics?.annualRevenue?.toString() || '',
        company_employees: data.metrics?.employees?.toString() || ''
      }
    });
  }
  
  callback({ succeeded: true });
};
```

---

## Limits That Matter

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Data sync connections | 1 | 5 | 10 | Unlimited |
| Sync frequency | Daily | Every 4h | Every 1h | Real-time |
| Field mappings per sync | 10 | 25 | 50 | 200 |
| Custom-coded actions | 0 | 0 | 10 | Unlimited |
| Custom-coded action timeout | — | — | 20s | 20s |
| Datasets (SQL) | 0 | 0 | 50 | 200 |
| Dataset query timeout | — | — | 60s | 120s |
| Calculated properties | 0 | 0 | 200 | 1,000 |
| Rollup properties | 0 | 0 | 200 | 1,000 |
| Data warehouse destinations | 0 | 0 | 0 | 5 |
| Webhook actions in workflows | ✓ | ✓ | ✓ | ✓ |
| Data quality rules | 3 | 10 | 50 | Unlimited |

---

## Common Gotchas

### 1. Data Sync Conflicts
When running bi-directional sync, conflicts are inevitable. Always set clear conflict resolution rules. "Most recent wins" is generally safest but can lose data if clocks are off between systems.

### 2. Custom-Coded Action Debugging
There's no step-through debugger. The only debugging tool is `console.log()` output, visible in the workflow action history. Test thoroughly in a sandbox first.

### 3. SQL Dataset Performance
Complex joins across large datasets (>1M records) can timeout. Use WHERE clauses to limit data, and avoid joining more than 3-4 objects in a single query.

### 4. Calculated Property Dependency
If a calculated property references another calculated property (chained calculations), changes to the source property may not cascade immediately. Keep calculation chains shallow (1-2 levels max).

### 5. Rollup Property Performance
Rollups over many associated records (>1,000) can slow down. When viewing a company with 5,000 contacts and 2,000 deals, rollup calculations may take seconds to compute.

### 6. Webhook Payload Limits
Webhook payloads are limited to 1MB. If you're sending large payloads (many properties, long text fields), they may be truncated.

### 7. Sync Pause Resets
If you pause data sync for more than 30 days, some connections may need to be re-authenticated when resumed.

### 8. Environment Variables
Custom-coded action environment variables are stored at the portal level. Be careful not to commit sensitive values (API keys, tokens) to version control.