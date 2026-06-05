# 9. Integrations, Workflows & Automation

## What It Does
HubSpot connects to hundreds of external tools and provides powerful native automation (workflows). This chapter covers the integrations ecosystem, workflow automation strategies, and how to chain HubSpot + external tools for end-to-end business process automation.

## Key Features

### Native Integrations
HubSpot has built-in, no-code integrations with major platforms:

| Category | Integrations |
|---|---|
| **CRM & Data** | Salesforce, Microsoft Dynamics 365, Zendesk Sell, Pipedrive |
| **E-commerce** | Shopify, WooCommerce, BigCommerce, Magento |
| **Accounting** | QuickBooks Online, Xero, Stripe |
| **Customer Support** | Zendesk, ServiceNow, Freshdesk, Jira Service Management |
| **Communication** | Gmail, Outlook, Slack, Microsoft Teams, Zoom, Google Meet |
| **Marketing** | Mailchimp, Constant Contact, Eventbrite, Google Ads, Facebook Ads, LinkedIn Ads, TikTok Ads |
| **Productivity** | Google Sheets, Airtable, Asana, Trello, Jira, Monday.com, Notion |
| **Webinars** | GoToWebinar, Zoom Webinars, ON24 |
| **Social** | LinkedIn (Sales Navigator, Pages), Facebook, Instagram, Twitter/X, YouTube |
| **Identity/SSO** | Google SSO, Microsoft SSO, Okta, OneLogin |

### iPaaS Connectors (Third-Party Automation)
When HubSpot doesn't have a native integration:
- **Zapier**: 5,000+ apps — HubSpot triggers and actions on both sides
- **Make (formerly Integromat)**: visual scenario builder with deep HubSpot modules
- **Workato**: enterprise iPaaS with HubSpot connector (supports custom object sync)
- **Tray.io**: advanced logic, API transformation, and custom connectors
- **Automate.io**: simpler alternative (now part of Notion)

### Breeze AI Automation Agents (2025)
HubSpot's Breeze AI includes automation agents that can design, build, and manage workflows with natural language:
- **Breeze Copilot for workflows**: describe what you want ("Send a welcome email when a new contact fills the demo form, then create a task for sales if they click the CTA") and Breeze builds the workflow for you
- **AI-recommended automation**: Breeze analyzes your CRM patterns and suggests workflows you haven't created yet (e.g., "I notice 30% of form submissions don't get a follow-up — create a lead nurture workflow?")
- **Natural language triggers**: "When a deal worth over $10,000 reaches Closed Won, create an onboarding ticket and Slack the CS team"
- **Workflow error detection**: Breeze flags stuck workflows, high error rates, and re-enrollment loops proactively

### Workflow Automation (Deep Dive)
Workflows are the backbone of HubSpot automation. Here's a full breakdown:

#### Workflow Triggers
- **Contact-based**: form submission, list membership change, property change, date-based, behavior event, score change
- **Company-based**: property change, list membership, date-based
- **Deal-based**: stage change, property change, deal creation, amount change, deal owner change
- **Ticket-based**: creation, stage change, property change, SLA breach, ticket owner change
- **Custom object-based**: creation, property change, stage change (pipelines)
- **Goal-based**: enroll until goal met (contact becomes customer, deal closes, form submitted)
- **Manual**: enroll selected records via action
- **Time-based**: recurring (weekly/monthly), fixed date, or delay after trigger

#### Workflow Actions
1. **CRM Actions**
   - Set/create property value
   - Create/update/associate record
   - Add to/remove from static list
   - Score contact (change lead score)
   - Merge records (Pro+)
   - Delete record
   - Copy property value
   - Rotate lead / assign owner

2. **Communication Actions**
   - Send marketing email (must exist as draft in Marketing Hub)
   - Enroll in sales sequence
   - Create task for owner or team
   - Log note/communication
   - Create meeting (with contact)
   - Send internal email notification

3. **Automation Actions**
   - Delay: fixed duration, specific date, or until day/time
   - Branch: if/then based on any property, list membership, or calculation
   - Goal: wait until condition is met, continue on success or timeout
   - Webhook: POST data to external URL (JSON, form-encoded, or XML)
   - Custom-coded action: Node.js or Python (Operations Hub)
   - Rotate lead (round-robin assignment)

4. **Commerce Actions** (Commerce Hub)
   - Create invoice
   - Send invoice
   - Create payment link
   - Create subscription
   - Refund payment
   - Cancel subscription

