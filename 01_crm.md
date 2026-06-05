# 1. HubSpot CRM

## What It Does
HubSpot CRM is the foundational layer of the HubSpot platform. It stores and manages all customer data including contacts, companies, deals, tickets, goals, and custom objects. It provides a unified view of customer interactions across marketing, sales, and service.

## Key Features

### Contacts
- Stores individual people records with standard properties (name, email, phone, company, etc.)
- Custom properties: create up to 10,000 custom properties (Enterprise: unlimited)
- Contact lifecycle stages: Subscriber, Lead, MQL, SQL, Opportunity, Customer, Evangelist, Other
- Contact ownership: assign to specific users/teams
- Merge contacts (detect duplicates, merge records)
- List membership tracking
- Timeline of all interactions (emails, meetings, notes, calls)
- GDPR consent tracking built in

### Companies
- Stores business/account records
- Company properties: name, domain, industry, revenue, number of employees, etc.
- Associate contacts to companies (many-to-one)
- Custom object association labels enable many-to-many relationships with custom labels (e.g., "Primary vendor" vs "Secondary vendor")
- Company insights (technographics, firmographics from HubSpot data partners)
- **Breeze Intelligence** adds deeper company enrichment: intent signals, company firmographics, technographics, and B2B contact data directly in CRM records
- Company domains auto-detect via email domain

### Deals
- Sales pipeline management
- Deal stages (customizable per pipeline)
- Deal amount, close date, deal owner
- Deal probability (auto-calculated based on stage)
- Multiple pipelines (Professional+: 50+ pipelines depending on tier)
- Line items associated with deals
- Discounts, recurring revenue tracking
- Deal forecasting (Sales Hub)
- Auto-assignment rules for deal creation

### Tickets
- Customer support request tracking
- Ticket status: New, Waiting on Contact, Waiting on Us, Closed
- Ticket priority: Low, Medium, High, Urgent
- Ticket type: Question, Problem, Feature Request, Refund, etc.
- Pipeline tracking for tickets (Service Hub)
- SLA tracking (Service Hub Enterprise)

### Pipelines
- Customizable pipeline stages for deals, tickets, custom objects
- Up to 10 deal pipelines (Starter), 50 (Pro), 100 (Enterprise)
- Up to 10 ticket pipelines (Service Hub Pro)
- Up to 50 custom object pipelines (Enterprise)
- Pipeline stages can have probability percentages
- Drag-and-drop pipeline management
- Pipeline rotation rules (round-robin assignment)

### Properties
- Standard properties provided by HubSpot (hundreds pre-built)
- Custom properties: Text (single line), Textarea, Number, Date, Date/Time, Dropdown select, Multiple checkboxes, Radio select, Boolean, File (URL), Calculation, Email, Phone, Domain, etc.
- Property groups for organization
- Calculated properties (Operations Hub Pro)
- **Calculate property** (beta): server-side rollup calculations across associated records (e.g., sum deal amounts on a contact)
- Property history tracking
- Required properties for forms/creation
- **Record preview cards**: customizable side-panel cards showing key fields, associations, and activity timeline on any object record

## Step-by-Step: Creating a Custom Property
1. Navigate to Settings > Data Management > Properties
2. Click "Create Property"
3. Select object type (Contact, Company, Deal, Ticket, etc.)
4. Choose field type (Single-line text, Dropdown, Number, Date, etc.)
5. Enter label, internal name (auto-generated from label, editable)
6. Add description (internal use, shows in hover)
7. For dropdowns: add options (label + value pairs)
8. Set field grouping (which group it appears in)
9. Configure behavior: "Required" only for forms, "Read-only" prevents edits via form/import
10. Click Create

## Step-by-Step: Creating a Pipeline
1. Navigate to Settings > Data Management > Pipelines
2. Select object type (Deals, Tickets, or Custom Objects)
3. Click "Create pipeline"
4. Name the pipeline
5. Add stages: click "Add a stage"
6. For each stage: set name, deal probability (if deals), stage order (drag)
7. Configure stage-to-stage rules (optional): which stages can move forward/backward
8. Set close date required in stage (optional)

## Limits That Matter
- Contacts: Free (1,000,000), Starter (1,000,000), Pro (unlimited), Enterprise (unlimited)
- Companies: Free (100,000), Starter (500,000), Pro (1,000,000), Enterprise (unlimited)
- Deals: No hard limit (performance degrades >5M)
- Tickets: No hard limit (performance degrades >5M)
- Goals: 5,000 per sandbox, unlimited production
- Custom objects: Free (10 objects/10k records), Starter (10 objects/100k records), Pro (10 objects/10M records), Enterprise (200 objects/unlimited records)
- Custom properties per object: Free/Starter (1,000), Pro (1,000), Enterprise (10,000)
- Custom property options per dropdown: 1,000
- Pipelines for deals: Free (10), Starter (10), Pro (50), Enterprise (100)
- Pipeline stages: 30 per deal pipeline, 10 per ticket pipeline, 30 per custom object pipeline
- File uploads per property: 1 file per file-upload property
- Association labels: 50 unique labels per object pair type
- Record preview cards: 10 custom cards per object type (Enterprise)

## Use Cases
- Centralize all customer data in one place
- Track sales pipeline from lead to close
- Manage support tickets with SLAs
- Segment contacts for marketing campaigns
- Build custom CRM workflows

## Common Gotchas
- Merging contacts is irreversible (data merges into primary record)
- Property internal names cannot be changed after creation
- Deleting a property permanently removes data (30-day recycle bin for some tiers)
- Pipeline stages with deals cannot be deleted (must move deals first)
- Custom objects use API or Operations Hub to create relationships
