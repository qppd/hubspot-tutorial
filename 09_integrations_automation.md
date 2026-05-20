# 9. Integrations, Workflows & Automation

## What It Does
HubSpot connects to hundreds of external tools and provides powerful native automation (workflows). This chapter covers the integrations ecosystem, workflow automation strategies, and how to chain HubSpot + external tools for end-to-end business process automation.

## Key Features

### Native Integrations
HubSpot has built-in, no-code integrations with major platforms:

| Category | Integrations |
|---|---|
| **CRM & Data** | Salesforce, Microsoft Dynamics, Zendesk Sell, Pipedrive |
| **E-commerce** | Shopify, WooCommerce, BigCommerce, Magento (M2) |
| **Accounting** | QuickBooks, Xero, Stripe |
| **Customer Support** | Zendesk, ServiceNow, Freshdesk, Jira Service Management |
| **Communication** | Gmail, Outlook, Slack, Microsoft Teams, Zoom, Google Meet |
| **Marketing** | Mailchimp, Constant Contact, Eventbrite, Google Ads, Facebook Ads, LinkedIn Ads |
| **Productivity** | Google Sheets, Airtable, Asana, Trello, Jira, Monday.com, Notion |
| **Webinars** | GoToWebinar, Zoom Webinars, ON24 |
| **Social** | LinkedIn (Sales Navigator, Pages), Facebook, Instagram, Twitter/X, YouTube |
| **Identity** | Google SSO, Microsoft SSO, Okta, OneLogin |

### iPaaS Connectors (Third-Party Automation)
When HubSpot doesn't have a native integration, use:
- **Zapier**: 5,000+ apps — trigger workflows in HubSpot (or from HubSpot triggers to other apps)
- **Make (formerly Integromat)**: visual scenario builder with HubSpot modules
- **Workato**: enterprise iPaaS with HubSpot connector
- **Tray.io**: advanced logic and API transformation
- **Automate.io**: simpler alternative (now part of Notion)

### Workflow Automation (Deep Dive)
Workflows are the backbone of HubSpot automation. Here's a full breakdown of what's possible:

#### Workflow Triggers
- **Contact-based**: form submission, list membership change, property change, date-based, behavior event, score change
- **Company-based**: property change, list membership, date-based
- **Deal-based**: stage change, property change, deal creation, amount change
- **Ticket-based**: creation, stage change, property change, SLA breach
- **Custom object-based**: creation, property change, stage change (pipelines)
- **Goal-based**: enroll until goal met (contact becomes customer, deal closes, form submitted)
- **Manual**: enroll selected records via action
- **Time-based**: recurring, fixed date, or delay after trigger

#### Workflow Actions
1. **CRM Actions**
   - Set/create property value
   - Create/update/associate record
   - Add to/remove from static list
   - Score contact (change lead score)
   - Merge records (Pro+)
   - Delete record
   - Copy property value

2. **Communication Actions**
   - Send marketing email (must exist as draft)
   - Enroll in sales sequence
   - Create task for owner or team
   - Log note/communication
   - Create meeting (with contact)

3. **Automation Actions**
   - Delay: fixed duration, specific date, or until day/time
   - Branch: if/then based on any property or list membership
   - Goal: wait until condition is met, continue then
   - Webhook: POST data to external URL
   - Custom-coded action: Node.js/Python (Operations Hub)
   - Rotate lead (assign round-robin)

4. **Commerce Actions** (Commerce Hub)
   - Create invoice
   - Send invoice
   - Create payment link
   - Create subscription
   - Refund payment

#### Workflow Goals
- Set a goal (e.g., contact becomes customer, form submitted, deal created)
- Contacts remain enrolled until goal is met
- If goal not met by deadline, take alternative path

#### Workflow Re-enrollment
- Re-enroll when property changes
- Re-enroll on schedule (weekly/monthly)
- Limit re-enrollment count (prevent infinite loops)
- Clear re-enrollment history

#### Workflow Governance
- **Error handling**: workflow logs show failed actions, enrollment failures
- **Version history**: save and rollback workflow versions
- **Cloning**: copy workflow to reuse structure
- **Workflow folder organization**: group by campaign, team, process
- **Cooldown**: prevent workflows from running too frequently on the same record
- **Limit**: workflow execution limits based on plan

### Common Automation Patterns

#### Pattern 1: Lead Nurture
```
Trigger: Form Submission (Downloaded Ebook)
→ Delay: 1 hour
→ Branch: If lifecycle stage = Lead → Send "Welcome" email
→ Delay: 3 days
→ Branch: If email opened → Send "Case Study" email
→ Delay: 7 days
→ Branch: If email clicked → Create task for Sales: "Hot lead"
            Else → Add to "Cold Lead Nurture" list
→ Goal: Contact becomes MQL
```

#### Pattern 2: Ticket Escalation
```
Trigger: Ticket created (Priority = Urgent)
→ Action: Set Ticket Owner = Senior Support
→ Action: Send Slack notification to #urgent-support
→ Action: Set property "Escalation Time" = now
→ Delay: 4 hours
→ Branch: If ticket status != Resolved → Send email to Support Manager
→ Goal: Ticket resolved
```

