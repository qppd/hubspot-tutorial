# 9. Integrations & Automation — Complete Tutorial

## Table of Contents
1. [Introduction to Integrations](#introduction-to-integrations)
2. [Native HubSpot Integrations — Complete Guide](#native-hubspot-integrations--complete-guide)
3. [iPaaS Connections (Zapier, Make, Workato) — Complete Guide](#ipaas-connections-zapier-make-workato--complete-guide)
4. [Advanced Workflow Patterns — Complete Guide](#advanced-workflow-patterns--complete-guide)
5. [Sequence Automation Patterns — Complete Guide](#sequence-automation-patterns--complete-guide)
6. [Cross-Hub Automation — Complete Guide](#cross-hub-automation--complete-guide)
7. [Custom Integration Architecture — Complete Guide](#custom-integration-architecture--complete-guide)
8. [Integration Testing & Monitoring — Complete Guide](#integration-testing--monitoring--complete-guide)
9. [Limits That Matter](#limits-that-matter)
10. [Common Gotchas](#common-gotchas)
11. [Use Cases](#use-cases)

---

## Introduction to Integrations

HubSpot connects with 1,000+ apps through native integrations, iPaaS platforms (Zapier, Make, Workato), and custom API integrations. This chapter covers how to connect, automate, and build integrations that make HubSpot the center of your tech stack.

### Integration Types

| Type | Complexity | Maintenance | Best For |
|------|-----------|-------------|----------|
| **Native integration** | Low | Low (HubSpot manages) | Popular apps (Salesforce, Shopify, Slack) |
| **iPaaS (Zapier/Make/Workato)** | Low-Medium | Medium | Rapid prototyping, simple automations |
| **Custom API integration** | High | High | Complex, unique, or high-volume needs |
| **Operations Hub Data Sync** | Medium | Medium | Bi-directional data sync with field mapping |

---

## Native HubSpot Integrations — Complete Guide

### Email Integrations

**Gmail / Google Workspace**:
- Two-way calendar sync (meetings → Google Calendar)
- Email tracking (opens, clicks, replies)
- Side panel shows contact info while composing
- One-click contact creation from email
- Meeting scheduling (check calendar availability)

**Outlook / Office 365**:
- Two-way calendar sync
- Email tracking (opens + clicks)
- HubSpot add-in for Outlook (desktop + web)
- Quick contact creation
- Meeting scheduling

**Connecting your inbox**:
1. **Settings** > **Integrations** > **Email**
2. Choose Gmail or Outlook
3. Authenticate with OAuth 2.0
4. Configure sync settings (tracking, signature, history import)

### Calendar Integrations

**Google Calendar**:
- Automatic meeting logging
- Availability for meeting links
- Two-way sync (meetings created in either system)

**Office 365 Calendar**:
- Same as Google Calendar

**Zoom / Google Meet / Microsoft Teams**:
- Auto-generate meeting links in HubSpot meeting links
- Log meetings in CRM
- Sync attendance data

### Communication Integrations

**Slack**:
- Notifications: New deal, high-priority ticket, contact form submission
- Action: Create contact from Slack message, update deal, log note
- Setup: /hubspot slash command integration
- Channels: Send different notifications to different channels
- Threads: Full conversation history linked to CRM

**WhatsApp**:
- Two-way messaging from conversations inbox
- Template-based messages (for approvals)
- Rich media (images, documents)
- Contact timeline logging

**Facebook Messenger**:
- Inbox integration for conversations
- Chatbot routing
- Message templates
- Contact timeline logging

### CRM Integrations

**Salesforce**:
- Bi-directional sync of Contacts, Companies, Deals, Tasks (with Operations Hub)
- Field mapping with transformations
- Conflict resolution rules
- Sync history and audit trail
- **Without Operations Hub**: One-way sync via Salesforce Connector

**Shopify**:
- Order sync: Shopify orders → HubSpot deals
- Customer sync: Shopify customers → HubSpot contacts
- Product sync: Shopify products → HubSpot products
- Abandoned cart tracking
- Revenue attribution
- **Direction**: One-way (Shopify → HubSpot)

**LinkedIn Sales Navigator**:
- Profile sync (LinkedIn ↔ HubSpot)
- Activity sync (InMail, profile views, saves)
- Save to CRM (one-click from LinkedIn)
- Icebreakers and conversation starters
- Requires LinkedIn Sales Navigator seat per user

### Content Integrations

**WordPress**:
- HubSpot tracking code (traffic, form tracking)
- HubSpot forms plugin
- HubSpot pop-up forms
- Contact sync
- Requires HubSpot plugin for WordPress

**Google Analytics 4**:
- Import GA4 data to HubSpot reports
- Traffic source integration
- Goal completion tracking
- Requires GA4 property connection

### Productivity Integrations

**Asana / Trello / Monday.com**:
- Create tasks from HubSpot workflows
- Sync deal updates to project boards
- Two-way task status updates

**DocuSign / PandaDoc**:
- E-signature integration for quotes
- Document status tracking in CRM
- Automated quote-to-sign flow

---

## iPaaS Connections (Zapier, Make, Workato)

### Zapier

Zapier connects HubSpot to 5,000+ apps through triggers and actions.

**Common Zaps**:

```
Trigger (HubSpot) → Action (External App):
- New contact → Add to Mailchimp list
- New deal (closed won) → Create invoice in QuickBooks
- New ticket (high priority) → Create Jira issue
- New form submission → Add row to Google Sheets

Trigger (External App) → Action (HubSpot):
- New Typeform submission → Create contact in HubSpot
- New Stripe charge → Create deal in HubSpot
- New Calendly booking → Log meeting in HubSpot
- New WooCommerce order → Create contact + deal in HubSpot
```

**HubSpot Triggers in Zapier**:
- New Contact
- New Deal
- New Ticket
- New Company
- Updated Contact
- Updated Deal
- Updated Company
- New Form Submission
- New Task
- New Meeting
- New Company
- Updated Deal Stage

**HubSpot Actions in Zapier**:
- Create/Update Contact
- Create/Update Deal
- Create/Update Ticket
- Create/Update Company
- Create Engagement (note, task, meeting, call, email)
- Create/Lookup Contact
- Search Contacts/Deals/Companies
- Add/Remove from List
- Enroll in Workflow
- Enroll in Sequence

**Zapier Best Practices**:
1. Use filters to avoid unnecessary runs (e.g., only new contacts from specific forms)
2. Turn on Zap History to monitor failures
3. Use delays to batch multiple updates
4. Watch for HubSpot API rate limits (100 req/10s)
5. Test with sample data before activating

### Make (formerly Integromat)

Make offers more complex automation scenarios than Zapier:

**Make Advantages over Zapier**:
- **Visual scenario builder**: See data flow visually
- **Complex logic**: Multiple branches, aggregators, iterators
- **Error handling**: Advanced retry, rollback, error routing
- **Data transformation**: Built-in text, math, date functions
- **Webhook support**: Incoming and outgoing webhooks
- **Better pricing**: More operations per month for the price

**Common Make Scenarios**:

```
1. Lead enrichment pipeline:
   New HubSpot contact → Query Clearbit by email → 
   Update contact with enriched data → If company data found, 
     search for existing company → Create or associate

2. Multi-channel follow-up:
   New deal created → Check amount → 
   If >$50k: Send Slack to executive team + Create high-priority task + 
   Update deal property "Enterprise Deal"
   If <$50k: Enroll in standard sequence

3. E-commerce fulfillment:
   New Shopify order → Create HubSpot deal → 
   Check inventory (via API) → If in stock, send to fulfillment system → 
   If out of stock, create ticket for procurement
```

### Workato

Workato is enterprise-grade iPaaS designed for complex integrations:

**Workato for HubSpot**:
- **Advanced field transformations**: Map complex data structures
- **Recipe SDK**: Build custom connectors
- **On-premise agents**: Connect to local databases and systems
- **Governance**: Audit trails, role-based access, approval flows
- **Enterprise SLAs**: Guaranteed uptime and support

**When to choose Workato over Zapier/Make**:
- High volume (10,000+ operations per month)
- Complex data transformations needed
- Compliance requirements (SOC 2, HIPAA, GDPR)
- On-premise system connectivity
- Enterprise support requirements

---

## Advanced Workflow Patterns

### Pattern 1: Multi-Branch Orchestration

```
Trigger: New deal created

Branch 1: Deal amount > $50,000
  → Notify VP of Sales (Slack + Email)
  → Assign to Enterprise sales team
  → Add to "Enterprise Deals" dashboard
  → Create onboarding task for Customer Success

Branch 2: Deal amount between $10,000-$50,000
  → Notify regional manager
  → Assign to standard sales team
  → Enroll in "Standard Sales Sequence"
  → Set property "Deal Tier" = "Standard"

Branch 3: Deal amount < $10,000
  → Send auto-quote via payment link
  → Set property "Self-serve eligible" = true
  → If not closed in 7 days → Assign to SDR

Branch 4: No amount entered
  → Create task: "Update deal amount before proceeding"
  → Set reminder in 2 days
```

### Pattern 2: Goal-Based with Escalation

```
Trigger: Contact fills out "Request Demo" form

Actions:
  1. Set lifecycle stage = "MQL"
  2. Enroll in "Demo Follow-up" sequence
  3. Set property "Demo requested" = true

Goal: Meeting booked (from sequence)

Expiration: 14 days without meeting booked
  → Escalation notifications:
    → Day 7: Reminder to SDR
    → Day 10: Notify SDR manager
    → Day 14: Escalate to sales director
    → Day 14: Set lifecycle = "MQL (cold)"
    → Day 14: Move to "Cold Lead Nurture" workflow
```

### Pattern 3: Data Quality Pipeline

```
Trigger: Contact created OR updated

Branch 1: Email is invalid (doesn't contain @)
  → Set property "Email Valid" = false
  → Create task: "Verify email address"
  → Notify contact owner

Branch 2: Phone has non-standard formatting
  → Format to standard: (555) 123-4567
  → Set property "Phone Cleaned" = true

Branch 3: Missing company name
  → Extract domain from email
  → Search for company by domain
  → If found: associate to company
  → If not found: create new company
  
Branch 4: Duplicate check (email matches existing contact)
  → Flag as potential duplicate
  → Merge into primary record (if high confidence)
  → Create task for manual review (if low confidence)

Always:
  → Standardize state abbreviations
  → Capitalize name fields
  → Lowercase email
```

### Pattern 4: Revenue Recognition Automation

```
Trigger: Deal stage = "Closed Won"

Actions:
  1. Set lifecycle stage = "Customer"
  2. Create invoice in QuickBooks (via webhook/custom-coded action)
  3. Calculate commission (calculated property: amount * commission_rate%)
  4. Create commission record in Commission custom object
  5. If recurring revenue: create subscription record
  6. Notify fulfillment team of new customer
  7. Create onboarding ticket
  8. Send welcome email series (enroll in automation)
  9. Update forecast to "Closed Won"
  10. Send Slack notification: "🎉 New deal closed: $X (Client Name)"
```

---

## Sequence Automation Patterns

### Pattern 1: Triggered Sequence Enrollment

```
Trigger: Form submission (e.g., "Download Whitepaper")

Actions in workflow:
  1. Send immediate: Thank-you email with download link
  2. 1 day later: Enroll in "Post-download Nurture" sequence
     (Sequence steps: Day 2, 5, 9 — related content, case study, demo offer)
  3. Monitor sequence progress

If sequence goal met (meeting booked):
  → Exit sequence
  → Create task for sales rep: "Follow up on {product} demo"

If sequence completed without goal:
  → Add to "Long-term Nurture" list
  → Re-enroll in 90 days with different content
```

### Pattern 2: Lead Re-engagement Sequence

```
Trigger: No activity for 90 days (property: last_activity_date < 90 days ago)

Actions:
  1. Send re-engagement email: "We haven't heard from you..."
  2. Delay 7 days

Branch: If contact opened the re-engagement email
  → Re-enroll in standard nurture sequence
  → Set property "Re-engaged" = true
  → Send personalized follow-up

Branch: If contact did NOT open (or bounced)
  → Try one more email with different subject
  → Delay 7 days
  → If still no open: Set lifecycle = "Unengaged"
  → Add to "Cold List" (suppressed from future sends)
```

### Pattern 3: Post-Purchase Upsell Sequence

```
Trigger: Deal stage = "Closed Won" (initial purchase)

Actions:
  1. Send onboarding sequence for purchased product
  2. Monitor product usage (if available via API/integration)

Branch: High usage (logged in 10+ times in first month)
  → Day 30: Enroll in upsell sequence for premium features
  → Sequence includes: Success story → Feature highlight → Upgrade offer

Branch: Low usage (logged in < 5 times)
  → Day 14: Schedule onboarding call with CS team
  → Day 21: Send training tips
  → Day 30: Enroll in re-engagement
```

---

## Cross-Hub Automation

### Marketing → Sales Handoff

```
Trigger (Marketing): Lead score reaches MQL threshold (50+)

Actions:
  1. Set lifecycle stage = "MQL"
  2. Enroll in "New MQL" sequence (Sales Hub)
  3. Create task for SDR: "Follow up with MQL — {contact.firstname} {contact.lastname}"
  4. Notify SDR via Slack
  5. Add to "Active Leads" dashboard (Marketing → Sales shared)

If SDR books a meeting (Sales Hub):
  → Set lifecycle = "SQL"
  → Enroll in "Demo Preparation" workflow (Marketing)
  → Send personalized demo email with relevant case studies

If SDR doesn't respond in 48 hours:
  → Escalate: Notify SDR manager (Service Hub: high-priority ticket)
  → Reassign to backup SDR
```

### Sales → Service Handoff

```
Trigger (Sales): Deal stage = "Closed Won"

Actions:
  1. Set lifecycle = "Customer"
  2. Create ticket in Service Hub: "Customer Onboarding"
     (Type: Onboarding, Priority: High)
  3. Assign onboarding ticket to CS team
  4. Enroll customer in "Welcome" series (Marketing Hub)
  5. Create customer health score baseline (Operations Hub)
  6. Set next renewal date (calculated property)
```

### Service → Sales (Upsell Trigger)

```
Trigger (Service): CSAT score = 5 (very satisfied) AND High product usage

Actions:
  1. Create task for Account Manager: "Upsell opportunity — satisfied customer"
  2. Add to "Expansion Candidates" list (shared Sales + Success)
  3. Enroll in "Postitive Feedback Upsell" sequence (Sales Hub)
  4. Set property "Upsell Qualified" = true
```

---

## Custom Integration Architecture

### Webhook-Based Integration

Best for: Real-time event processing

```
External System ──webhook──→ HubSpot
   (POST /webhooks/v3/subscriptions)
   
HubSpot ──webhook──→ External System
   (POST to your endpoint when events occur)
```

**Your server handles**:
1. Receives webhook from HubSpot
2. Verifies HMAC signature
3. Processes event (sync, enrich, transform)
4. Responds with 200 OK

### Scheduled Sync Integration

Best for: Daily data exports/imports

```
HubSpot API ──REST──→ Your Server (cron job, daily)
   (Fetch updated records, process, store)

Your Server ──REST──→ HubSpot API
   (Push updates back)
```

### Real-Time Bidirectional Sync

Best for: Keeping two systems in sync continuously

```
HubSpot webhook → Your Server
    ↓
Your Server transforms data → updates External System
    ↓
External System webhook → Your Server
    ↓
Your Server transforms data → updates HubSpot
```

**Conflict resolution**: When both systems update the same record simultaneously:
1. Timestamp comparison (latest wins)
2. Field-level merging (different fields updated in each system)
3. Human review queue (conflicts that can't be auto-resolved)

---

## Integration Testing & Monitoring

### Testing Strategies

**Sandbox testing**:
1. Create a developer sandbox
2. Set up integration in sandbox first
3. Test with sample data
4. Verify data flows correctly
5. Test error scenarios (network failure, invalid data)

**Staging environment**:
- Use a separate HubSpot portal for UAT
- Operations Hub Data Sync can run in staging mode
- Test with simulated production data volumes

**Monitoring**:

| Metric | What to Watch | Alert Threshold |
|--------|--------------|-----------------|
| API error rate | 4xx and 5xx responses | > 5% of requests |
| API latency | Average response time | > 2 seconds |
| Sync lag | Time since last successful sync | > 1 hour |
| Failed webhooks | Expired retries | > 3 in a day |
| Data quality | Records failing validation | > 1% of records |
| Rate limit hits | 429 responses | > 10% of requests |

---

## Limits That Matter

| Resource | Limit | Notes |
|----------|-------|-------|
| Native integration connections | 100+ (varies) | Most connections are unlimited |
| API rate limit | 100 req/10s | Per app, not per user |
| API daily limit | 250k-1M+ | Depends on plan |
| Webhook subscriptions | 100 per portal | Across all event types |
| Zapier tasks | Varies by plan | From 100 to 50k+/mo |
| Make operations | Varies by plan | From 1k to 10k+/mo |
| Workato recipes | Varies by plan | From 5 to unlimited |
| Custom-coded actions | 10 Pro, Unlimited Enterprise | Workflow actions |
| Programmable automation | 10 Pro | Additional cost for more |

---

## Common Gotchas

### 1. Webhook Idempotency
Webhooks can be delivered more than once. Always design your integration to be idempotent — processing the same event twice should have the same result as processing it once.

### 2. API Rate Limit Handling
Your integration should handle 429 (rate limit) responses gracefully. Implement exponential backoff: first retry in 1s, then 2s, 4s, 8s, up to a maximum of 60s.

### 3. Zapier Error Handling
Zapier will retry failed tasks up to 3 times. After that, the task is marked as "error" and skipped. Monitor Zapier's task history for errors.

### 4. Field Mapping Discrepancies
HubSpot and your external system may use different field names, formats, or data types. Always create a field mapping document before building the integration.

### 5. Data Volume Surprises
A "simple" integration can quickly overwhelm API limits when importing large datasets. Always add rate limiting and throttle controls to your integration code.

### 6. Authentication Expiry
OAuth tokens expire. Service account credentials change. Build monitoring for authentication failures — a disconnected integration running silently can cause data inconsistency.

### 7. Circular Syncs
Be careful when setting up bi-directional sync. If System A updates a field, which triggers System B to update the same field, which triggers System A again... you have a circular sync. Use a sync tag or timestamp to prevent loops.