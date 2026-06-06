# 1. CRM Foundation — Complete Tutorial

## Table of Contents
1. [Introduction to the CRM](#introduction-to-the-crm)
2. [Contacts — Complete Guide](#contacts--complete-guide)
3. [Companies — Complete Guide](#companies--complete-guide)
4. [Deals — Complete Guide](#deals--complete-guide)
5. [Tickets — Complete Guide](#tickets--complete-guide)
6. [Properties — Complete Guide](#properties--complete-guide)
7. [Pipelines — Complete Guide](#pipelines--complete-guide)
8. [Lists — Complete Guide](#lists--complete-guide)
9. [Activities — Complete Guide](#activities--complete-guide)
10. [Associations — Complete Guide](#associations--complete-guide)
11. [CRM Reporting](#crm-reporting)
12. [Limits That Matter](#limits-that-matter)
13. [Common Gotchas](#common-gotchas)
14. [Use Cases](#use-cases)

---

## Introduction to the CRM

The HubSpot CRM is the central nervous system of the entire platform. Every hub — Marketing, Sales, Service, Content, Operations, Commerce — reads from and writes to the same CRM database. This unified data model is HubSpot's biggest differentiator from competitors.

### What You Get with the Free CRM

The free tier of HubSpot CRM is surprisingly generous. It's not a trial — it's a permanently free product that thousands of businesses use as their primary CRM:

**Free CRM Features**:
- **Unlimited contacts, companies, deals, and tasks** (with storage limits: 1M contacts, 100K companies)
- **Up to 10 custom objects** with 10,000 records each
- **1 pipeline for deals** with up to 10 stages
- **1 pipeline for tickets**
- **Email tracking** (200 tracked emails/day): you get open and click notifications
- **Email templates**: create and save up to 5 email templates
- **Meeting scheduling**: shareable meeting link synced with Google/Outlook
- **Live chat**: website chat widget
- **Form builder**: up to 1,000 forms
- **Landing pages**: up to 20 landing pages with HubSpot subdomain
- **Basic reporting dashboards**: pre-built dashboards for pipeline, sales activity, and contacts
- **Mobile apps**: iOS and Android
- **Lists**: up to 100 static and 100 active lists
- **Workflows**: up to 5 active workflows
- **Integrations**: Gmail, Outlook, Google Calendar, Office 365
- **GDPR consent fields**: built-in
- **Conversations inbox**: shared team inbox for chat, email, and social messages

**Not included in Free**:
- Sequences (automated follow-up series)
- Smart content (dynamic content personalization)
- A/B testing
- Custom reporting (you get pre-built dashboards only)
- Call recording and transcription
- Quotes with e-signature
- Custom object pipelines (Enterprise only anyway)
- Advanced permissions
- Automated lead rotation

### How CRM Data Flows Across Hubs

Understanding data flow is critical for configuring HubSpot correctly:

```
Form Submission (Marketing) 
  → New Contact created in CRM 
  → Workflow triggers (Automation) 
  → Lead assigned to Sales rep 
  → Deal created on contact record 
  → Sales rep sends Sequence emails 
  → Emails logged on Contact + Deal timelines 
  → Deal closes → Invoice generated (Commerce) 
  → Ticket created for onboarding (Service) 
  → Knowledge Base articles suggested automatically 
  → Survey sent → CSAT score logged on Contact
```

Every action across hubs updates the same contact, company, or deal record. This means:
- A marketing email open appears on the same timeline as a support ticket resolution
- A deal amount from Sales is visible in Service when a ticket is created
- A customer's subscription status from Commerce is visible in Marketing for smart content decisions

---

## Contacts — Complete Guide

### The Contact Record Structure

Every contact in HubSpot has:

1. **Standard Properties**: Hundreds of built-in fields (first name, last name, email, phone, job title, company name, industry, website, address, lifecycle stage, lead status, created date, last activity date, etc.)

2. **Custom Properties**: Fields you create (up to 1,000 on Pro, 10,000 on Enterprise)

3. **Associations**: Links to companies, deals, tickets, custom objects, and other records

4. **Activity Timeline**: Every interaction in chronological order — emails, calls, meetings, notes, form submissions, page views, deal stage changes, ticket updates

5. **List Memberships**: Which static and active lists the contact belongs to

6. **Communication Subscriptions**: Which email types the contact has opted into

7. **GDPR Consent Status**: Consent records for processing and communication

8. **Contact Owner**: The HubSpot user assigned to manage this contact

### Lifecycle Stages Explained

The lifecycle stage is one of the most important properties on a contact. It defines where the contact is in their journey with your business:

| Stage | Description | Typical Actions |
|-------|-------------|-----------------|
| **Subscriber** | Opted in to receive content but not yet identified as a lead | Send educational content, blog posts, newsletters |
| **Lead** | Identified as a potential customer (form fill, chat, meeting) | Nurture with targeted content, sales outreach |
| **MQL (Marketing Qualified Lead)** | Met marketing's qualification criteria (score threshold, behavior) | Hand off to sales for follow-up |
| **SQL (Sales Qualified Lead)** | Sales has qualified the lead (BANT, budget, authority, need, timeline) | Schedule demo, send proposal |
| **Opportunity** | Active deal in progress, engaged in sales process | Focus on closing, negotiate terms |
| **Customer** | Closed-won deal, has purchased | Onboard, support, upsell/cross-sell |
| **Evangelist** | Highly satisfied customer who actively promotes your brand | Request referrals, case studies, reviews |
| **Other** | Doesn't fit standard stages (partner, investor, vendor) | Specific workflows apply |

**Best Practice**: Set up automation to move contacts through lifecycle stages automatically:
- New form submission → Set lifecycle to "Lead"
- Lead score reaches 50+ → Set lifecycle to "MQL"
- Deal created → Set lifecycle to "Opportunity"
- Deal closed won → Set lifecycle to "Customer"

### Creating Contacts

**Method 1: Manual Creation**
1. Navigate to **Contacts** > **Contacts** in the main navigation
2. Click the orange "Create contact" button (top-right)
3. Fill in required fields (email is the most common identifier, but you can create without email if you use a different unique identifier)
4. Add standard properties: first name, last name, phone, job title
5. Scroll to property groups and fill in additional fields
6. Click "Create"

**Method 2: CSV Import**
1. Navigate to **Contacts** > **Import** (or **Settings** > **Import & Export**)
2. Click "Import from file"
3. Choose file type: CSV (.csv), XLSX (.xlsx), or TSV (.tsv)
4. Select "Contacts" as the object type
5. Upload your file (limits: 15MB on Free/Starter, 100MB on Pro, 1GB on Enterprise)
6. **Column Mapping**: HubSpot auto-detects standard fields based on column headers. If your column is "First Name", it auto-maps to `firstname`. If it doesn't match, you'll see a dropdown to manually select the HubSpot property.
7. **Unmapped columns**: You can skip, map to existing properties, or create new custom properties on-the-fly
8. **Identifier matching**:
   - **Email**: Primary identifier. If email exists in CRM, contact is updated. If not, new contact created.
   - **First name + Last name + Email**: More precise matching
   - **Custom unique identifier**: Use your own ID field
9. **Duplicate handling**:
   - **Skip**: Don't import records that match existing
   - **Overwrite**: Update existing records with imported data
   - **Create new**: Always create new contacts, even if duplicates
10. **Association setup**: Optionally associate imported contacts to existing companies or deals by including a "Company name" or "Deal name" column
11. **Marketing contact assignment**: Choose whether imported contacts should be marketing contacts (affects billing on paid Marketing Hub)
12. **Review screen**: Shows first 10 rows, mapping summary, estimated total
13. Click "Import" → Import runs in background; you get an email when complete

**Method 3: Form Submission**
When a visitor submits a HubSpot form on your website:
- If the email doesn't exist in CRM → New contact created
- If the email exists → Contact updated with form data
- The form submission is logged on the contact's timeline
- Workflows can trigger on form submission

**Method 4: API Creation**
```python
# Python SDK example
from hubspot import HubSpot
api_client = HubSpot(access_token="YOUR_TOKEN")
contact = api_client.crm.contacts.basic_api.create(
    {
        "properties": {
            "email": "jane@example.com",
            "firstname": "Jane",
            "lastname": "Doe",
            "jobtitle": "Marketing Manager",
            "company": "Acme Corp"
        }
    }
)
```

**Method 5: Integration Sync**
Contacts synced from Gmail, Outlook, LinkedIn, Salesforce, Shopify, or 1000+ other integrations appear automatically in the CRM.

### Merging Contacts

Duplicate contacts are inevitable. HubSpot provides merging to clean up duplicates.

**When to merge**: When two or more contact records represent the same person.

**How to merge**:
1. Open one of the duplicate contacts
2. Click the action menu (•••) > Merge
3. Select the other duplicate contact(s)
4. **Choose primary record**: The primary record's properties, associations, and activities become the surviving record
5. Review conflicts: For properties with different values, choose which record's value to keep (primary or secondary)
6. **Merge preview**: Shows what the merged record will look like
7. Click "Merge"

**What happens during merge**:
- Properties: Values from primary kept; secondary values added only if primary is empty
- Associations: Combined — all companies, deals, tickets from both records
- Activities: Combined into one timeline
- List memberships: Combined
- Tasks: Combined and re-assigned
- Deals: All deals stay associated
- Notes: Combined
- Emails: Combined in timeline

**What is irreversible**: Merging contacts is **permanent**. There is no "unmerge" option. The secondary contact record is deleted.

**Best practices for merging**:
- Before merging, decide which record is the "canonical" version (usually the one with a longer history or more complete data)
- If a contact has active deals or open tickets, merge carefully
- When using Operations Hub deduplication, you can auto-merge with rules

### Contact Ownership

Every contact can be assigned an owner (a HubSpot user).

**Assigning owners**:
1. Open contact record
2. Click the "Contact owner" field
3. Search and select a HubSpot user

**Auto-assignment rules**: You can create rules that automatically assign contacts:
- **Round-robin**: Distribute evenly among a team
- **Rules-based**: Assign based on territory, company size, industry, lead source, etc.
- **Form-based**: Set owner in form submission options

**Team-based ownership** (Professional+): Assign contacts to teams rather than individuals for shared visibility.

### Communication Preferences

HubSpot provides sophisticated subscription management:

**Subscription types**:
- **Bulk email**: Marketing emails (newsletters, promotions, blog digests)
- **One-to-one**: Sales emails (sequences, personal outreach)
- **Transactional**: Operational emails (receipts, password resets, confirmations)

**Managing subscriptions**:
- Contacts can manage their own subscriptions via the **subscription preferences page** (HubSpot-hosted)
- The "Update your preferences" link is automatically included in all marketing emails
- Unsubscribe management: one-click unsubscribe is required by law (CAN-SPAM, GDPR)
- **Double opt-in**: Optional setting where contacts must confirm their email after subscribing

**GDPR consent**:
- Add GDPR consent fields to forms
- Track consent type (explicit consent, legitimate interest)
- Record consent timestamp and method
- Store consent evidence (what the contact saw and agreed to)

### Breeze Intelligence Enrichment

With Breeze Intelligence (paid add-on), contacts are enriched automatically:

- **Auto-enrich on creation**: When a contact is created, Breeze Intelligence looks up their company and job title
- **Company firmographics**: Industry, revenue, employee count, location, funding
- **Technographics**: What software and tools the company uses
- **Contact data**: Direct phone numbers, LinkedIn URLs, professional email addresses
- **Intent signals**: Which contacts/companies are actively researching your product category

**Enrichment settings**:
- Settings > Data Management > Breeze Intelligence
- Configure auto-enrichment rules
- Set enrichment triggers (on create, on update, batch)
- View enrichment history per contact

### Contact Reporting

Key reports for contacts:
- **New contacts over time**: Track contact growth
- **Contacts by lifecycle stage**: See distribution across the funnel
- **Contacts by lead source**: Which channels generate the most contacts
- **Contacts by owner**: Workload distribution
- **Contacts by company**: Account-based views
- **Activity by contact**: Email opens, page views, form submissions

---

## Companies — Complete Guide

### Company Record Structure

Companies in HubSpot represent business accounts or organizations. Key features:

**Standard properties**: Name, domain, industry, annual revenue, number of employees, country, company owner, company type (prospect, partner, customer, vendor), description, website URL, phone, address

**Custom properties**: Same range as contacts

**Key differentiators from contacts**:
- Companies have a **domain** property that auto-detects company info
- Companies can have **parent-child hierarchies** (Enterprise)
- Companies can have **multiple contacts** associated
- Breeze Intelligence enrichment for companies is more detailed (firmographics, technographics, intent)

### Creating Companies

**From a contact**: When you associate a contact to a company, if the company doesn't exist, you can create it from the association dialog.

**Manual creation**:
1. **Contacts** > **Companies** > Create company
2. Enter company name (required), domain (auto-fills company insights), and other properties
3. Click Create

**CSV import**: Steps same as contacts but select object type "Companies"

**Domain verification**: HubSpot verifies company domains to provide accurate company insights. Verified domains unlock Breeze Intelligence data.

### Company Hierarchies (Enterprise)

Parent-child relationships between companies:
- **Parent company**: Usually the holding company or HQ
- **Child company**: Subsidiary, branch, division
- **Multi-level**: Grandparent → Parent → Child

**Setting up hierarchies**:
1. Open a company record
2. Go to the "Hierarchy" tab
3. Click "Add parent" or "Add child"
4. Search and select the related company
5. Choose association label

### Company Insights with Breeze Intelligence

When a company record has a verified domain, Breeze Intelligence enriches it with:

**Firmographics**:
- Industry (from multiple classification systems)
- Annual revenue range
- Employee count range
- Founded year
- Public/private status
- Stock ticker (for public companies)
- Headquarters and branch locations

**Technographics**:
- CRM system (Salesforce, Zoho, etc.)
- Marketing automation (Marketo, Pardot, etc.)
- E-commerce platform (Shopify, Magento, etc.)
- Support platform (Zendesk, Freshdesk, etc.)
- Analytics tools (Google Analytics, Adobe, etc.)
- Cloud provider (AWS, Azure, GCP)
- HR/Payroll systems

**Intent signals**:
- Research activity about your product category
- Content consumption (whitepapers, case studies, comparison pages)
- Competitor research activity
- Budget signals (job postings for relevant roles)

**Recent activity**:
- News mentions
- Funding rounds
- Product launches
- Executive changes
- Job postings with growth signals

---

## Deals — Complete Guide

### Deal Record Structure

Deals represent sales opportunities. Key components:

**Standard properties**: Deal name, amount, deal stage, pipeline, close date, deal owner, created date, deal type (new business, upgrade, renewal), forecast category (commit, best case, pipeline), probability, deal source

**Line items**: Products/services associated with the deal, with quantity, unit price, and discount

**Associations**: Contact (buyer), company (account), quotes, invoices, payments, tickets

### Creating Deals

**From a contact/company record**:
1. Open a contact or company record
2. In the "Deals" section, click "Create deal"
3. Enter deal name, amount, pipeline, and stage
4. Set close date, deal owner
5. Add line items (if applicable)
6. Click Create

**From a form submission**: Marketing workflows can auto-create deals when a contact fills out a "request a demo" form.

**From import**: CSV import similar to contacts, mapping deal stages to values.

**From email**: If a contact emails about purchasing, you can create a deal directly from the email timeline entry.

### Line Items

Line items are products/services on a deal:

**Adding line items**:
1. Open a deal
2. In the "Line items" section, click "Add line items"
3. Select from your product library or create a custom line item
4. Set quantity, unit price, and discount (flat amount or percentage)
5. Recurring billing period (for subscriptions)

**Product library**: Manage your catalog at **Settings** > **Products** > **Products**

### Deal Splits (Enterprise)

When multiple reps share credit for a deal:
- Split revenue among up to 15 reps
- Split by percentage (e.g., 70%/30%)
- Each rep's split affects their individual forecast
- Splits can be added during deal creation or after close

### Pipeline Management

See the [Pipelines section](#pipelines--complete-guide) below for detailed coverage.

### Deal Board View vs List View

**Board view** (Kanban):
![Screenshot: Deals shown as cards in columns by pipeline stage]
- Drag and drop deals between stages
- Cards show deal name, amount, contact, and owner
- Quick actions (edit, delete, change owner)
- Collapse stages to focus on specific pipeline sections

**List view**:
- Table layout with sortable columns
- Bulk edit, export, filter
- Custom columns: choose which properties to display
- CSV export

**Table view**:
- Similar to list view but with inline editing
- Click any cell to edit without opening the record

---

## Tickets — Complete Guide

### Ticket Record Structure

Tickets represent support requests or customer issues:

**Standard properties**: Ticket name, status (New, Waiting on Contact, Waiting on Us, Closed), priority (Low, Medium, High, Urgent), type (Question, Problem, Feature Request, Refund, Order Issue, Other), pipeline, ticket owner, created date, time to close, source (email, chat, phone, form, internal)

**Pipeline**: Tickets follow their own pipeline (similar to deals but focused on resolution stages)

### Creating Tickets

**Manual creation**:
1. **Contacts** > **Tickets** > Create ticket
2. Enter ticket name, pipeline, status, priority, type
3. Associate to contact and company
4. Add description of the issue
5. Click Create

**Email-to-ticket**: Configure a support email address. Emails sent to it automatically become tickets linked to the sender's contact record.

**Form submission**: Create a "Report an issue" or "Contact support" form. Submissions create tickets.

**Chatbot**: Chat conversations can create tickets automatically with the conversation history attached.

**Automation**: Workflows can create tickets based on deal stage changes, property values, or time-based triggers.

**API**: Create tickets programmatically for integrations.

---

## Properties — Complete Guide

### Property Types — Detailed

| Property Type | UI Element | Use Case | Example Value |
|--------------|------------|----------|---------------|
| **Single-line text** | Text input | Short free-form data | "Acme Corp" |
| **Multi-line text** | Textarea | Paragraphs, notes | "Customer reported issue with login..." |
| **Number** | Numeric input | Quantities, scores, amounts | 15000 |
| **Date** | Date picker | Calendar dates | June 15, 2025 |
| **Date/Time** | DateTime picker | Precise timestamps | June 15, 2025 at 3:30 PM |
| **Dropdown select** | Dropdown menu | Single choice from list | Industry: Technology |
| **Multiple checkboxes** | Checkbox group | Multiple choices | Interests: [x] Email [x] Webinar [ ] Events |
| **Single checkbox** | Single checkbox | Boolean yes/no | "I agree to terms" ☑ |
| **Radio select** | Radio buttons | Single choice, visible options | Priority: ○ Low ○ Medium ● High |
| **Boolean** | Toggle switch | True/false | Active ● ————— ○ |
| **File (URL)** | File upload | Documents, images, PDFs | https://...contract.pdf |
| **Calculation** | Read-only formula | Computed values | `deal_amount * 0.15` |
| **Phone** | Phone input with formatting | Phone numbers, validation | +1 (555) 123-4567 |
| **Email** | Email input with validation | Email addresses, click-to-email | jane@example.com |
| **Domain** | URL input | Website addresses, click-to-visit | acme.com |
| **Rich text** | WYSIWYG editor | Formatted content, article bodies | Bold, italic, lists, links |
| **HTML** | HTML editor | Custom HTML content | `<div class="custom">` |
| **Recurring** | Recurring pattern | Subscription intervals | Monthly |

### Creating Custom Properties — Step-by-Step

1. Navigate to **Settings** (gear icon, top-right) > **Data Management** > **Properties**
2. Click "Create property" button (top-right)
3. **Select object**: Choose which CRM object this property belongs to (Contact, Company, Deal, Ticket, Product, or a Custom Object)
4. **Choose field type**: Select from the table above. **Important**: Field type cannot be changed after creation. Choose carefully.
5. **Label**: The human-readable name your team will see (e.g., "Preferred Contact Time")
6. **Internal name**: Auto-generated from the label, but you can customize it. **This cannot be changed after creation**. Best practice: use lowercase_with_underscores (e.g., `preferred_contact_time`)
7. **Description**: Internal description shown as a tooltip. Useful for explaining what the field should contain.
8. **For dropdown/multiple checkboxes/radio**: Add options. Each option has:
   - **Label**: What users see in the UI (e.g., "Morning")
   - **Value**: What's stored internally (e.g., "morning")
   - **Hidden/archived**: Hide old options without deleting them
9. **Property group**: Choose which group this property appears under on record pages. You can create new groups.
10. **Field appearance options** (for some types):
    - **Placeholder text**: Ghost text inside the field
    - **Number of lines**: For multi-line text
    - **Min/max**: For numeric fields
11. **Display logic** (Enterprise): Show or hide this field based on other property values. Example: Show "Number of employees" only when "Company size" is "Enterprise"
12. **Required**: Force users to fill this field before saving. Applies to manual creation, imports, and API.
13. **Read-only**: Field value can't be changed manually. Can only be updated via API, workflows, or automation.
14. **GDPR consent**: Mark as a consent property (only if it's a GDPR consent field)
15. **Create property**

### Property Groups

Groups organize properties into logical sections on record pages.

**Common default groups**:
- About this contact/company/deal
- Contact information
- Company information
- Deal information
- Sales details
- Marketing details

**Creating groups**:
1. Settings > Data Management > Properties
2. Click "Create group"
3. Name the group, choose object, set order

**Best practice**: Keep related properties in the same group. Don't create too many groups (5-10 is ideal for most objects).

### Calculated Properties (Operations Hub)

Formula-based properties that compute values from other properties. Syntax examples:

```
# Simple arithmetic
deal_discount = deal_amount * 0.10

# Conditional
commission = IF (deal_stage = "closedwon", deal_amount * 0.05, 0)

# Text concatenation
full_name = firstname + " " + lastname

# Date calculation
days_in_pipeline = DATE_DIFF(createdate, TODAY(), "day")
```

**Available functions**:
- `IF(condition, value_if_true, value_if_false)` — Conditional logic
- `AND(condition1, condition2)` — Logical AND
- `OR(condition1, condition2)` — Logical OR
- `DATE_DIFF(date1, date2, unit)` — Difference between dates
- `TODAY()` — Current date
- `NOW()` — Current datetime
- `CONTAINS(text, substring)` — Check if text contains substring
- `ROUND(number, decimal_places)` — Round to decimal places

### Rollup Properties (Operations Hub)

Aggregate values from associated records. Examples:

**On Contact**: Roll up deals:
- `SUM(associated_deals, amount)` — Total deal value
- `COUNT(associated_deals)` — Number of deals
- `AVG(associated_deals, amount)` — Average deal value
- `MAX(associated_deals, amount)` — Largest deal
- `MIN(associated_deals, amount)` — Smallest deal
- `LATEST(associated_deals, closedate)` — Most recent deal close date

**On Company**: Roll up contacts and deals:
- `COUNT(associated_contacts)` — Number of contacts
- `SUM(associated_deals, amount)` — Total pipeline value
- `COUNT(associated_tickets)` — Open tickets count

**Best practice**: Use rollup properties for at-a-glance metrics on parent records. Example: Show total deal value on a company record so account managers see the full relationship value.

### Property Permissions (Enterprise)

Control who can view, edit, or delete specific properties:

1. Settings > Data Management > Properties
2. Select a property
3. Go to the "Permissions" tab
4. Set permissions per user role:
   - **View**: Who can see this property
   - **Edit**: Who can modify this property
   - **Delete**: Who can delete this property

**Use case**: Hide compensation-related properties (commission rates, bonus amounts) from regular sales reps but make them visible to managers and admins.

---

## Pipelines — Complete Guide

Pipelines are visual stages for tracking progress. Used for deals, tickets, and (on Enterprise) custom objects.

### Creating a Deal Pipeline — Step-by-Step

1. Navigate to **Settings** > **Data Management** > **Pipelines**
2. Select "Deals" from the object dropdown
3. Click "Create pipeline"
4. **Name your pipeline**: e.g., "Standard Sales Process" or "Enterprise Sales"
5. **Add stages**: Click "Add a stage" for each step in your process

   Example stages for a SaaS pipeline:
   | Stage | Probability | Description |
   |-------|-------------|-------------|
   | New Lead | 10% | Initial inquiry |
   | Qualified | 25% | BANT criteria met |
   | Demo Scheduled | 40% | Demo confirmed |
   | Demo Completed | 50% | Demo presented |
   | Proposal Sent | 70% | Quote delivered |
   | Negotiation | 85% | Terms discussion |
   | Closed Won | 100% | Deal closed |
   | Closed Lost | 0% | Lost deal |

6. **Drag to reorder** stages
7. **Stage-to-stage rules**:
   - **Enable stage locking**: Deals must go through each stage sequentially. No skipping.
   - **Allow backward movement**: Can deals return to earlier stages? (Usually yes for contract sent → negotiation)
   - **Required properties**: Set fields that must be filled before moving to the next stage (e.g., close date required from "Proposal Sent" onwards)
8. **Pipeline rotation** (optional):
   - **Round-robin**: Distribute new deals evenly
   - **Rules-based**: Assign based on territory, deal size, product
9. Click "Save"

### Pipeline Design Best Practices

- **Too few stages (2-3)**: Doesn't provide enough tracking granularity
- **Too many stages (15+)**: Creates administrative burden. 5-8 stages is ideal for most businesses.
- **Avoid "parking lot" stages**: A deal should always be moving forward. Remove stages where deals sit indefinitely.
- **Closed lost is a stage, not deletion**: Track why deals are lost. Create a "Closed Lost" stage rather than deleting deals.
- **Probability accuracy**: If you say 50% probability at demo, but only 20% of deals at demo stage close, your probability is wrong. Review and adjust.

### Multiple Pipeline Strategy

Use multiple pipelines when you have fundamentally different sales processes:

| Pipeline | Used For | Stages |
|----------|----------|--------|
| Standard Sales | New business | Lead → Qualified → Demo → Closed |
| Renewals | Existing customers | Notice → Quote → Approved |
| Partner Deals | Channel sales | Lead → Partner → Closed |
| Self-Serve | Low-touch upgrade | Trial → Upgrade → Active |

**When NOT to use multiple pipelines**:
- If the stages are similar but products differ (use deal type property instead)
- If it's just for reporting segmentation (use custom properties for reporting)

---

## Lists — Complete Guide

### Static Lists

A fixed snapshot of records. Members stay the same until you manually change them.

**When to use static lists**:
- One-time email sends (event invitation)
- Manual groupings you don't want changing
- Historical snapshots for analysis
- Ad retargeting (static audience)

**Creating a static list**:
1. **Contacts** > **Lists** > Create list
2. Select "Static list"
3. Name: "Webinar June 2025 Attendees"
4. Add contacts manually:
   - Search contacts and add individually
   - Import a CSV of contacts
   - Add from a saved filter/search
   - Add all contacts from a dynamic search
5. Save

**Adding/removing members**:
- Open the list → "Add contacts" or "Remove contacts"
- Bulk add by importing contact IDs
- Remove all members to clear the list

### Active Lists

Dynamic lists that update in real-time based on criteria.

**When to use active lists**:
- Email sends that should only go to qualified leads
- Workflow enrollment (trigger workflows when contacts meet criteria)
- Live reporting segments
- Ad audiences that should update automatically

**Creating an active list** — Step-by-Step:
1. **Contacts** > **Lists** > Create list
2. Select "Active list"
3. **Name**: e.g., "Hot Leads — Engaged + High Score"
4. **Set criteria**:

   **Basic filters**:
   - Property: "Lifecycle stage" → is → "MQL"
   - Property: "Lead score" → is greater than → "50"
   - Property: "Last activity date" → is after → "30 days ago"

   **AND/OR logic**:
   - **All criteria must match (AND)**: Use for narrow segments
   - **Any criteria matches (OR)**: Use for broad segments
   - **Mixed AND/OR**: Create groups. Example: "(Lifecycle stage is MQL OR Lead score > 50) AND (Last activity is after 30 days ago)"

   **Filter types available**:
   - **Contact property**: Any contact field
   - **Form submissions**: Specific form, submitted after date
   - **Page views**: Specific page, URL contains, title contains
   - **Email engagement**: Opened, clicked, replied to specific campaign
   - **List membership**: Member of another list
   - **Deal associations**: Has deal in specific stage
   - **Company associations**: Related to company with specific property
   - **Activity**: Has logged call, meeting, email within timeframe

5. **Preview**: Shows estimated membership count. Click to see actual contacts that match.
6. Click "Save"

**How active lists update**: HubSpot checks list criteria:
- When a contact's properties change
- When a contact submits a form
- When a contact visits a page
- On a regular re-evaluation schedule
- This happens within minutes (typically 5-15 minutes for most criteria)

### List Use Cases in Practice

| Use Case | List Type | Criteria |
|----------|-----------|----------|
| Newsletter subscribers | Active | Contact → Email subscription status → is "Subscribed" |
| Hot leads for sales | Active | Lead score > 80 AND Last activity is within 7 days |
| Webinar attendees | Static | Manually added after event |
| At-risk customers | Active | Open tickets > 2 AND No deal in last 90 days |
| Abandoned cart | Active | Form submitted "cart abandon" AND No deal created |
| Product interest | Active | Form submission → Product interest is "Product A" |

---

## Activities — Complete Guide

Activities are events logged on a contact, company, or deal timeline. They include emails, calls, meetings, notes, tasks, form submissions, page views, and system events.

### Logging Emails

**Automatic logging** (via integration):
- Connect Gmail/Outlook → HubSpot automatically logs sent and received emails
- A 1x1 tracking pixel in your signature enables open tracking
- Link tracking: HubSpot rewrites links for click tracking

**Manual logging**:
1. Open a contact/company/deal record
2. Scroll to the "Timeline" section
3. Click the filter icon → Toggle "Email"
4. Click "Log email"
5. Fill in: To, From, Subject, Body, Date
6. Click "Log"

**Email tracking limits**:
- Free: 200 tracked emails/day
- Pro/Enterprise: 1,000 tracked emails/day
- Some email clients block tracking pixels (Apple Mail Private Relay, for example)

### Logging Calls

**Automatic logging** via HubSpot Calling:
1. Go to the contact record
2. Click the phone icon → "Call with HubSpot"
3. Your browser will request microphone access
4. Dialer opens, you can enter a number or use the contact's stored number
5. Call connects via your computer (VoIP)
6. After the call, you can log: Duration (auto), notes (manual), outcome (dropdown), recording (if enabled)

**Manual call logging**:
1. Open contact record
2. Click "Log a call" in the timeline section
3. Enter: Direction (inbound/outbound), duration, notes, outcome
4. Click "Log"

**Call outcome options**: Connected, Left voicemail, No answer, Busy, Wrong number, Other

### Logging Meetings

**Automatic**:
1. Share your HubSpot meeting link
2. Contact books a time → Meeting logged on both your and their timeline
3. Calendar integration syncs

**Manual**:
1. Open contact record
2. Click "Log a meeting"
3. Enter: Title, date/time, duration, meeting type (Discovery, Demo, Proposal, Closing, Other), notes, attendees
4. Click "Log"

### Notes

Free-form text added to the timeline:
1. Open a record
2. In the "Add a note" box at the top of the timeline
3. Type your note (supports basic formatting)
4. Click "Add note"

Notes support @mentions of other HubSpot users (they get notified).

### Tasks

Track action items assigned to HubSpot users:

1. **Create a task**:
   - From a contact/deal record: Click "Create task" in the timeline
   - From the task dashboard: **Sales** > **Tasks**
   - From a workflow: Automation creates tasks on trigger

2. **Task fields**:
   - Title (required)
   - Due date (with reminder)
   - Priority (Low, Medium, High)
   - Task type (Email, Call, To-do, Follow-up, Meeting, Other)
   - Assigned to (HubSpot user, defaults to you)
   - Associated to (contact, company, deal)
   - Queue (group tasks into logical sets)
   - Notes (free text)

3. **Task queues**: Create custom queues for different workflows:
   - "Priority follow-ups" — High priority, due today
   - "Weekly check-ins" — Recurring tasks for key accounts
   - "Data cleanup" — Tasks to update properties

4. **Task notifications**: When a task is assigned and when it's overdue

5. **Task reporting**: Reports on tasks (created, completed, overdue) per user, per team

---

## Associations — Complete Guide

Associations link records across objects. They're what make HubSpot a connected CRM rather than a set of isolated tables.

### Standard Associations

| From | To | Cardinality | Default Label |
|------|----|------------|---------------|
| Contact | Company | Many-to-one | Employee of / Has employee |
| Contact | Deal | Many-to-many | Contact on deal / Has contact |
| Contact | Ticket | Many-to-many | Contact on ticket / Has contact |
| Company | Deal | One-to-many | Company deal / Associated company |
| Company | Ticket | One-to-many | Company ticket / Associated company |
| Deal | Quote | One-to-many | Deal quote / Associated deal |
| Deal | Line Item | One-to-many | Deal line item / Associated deal |
| Deal | Product | Many-to-many | Deal product / Associated deal |
| Contact | Company | Many-to-many (custom label) | Primary contact / Secondary contact |

### Association Labels

Labels give semantic meaning to associations:

**Creating labels**:
1. Settings > Data Management > Associations
2. Select object pair (e.g., Contact → Company)
3. Click "Create label"
4. Label the forward direction: "Employee of"
5. Label the reverse direction: "Has employee"
6. Click "Create"

**Use case examples**:
- Contact → Company: "Primary contact" / "Secondary contact"
- Deal → Contact: "Decision maker" / "Champion" / "Economic buyer"
- Contact → Custom Object (Course): "Enrolled in" / "Has student"

### Viewing Associations

On any record page, you'll see association sections:
- **Contacts** section shows associated people
- **Companies** section shows associated accounts
- **Deals** section shows associated opportunities
- **Tickets** section shows associated support requests

Each section shows a card or table with key properties of the associated record.

---

## CRM Reporting

### Standard Dashboards

HubSpot provides pre-built dashboards covering:
- **Pipeline report**: Deals by stage, total value, weighted value
- **Sales activity report**: Emails sent, calls made, meetings logged per rep
- **Contacts report**: New contacts over time, by source, by lifecycle stage
- **Conversion report**: Visitor → Contact → Deal → Customer conversion rates

### Custom Report Builder

1. Navigate to **Reports** > **Dashboards** > **Create report**
2. **Choose report type**:
   - **Single object**: Report on one object (e.g., contacts by lifecycle stage)
   - **Cross-object**: Combine multiple objects (e.g., contacts with deals, showing deal amount)
   - **Funnel**: Visualize conversion between stages
   - **Trends**: Metrics over time (e.g., monthly new deals)
   - **Attribution**: Which sources drive closed deals
3. **Select data sources**: Choose the primary object and any related objects
4. **Configure filters**: Narrow down which records to include
5. **Select visualization**:
   - Bar chart (vertical, horizontal, stacked, grouped)
   - Line chart
   - Pie/donut chart
   - Table
   - Single number (KPI)
   - Area chart
6. **Add to dashboard**: Create a new dashboard or add to existing one
7. **Schedule delivery**: Email the dashboard to stakeholders on a recurring basis (daily, weekly, monthly)

### Attribution Reporting

Understand which marketing channels contribute to revenue:

**Attribution models**:
- **First interaction**: First touchpoint gets 100% credit
- **Last interaction**: Last touchpoint gets 100% credit
- **Linear**: Equal credit to all touchpoints
- **U-shaped**: 40% first, 40% last, 20% middle
- **W-shaped**: 30% first, 30% deal creation, 30% close, 10% middle
- **Time decay**: More recent touchpoints get more credit

---

## Limits That Matter

### By Plan

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Contacts | 1,000,000 | 1,000,000 | Unlimited | Unlimited |
| Companies | 100,000 | 500,000 | 1,000,000 | Unlimited |
| Custom objects | 10 (10k records) | 10 (100k records) | 10 (1M records) | 200 (unlimited) |
| Custom properties/object | 1,000 | 1,000 | 1,000 | 10,000 |
| Deal pipelines | 10 | 10 | 50 | 100 |
| Deal stages/pipeline | 30 | 30 | 30 | 30 |
| Static lists | 100 | 500 | 1,000 | Unlimited |
| Active lists | 100 | 250 | 1,000 | Unlimited |
| List members | 1,000,000 | 1,000,000 | 1,000,000 | Unlimited |
| Workflows (active) | 5 | 20 | 500 | 1,000+ |
| Teams | 1 | 3 | 15 | Unlimited |
| Import file size | 15MB | 15MB | 100MB | 1GB |
| API daily calls | 250,000 | 500,000 | 1,000,000 | Varies |

### Important Limits to Monitor

- **Dropdown property options**: 1,000 max per property
- **File upload per property**: 1 file per file-upload property
- **Association labels**: 50 unique labels per object pair
- **Associations per record**: 10,000 max (1,000 per label)
- **Tasks**: No hard limit, but performance degrades beyond 100,000 per user

---

## Common Gotchas

### 1. Merging is Permanent
Once you merge two contacts, there is no "undo." The secondary record is permanently deleted. Always double-check the merge preview before confirming.

### 2. Property Internal Names Cannot Change
After creating a property, the internal name (e.g., `my_custom_field`) is locked. If you spelled it wrong, you'd need to create a new one. The label (display name) CAN change anytime.

### 3. Deleting Properties Has a Safety Net
Deleted properties go to a recycle bin for 30 days (on most paid tiers). After 30 days, data is permanently deleted. On the Free tier, there is no recycle bin — deletion is immediate.

### 4. Pipeline Stages with Active Deals
If a pipeline stage has deals in it, you cannot delete that stage. You must first move all deals to another stage.

### 5. CSV Import Encoding
HubSpot expects UTF-8 encoded CSV files. If your CSV has special characters (é, ñ, ü, etc.) and is encoded as Windows-1252 (Latin-1), you'll get garbled text. Save CSV files as "UTF-8 with BOM" to avoid this.

### 6. Timezone Affects Date Properties
HubSpot stores dates in UTC but displays them in the user's timezone. If your team spans multiple timezones, there can be date confusion — especially for "today" logic in workflows.

### 7. Workflow Re-enrollment Pitfalls
When a contact exits and re-enters a workflow, they may take actions again (e.g., get another welcome email). Always check re-enrollment settings.

### 8. Activity History on Merge
When merging contacts, activities from both records combine on the timeline. But if you accidentally merge two records that were NOT duplicates, the activity mix is permanent.

### 9. API Property Mapping Case Sensitivity
Property internal names are case-sensitive in the API. `FirstName` and `firstname` are different properties. The standard property is lowercase: `firstname`.

### 10. Contact Deletion is Soft
When you "delete" a contact, they go to the recycle bin (30 days). But deleted contacts also decrement from your marketing contact limit for up to 30 days (Pro) or up to 7 days (Free/Starter).

---

## Use Cases

### Use Case 1: B2B Lead Management
**Setup**: Import 5,000 contacts from a trade show. Set lifecycle stages. Assign owners based on territory. Create workflow: "When contact is MQL for 7 days with no activity → notify manager."

### Use Case 2: E-commerce Customer CRM
**Setup**: Shopify integration creates contacts from orders. Custom properties: "Last order date," "Average order value," "Preferred category." Rollup property on company: "Total lifetime orders." Active list: "VIP customers" — order value > $500 AND purchased in last 90 days.

### Use Case 3: Agency Client Management
**Setup**: Custom object "Project" associated to contacts and companies. Custom properties on deal: "Project scope," "Retainer amount." Pipeline stages: Discovery → Proposal → Signed → Onboarding → Active → Completed.

### Use Case 4: Multi-product Sales Team
**Setup**: Multiple deal pipelines (Product A, Product B, Product C). Rules-based assignment routing to specialized reps. Cross-object reports showing pipeline velocity per product.

### Use Case 5: Service-first CRM
**Setup**: Heavy use of tickets and SLAs. Companies enriched with support plan type. Properties track: "Current SLA", "Escalation level", "Last support interaction." Rollup: total open tickets per company shown on company record.