#### Workflow Goals
- Set a goal (e.g., contact becomes customer, form submitted, deal created)
- Contacts remain enrolled until goal is met
- If goal not met by deadline, take alternative path (timeout branch)

#### Workflow Re-enrollment
- Re-enroll when property changes
- Re-enroll on schedule (weekly/monthly)
- Limit re-enrollment count (prevents infinite loops)
- Clear re-enrollment history

#### Workflow Governance
- **Error handling**: workflow logs show failed actions, enrollment failures with details
- **Version history**: save and rollback workflow versions
- **Cloning**: copy workflow to reuse structure across campaigns
- **Folder organization**: group by campaign, team, or process
- **Cooldown**: prevent workflows from running too frequently on the same record
- **Execution limits**: enrollment and action limits based on plan

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

#### Pattern 6: Breeze AI Agent — Automated Lead Qualification
```
Trigger: Form submission (any form)
→ Breeze AI Agent: Analyze contact intent, company size, job title
→ Branch: High-fit → Add to "Hot Lead" list, assign to senior rep
→ Branch: Medium-fit → Enroll in nurture sequence
→ Branch: Low-fit → Add to "Long-term nurture" list
→ Action: Log AI scoring summary in contact note
```

### External Automation (Webhooks)
Webhooks let HubSpot talk to any external system:

**HubSpot → External:**
- Form submitted → create row in Google Sheets
- Deal closed → create invoice in QuickBooks
- Ticket created → create issue in Jira
- Contact created → add to Mailchimp list
- Meeting booked → add to Salesforce campaign

**External → HubSpot:**
- Shopify order placed → create deal in HubSpot
- Zendesk ticket resolved → close HubSpot ticket
- Stripe payment succeeded → move deal to Closed Won
- Typeform response → create/update contact
- Calendly booking → create meeting activity

### Sequence Automation
- **Trigger from workflow**: "Enroll in sequence" action in workflows
- **Auto-enroll from lists**: schedule sequences for new list members
- **Sequence steps**: email → wait → task → email → wait → call
- **Unenrollment triggers**: reply detection, meeting booked, deal stage change
- **A/B test subject lines**: test variations within sequences
- **Breeze AI sequence optimization**: AI suggests optimal send times, email content, and follow-up intervals based on historical performance (Enterprise)

### HubSpot + Zapier/Make Recipes

| Trigger (HubSpot) | Action (External) |
|---|---|
| New contact created | Add to Mailchimp list |
| Deal stage changed | Create Trello card |
| Form submitted | Add row to Google Sheets |
| Ticket created | Create Jira issue |
| Deal closed won | Create QuickBooks invoice |
| Contact property changed | Update Salesforce record |

| Trigger (External) | Action (HubSpot) |
|---|---|
| Shopify new order | Create deal |
| Typeform submitted | Create/update contact |
| Stripe payment received | Move deal stage |
| Calendly booking | Create meeting activity |
| Google Form entry | Create contact + enroll in workflow |

### Workflow Templates (Built-in)
HubSpot provides pre-built workflow templates for common scenarios:
- Lead nurturing (5-email drip)
- Welcome series for new contacts
- Abandoned cart recovery (Commerce Hub)
- Ticket auto-response and routing
- Deal stage progression notifications
- Re-engagement for dormant contacts
- Invoice follow-up and dunning

## Limits That Matter

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Workflows | 5 | 20 | 500 | 1,000+ |
| Workflow enrollment | 200k lifetime | 500k/yr | 2M/yr | Unlimited |
| Workflow branches | 500 | 500 | 500 | 500 |
| Workflow steps | 500 | 500 | 500 | 500 |
| Workflow delay max | 365 days | 365 days | 365 days | 365 days |
| Webhook calls | Included | Included | Included | Included |
| Custom-coded actions | — | — | 10 (Ops Hub) | 200 (Ops Hub) |
| Sequence steps | 5 | 10 | 50 | 50 |
| Sequence enrollments (active) | 50 | 250 | 1k/user | 2k/user |
| Integration limits | Vary by connector | Vary | Vary | Vary |
| Zapier tasks | Depends on Zapier plan | Depends | Depends | Depends |

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
- Native integrations may have field mapping limitations that need manual override
- Workflow branches evaluate top-down — put most common path first for performance
- Custom-coded action logs are retained for 30 days only
- API integrations should use Private App tokens (scoped) rather than shared API keys
- Breeze AI workflow generation is a starting point — always review and test before activating
- Workflow enrollment counts include re-enrollments — monitor your plan's annual limit