#### Pattern 3: Deal → Invoice → Payment
```
Trigger: Deal stage changes to "Contract Signed"
→ Action: Create invoice from deal line items
→ Action: Send invoice to contact email
→ Action: Create payment link
→ Action: Create task for Sales: "Follow up on payment"
→ Delay: 7 days
→ Branch: If invoice not paid → Send reminder email
            Else → Move deal to "Closed Won"
→ Goal: Invoice paid
```

#### Pattern 4: Cross-Object Data Sync
```
Trigger: Contact property "Phone" changes
→ Action: Copy phone to company's "Primary Contact Phone"
→ Action: Send webhook to external API (if phone != last synced)
```

#### Pattern 5: Re-engagement Campaign
```
Trigger: Last activity date > 90 days ago
→ Action: Add to "Dormant" list
→ Branch: If dormant > 180 days → Add to "Churn Risk"
            Else → Send "We miss you" email
→ Delay: 14 days post email
→ Branch: If opened/clicked → Remove from dormant
            Else → Add to "Cold Outreach" sequence
```

### External Automation (Webhooks)
Webhooks let HubSpot talk to any external system:

**HubSpot → External:**
- Form submitted → create row in Google Sheets
- Deal closed → create invoice in QuickBooks
- Ticket created → create issue in Jira
- Contact created → add to Mailchimp list

**External → HubSpot:**
- Shopify order placed → create deal in HubSpot
- Zendesk ticket resolved → close HubSpot ticket
- Stripe payment succeeded → move deal to Closed Won
- Typeform response → create contact

### Sequence Automation
- **Trigger from workflow**: "Enroll in sequence" action in workflows
- **Auto-enroll from lists**: schedule sequences for new list members
- **Sequence steps**: email → wait → task → email → wait → call
- **Unenrollment**: reply detection, meeting booked, deal closed
- **A/B test**: test subject lines in sequences

### HubSpot + Zapier/Make Recipes
| Trigger (HubSpot) | Action (External) |
|---|---|
| New contact | Add to Mailchimp list |
| Deal stage change | Create Trello card |
| Form submission | Add row to Google Sheets |
| Ticket created | Create Jira issue |
| Deal closed won | QuickBooks invoice |
| Contact property change | Update Salesforce record |

| Trigger (External) | Action (HubSpot) |
|---|---|
| Shopify new order | Create deal |
| Typeform submission | Create/update contact |
| Stripe payment | Move deal stage |
| Calendly booking | Create meeting activity |
| Google Form entry | Create contact + enroll in workflow |

## Limits That Matter

- Workflows: Free (5), Starter (20), Pro (500), Enterprise (1,000+)
- Workflow enrollment: Free (200k lifetime), Starter (500k/yr), Pro (2M/yr), Enterprise (unlimited)
- Workflow branches: 500 per workflow
- Workflow steps: 500 per workflow
- Workflow delay max: 365 days
- Webhook calls: included in workflow limits
- Custom-coded actions: Operations Hub Pro (10), Enterprise (200)
- Sequence steps: 50 per sequence
- Sequence enrollments: 1,000 active (Pro), 2,000 active (Enterprise)
- Integration limits: vary by connector
- Zapier tasks: depends on Zapier plan (not HubSpot)
- Marketing email sends/month: Free (2k), Pro (10x contacts), Enterprise (12x contacts)

## Step-by-Step: Creating a Cross-Object Workflow

Goal: When a deal reaches "Closed Won", auto-create a ticket for onboarding.

1. Automation > Workflows > Create workflow
2. Type: Deal-based workflow
3. Enrollment trigger: Deal stage = Closed Won
4. Add action: Create record → Ticket
5. Set ticket properties:
   - Ticket name: "Onboarding: {{ dealname }}"
   - Ticket type: "Onboarding"
   - Priority: "High"
   - Pipeline: "Support Pipeline"
   - Pipeline stage: "New"
6. Associate ticket to the contact on the deal
7. Add action: Send email to deal contact — "Welcome! Your onboarding starts now."
8. Add action: Create internal Slack notification (via webhook)
9. Save and turn on

## Common Gotchas

- Workflows are evaluated at enrollment time — if a contact doesn't meet criteria at that moment, they won't retroactively enter when they later meet the criteria
- Deleting a workflow does not undo actions already taken (emails sent, properties set)
- Workflow webhooks have a 10-second timeout — external endpoints must respond fast
- Sequences with too many steps hurt deliverability (stick to 3-6 steps)
- Reply detection in sequences uses email headers — not 100% reliable (Gmail's threading can interfere)
- Zapier/Make rate limits apply on their side — HubSpot sends at its own rate
- Native integrations (Salesforce sync, QuickBooks) may have field mapping limitations that need manual override
- Workflow branches evaluate top-down — reorder branches to put most common path first for performance
- Custom-coded action logs are retained for 30 days only
- API integrations should use Private App tokens (scoped) rather than shared API keys