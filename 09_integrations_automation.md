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

---

## Integration Case Studies

### Case Study 1: HubSpot + Salesforce Bi-Directional Sync

**Scenario**: A mid-market B2B company uses HubSpot for marketing (forms, emails, automation) and Salesforce for sales (pipeline, forecasting, reporting). They need data to flow both ways in near-real-time while maintaining data quality.

**Challenge**: Marketing creates MQLs in HubSpot with enrichment data. Sales needs those contacts in Salesforce with proper lead status. When deals close in Salesforce, HubSpot needs to update lifecycle stages and trigger post-sale workflows.

**Solution using Operations Hub Data Sync**:
1. Connect HubSpot to Salesforce via Operations Hub
2. Configure bi-directional Contact sync:
   - HubSpot → Salesforce: New contacts, updated fields (lead score, lifecycle stage, Breeze enrichment)
   - Salesforce → HubSpot: Lead status updates, conversion to contact, assignment changes
3. Field mapping:
   | HubSpot Field | Salesforce Field | Direction |
   |--------------|-----------------|-----------|
   | Email | Email | Both |
   | First Name | FirstName | Both |
   | Last Name | LastName | Both |
   | Lead Score | Lead_Score__c | HubSpot → Salesforce |
   | Lifecycle Stage | Lifecycle_Stage__c | HubSpot → Salesforce |
   | Lead Status | Status | Salesforce → HubSpot |
   | Owner | OwnerId | Salesforce → HubSpot |
4. Conflict resolution: "Most recent wins" for all fields
5. Sync schedule: Continuous (near-real-time)

**Result**: Marketing can create a lead in HubSpot → it appears in Salesforce within 2-5 minutes. Sales can update Lead Status in Salesforce → HubSpot workflow automatically handles the lifecycle stage change.

### Case Study 2: E-commerce Integration with Shopify

**Scenario**: An e-commerce brand uses Shopify for the online store and HubSpot for CRM, email marketing, and customer support. They need order data, customer information, and abandoned cart events in HubSpot.

**Challenge**: Orders placed in Shopify need to appear as deals in HubSpot with correct line items. Customer profiles need to sync with purchase history. Abandoned carts need to trigger email sequences.

**Solution**:
1. **Native Shopify integration**: Connect Shopify store to HubSpot
2. **Order sync**: 
   - New Shopify order → New Deal in HubSpot (pipeline: E-commerce)
   - Products become line items on the deal
   - Deal amount = order total
3. **Customer sync**:
   - Shopify customer → HubSpot contact (if email matches, update)
   - Contact properties: Total orders, Last order date, Average order value, Customer lifetime value (calculated properties)
4. **Abandoned cart workflow**:
   - Trigger: "Cart abandoned" event from Shopify
   - Actions: 
     - Wait 1 hour → Send "Did you forget something?" email
     - Wait 24 hours → Send "Free shipping" offer
     - Wait 72 hours → If no purchase, add to retargeting list
5. **Post-purchase workflow**:
   - Trigger: Deal stage = "Closed Won" (paid)
   - Actions:
     - Send order confirmation email
     - Wait 7 days → Send "How's your purchase?" email + review request
     - Wait 30 days → Send cross-sell recommendation

### Case Study 3: HubSpot + Slack + Jira for Service Teams

**Scenario**: A SaaS company uses HubSpot for customer support tickets, Slack for team communication, and Jira for engineering bug tracking. High-priority bugs need to create Jira issues automatically while keeping everyone in the loop on Slack.

**Solution**:
1. **Slack integration**: Connect HubSpot to Slack
2. **Jira integration**: Connect via Zapier or custom webhook
3. **HubSpot Workflow — Urgent Bug Ticket**:
   - Trigger: Ticket type = "Bug" AND priority = "Urgent"
   - Action 1: Send Slack webhook to #bugs channel with ticket details
   - Action 2: Trigger webhook to Jira API → Create Jira issue
   - Action 3: Create internal note on ticket: "Jira issue TICKET-123 created"
   - Action 4: Update ticket property "Engineering Ticket" = Jira issue URL
4. **Slack message format**:
   ```
   🐛 URGENT BUG REPORT
   
   Ticket: HS-4521
   Contact: Jane Doe (jane@acmecorp.com)
   Summary: Login page returns 500 error on Safari
   Priority: Urgent
   
   🔗 [View Ticket in HubSpot](link)
   🎫 [Jira Issue: TICKET-123](link)
   ```
5. **Jira issue auto-populated fields**:
   - Summary: From ticket name
   - Description: Full ticket body + contact info
   - Priority: Critical
   - Labels: hubspot-urgent
   - Custom field: HubSpot link back to ticket

**Benefits**: Engineers stay in Jira, support stays in HubSpot, but urgent bugs get seamless handoff. No manual copy-paste, no dropped tickets.

---

## Integration Architecture Patterns

### Pattern 1: Event-Driven Architecture (Webhook-Centric)

Best for: Real-time data synchronization, immediate reactions to CRM events

```
HubSpot Event → Webhook → Event Bus (e.g., AWS EventBridge, RabbitMQ) 
                          → Multiple Consumers:
                            → Customer Data Platform
                            → Analytics Pipeline
                            → Email Service Provider
                            → Notification System (Slack, SMS)
                            → Data Warehouse (via streaming)
```

**Advantages**: Decoupled, scalable, fault-tolerant. Each consumer processes independently.
**Disadvantages**: Event ordering not guaranteed. Eventual consistency.

### Pattern 2: Batch/Scheduled Architecture

Best for: Daily reporting, nightly data syncs, ETL operations

```
HubSpot API → Cron Job (daily at 2 AM) → Extract
                                       → Transform (clean, normalize, enrich)
                                       → Load to Data Warehouse
                                       → Generate Reports
                                       → Send Summary Email
```

**Advantages**: Simple to implement, easy to debug, predictable load.
**Disadvantages**: Not real-time, daily cycles mean stale data mid-day.

### Pattern 3: Two-Phase Commission

Best for: Critical data that must be accurate (financials, inventory, compliance)

```
Phase 1: HubSpot → Staging System (validate, transform, map)
Phase 2: Human Approval → Commit to Production System
         OR Auto-approve if confidence > 95%
```

**Advantages**: Prevents bad data from propagating. Audit trail for compliance.
**Disadvantages**: Slower, requires human oversight, more complex.

---

## Webhook Implementation Reference

### Retry & Error Handling

```python
import time
import logging

def handle_webhook(event_type, payload):
    """Process a HubSpot webhook with proper error handling and retry."""
    max_retries = 3
    for attempt in range(max_retries):
        try:
            if event_type == "contact.creation":
                process_new_contact(payload)
            elif event_type == "deal.stageChange":
                process_deal_stage_change(payload)
            elif event_type == "ticket.creation":
                process_new_ticket(payload)
            else:
                logging.warning(f"Unknown event type: {event_type}")
            
            return {"status": "success"}
            
        except TemporaryError as e:
            logging.warning(f"Temporary error (attempt {attempt + 1}): {e}")
            if attempt < max_retries - 1:
                time.sleep(2 ** attempt)  # Exponential backoff: 1s, 2s, 4s
            else:
                logging.error(f"Max retries reached for event: {payload.get('objectId')}")
                return {"status": "failed", "reason": "max_retries"}
                
        except PermanentError as e:
            logging.error(f"Permanent error: {e}")
            # Don't retry permanent errors (invalid data, missing records)
            return {"status": "failed", "reason": str(e)}
```

### Webhook Server Example (Flask)

```python
from flask import Flask, request, jsonify
import hmac
import hashlib
import json

app = Flask(__name__)
WEBHOOK_SECRET = "your-hubspot-webhook-secret"

@app.route("/webhooks/hubspot", methods=["POST"])
def hubspot_webhook():
    # 1. Verify signature
    signature = request.headers.get("X-HubSpot-Signature-v3")
    timestamp = request.headers.get("X-HubSpot-Request-Timestamp")
    body = request.data.decode("utf-8")
    
    expected_sig = hmac.new(
        WEBHOOK_SECRET.encode("utf-8"),
        (body + timestamp).encode("utf-8"),
        hashlib.sha256
    ).hexdigest()
    
    if not hmac.compare_digest(signature, expected_sig):
        return jsonify({"error": "Invalid signature"}), 401
    
    # 2. Check timestamp freshness (prevent replay attacks)
    import time
    now = int(time.time())
    if abs(now - int(timestamp)) > 300:  # 5 minute window
        return jsonify({"error": "Stale timestamp"}), 401
    
    # 3. Process events
    events = request.json
    results = []
    
    for event in events:
        result = handle_webhook(
            event.get("subscriptionType"),
            event
        )
        results.append(result)
    
    # 4. Always return 200 OK to acknowledge receipt
    return jsonify({"results": results}), 200

if __name__ == "__main__":
    app.run(port=8080)
```

### Webhook Batching

HubSpot delivers webhooks in batches (up to 100 events per batch). Handle this correctly:

```python
def process_webhook_batch(events):
    """Process a batch of webhook events efficiently."""
    
    # Group by event type for efficient processing
    grouped = {}
    for event in events:
        event_type = event["subscriptionType"]
        if event_type not in grouped:
            grouped[event_type] = []
        grouped[event_type].append(event)
    
    # Process each group
    for event_type, type_events in grouped.items():
        if event_type == "contact.creation":
            # Batch API call - get all these contacts at once
            contact_ids = [e["objectId"] for e in type_events]
            batch_create_contacts(contact_ids)
            
        elif event_type == "deal.stageChange":
            # Process each deal stage change
            for event in type_events:
                process_stage_change(
                    event["objectId"], 
                    event["propertyValue"]
                )

---

## Integrations Tutorials — Advanced

### Tutorial 4: Salesforce-HubSpot Sync Architecture

**Goal**: Design a bidirectional sync between HubSpot and Salesforce that keeps both systems consistent without data loss.

**Phase 1: Determine Sync Strategy**

**Option A: HubSpot Operations Hub Data Sync** (Best for most teams)
1. **Settings** > **Integrations** > **Data Sync** > Add connection
2. Select Salesforce
3. Choose sync direction per object:
   - Contacts: Bidirectional (updates from either system sync to the other)
   - Companies: Salesforce → HubSpot (Salesforce is source of truth)
   - Deals: HubSpot → Salesforce (HubSpot is source of truth)
   - Tasks: HubSpot → Salesforce
4. Configure field mapping:
   - HubSpot `email` ↔ Salesforce `Email`
   - HubSpot `firstname` ↔ Salesforce `FirstName`
   - HubSpot `lastname` ↔ Salesforce `LastName`
   - HubSpot `phone` ↔ Salesforce `Phone`
   - Custom field: HubSpot `lead_score` → Salesforce `Lead_Score__c`
5. Set conflict resolution: Last updated wins (with audit log)

**Option B: Custom Middleware** (Best for complex mapping needs)
1. Build a middleware service (Node.js or Python)
2. Receive webhooks from both systems
3. Transform data formats
4. Handle complex business logic
5. Sync to the other system via API

**Phase 2: Handle Common Sync Challenges**

**Challenge 1: Record Ownership**
- HubSpot owner → Salesforce owner mapping
- Create a custom field in both systems matching owner IDs
- Sync owner assignments weekly

**Challenge 2: Duplicate Detection**
- Set up matching rules: Match by email (preferred) or by external ID
- When a new contact appears in Salesforce, check HubSpot by email before creating
- Create a "Sync Log" custom object to track duplicates found and resolved

**Challenge 3: Deleted Records**
- HubSpot soft-deletes contacts (recycle bin)
- Salesforce hard-deletes
- Strategy: Don't delete in HubSpot when deleted in Salesforce — instead, set a "Deleted in Salesforce" flag and update the contact to non-marketing

**Phase 3: Monitor Sync Health**
Create a "Salesforce Sync Health" dashboard:
- **Sync Status** — Last successful sync time, current sync status (Running, Idle, Error)
- **Sync Errors (24h)** — Count of failed sync operations
- **Records Synced** — Contacts, Companies, Deals synced today
- **Conflict Queue** — Number of unresolved conflicts
- **Lag Time** — How far behind the sync is running

### Tutorial 5: Building a Slack Integration for Sales Alerts

**Goal**: Create real-time Slack notifications for important sales events using HubSpot webhooks.

**Step 1: Create Slack App**
1. Go to [api.slack.com/apps](https://api.slack.com/apps) → Create New App
2. Name: "HubSpot Sales Alerts"
3. Select workspace
4. Enable Incoming Webhooks → Activate
5. Copy webhook URL: `https://hooks.slack.com/services/T00/B00/xxxxx`

**Step 2: Set Up HubSpot Webhooks**
1. **Settings** > **Integrations** > **Webhooks** > Create webhook
2. Subscribe to events:
   - `deal.stageChange` — When a deal moves to "Closed Won" or "Closed Lost"
   - `deal.propertyChange` — When deal amount changes
   - `contact.creation` — When a new high-value contact is created
3. Target URL: Your middleware endpoint (or serverless function)

**Step 3: Build Slack Notification Formatting**
```python
import requests
import json
from datetime import datetime

SLACK_WEBHOOK = "https://hooks.slack.com/services/T00/B00/xxxxx"

def send_deal_notification(event_type, deal_data):
    """Send formatted deal notification to Slack."""
    
    colors = {
        'closedwon': '#36A64F',    # Green
        'closedlost': '#FF0000',   # Red
        'default': '#3B82F6'       # Blue
    }
    
    blocks = [
        {
            "type": "header",
            "text": {
                "type": "plain_text",
                "text": f"🚀 {event_type.replace('_', ' ').title()}"
            }
        },
        {
            "type": "section",
            "fields": [
                {"type": "mrkdwn", "text": f"*Deal:* {deal_data.get('dealname', 'Unknown')}"},
                {"type": "mrkdwn", "text": f"*Amount:* ${deal_data.get('amount', 0):,.2f}"},
                {"type": "mrkdwn", "text": f"*Owner:* {deal_data.get('owner', 'Unassigned')}"},
                {"type": "mrkdwn", "text": f"*Company:* {deal_data.get('company', 'Unknown')}"},
            ]
        },
        {
            "type": "section",
            "text": {
                "type": "mrkdwn",
                "text": f"*Time:* {datetime.now().strftime('%Y-%m-%d %H:%M')}\n"
                        f"<{deal_data.get('hubspot_url', '#')}|View in HubSpot>"
            }
        }
    ]
    
    payload = {
        "attachments": [{
            "color": colors.get(event_type, colors['default']),
            "blocks": blocks
        }]
    }
    
    response = requests.post(SLACK_WEBHOOK, json=payload)
    return response.status_code == 200
```

**Step 4: Create Notification Rules**

| Event | Channel | Message Format | Throttle? |
|-------|---------|---------------|-----------|
| Deal Closed Won (>$10K) | #sales-wins | Celebratory with amount, owner, company | No — celebrate every win |
| Deal Closed Won (<$10K) | #sales-wins | Plain summary | No |
| Deal Closed Lost (any) | #sales-leadership | Brief with loss reason | Yes — don't flood channel |
| Deal Amount > Doubled | #sales-leadership | Alert with rep name and new amount | Yes |
| New Enterprise Contact | #sales-leads | Contact details and company info | Yes — only for VIP |
| Weekly Pipeline Summary | #sales-team | Aggregated numbers | Every Monday 9 AM |

### Tutorial 6: Zapier/Make (Integromat) Automation Recipes

**Goal**: Build powerful automations using Zapier or Make as the middleware between HubSpot and other apps.

**Recipe 1: HubSpot → Google Sheets CRM Backup**
1. **Trigger**: New contact created in HubSpot
2. **Action**: Add row to Google Sheet
3. Columns: Timestamp, Email, First Name, Last Name, Phone, Company, Created Date, Lifecycle Stage
4. **Filter**: Only if contact is NOT already in sheet (dedup by email)

**Recipe 2: HubSpot → Mailchimp List Sync**
1. **Trigger**: Contact lifecycle stage changes to "MQL"
2. **Action**: Add/update subscriber in Mailchimp list "Hot Leads"
3. **Mapping**: Email, First Name, Last Name, Company
4. **Tags**: "MQL", source channel

**Recipe 3: Typeform → HubSpot Form Connector**
1. **Trigger**: New Typeform submission received
2. **Actions**:
   - Create HubSpot contact from Typeform responses
   - Map Typeform fields to HubSpot properties
   - Add contact to "Typeform Leads" list
   - Create task: "Follow up with Typeform lead"

**Recipe 4: HubSpot → QuickBooks Invoice Creator**
1. **Trigger**: Deal closed won in HubSpot
2. **Actions**:
   - Create invoice in QuickBooks
   - Add line items from deal products
   - Set customer from associated company
   - Send invoice to contact email
   - Log QuickBooks invoice ID back to HubSpot deal

**Recipe 5: HubSpot Calendar → Google Calendar Sync**
1. **Trigger**: Meeting booked in HubSpot
2. **Actions**:
   - Create Google Calendar event
   - Add contact as guest
   - Add meeting notes and preparation link
   - Create Slack reminder 15 minutes before

### Tutorial 7: Enterprise SSO and SCIM Setup

**Goal**: Configure Single Sign-On (SSO) and System for Cross-domain Identity Management (SCIM) for enterprise user management.

**Step 1: Configure SSO (Enterprise)**
1. **Settings** > **Account Management** > **Security** > **Single Sign-On**
2. Choose identity provider: Okta, Azure AD, OneLogin, or custom SAML 2.0
3. Download HubSpot metadata XML
4. In your IdP:
   - Create a new SAML application
   - Upload HubSpot metadata
   - Map attributes: Email → user.email, First Name → user.firstName, Last Name → user.lastName
   - Assign users/groups to the HubSpot app
5. In HubSpot SSO settings:
   - Upload IdP metadata XML
   - Set default user role: "Viewer" (least privilege)
   - Enable Just-in-Time (JIT) provisioning: Creates HubSpot account on first SSO login
6. Test SSO with a test user account
7. Enforce SSO: "Require SSO for all users"

**Step 2: Configure SCIM (Enterprise)**
1. **Settings** > **Account Management** > **Integrations** > **SCIM**
2. Enable SCIM
3. Copy SCIM endpoint URL and API token
4. In your IdP (Okta/Azure AD):
   - Configure SCIM provisioning
   - Map HubSpot SCIM endpoint
   - Set attribute mapping
   - Enable: Create users, Update attributes, Deactivate users
5. Test provisioning: Add a test user in IdP, verify they appear in HubSpot

**Step 3: Set Up User Groups and Role Mapping**
| IdP Group | HubSpot Role | Notes |
|-----------|-------------|-------|
| hubspot-admins | Super Admin | Full access, all hubs |
| hubspot-marketing | Marketing Manager | Marketing Hub, Reports |
| hubspot-sales | Sales Manager | Sales Hub, CRM |
| hubspot-sales-rep | Sales Rep | Sales Hub, limited |
| hubspot-support | Service Agent | Service Hub, Tickets |
| hubspot-viewers | View Only | Read-only across all hubs |

**Step 4: Audit User Activity**
1. **Settings** > **Account Management** > **Users & Teams** > **Audit Log** (Enterprise)
2. Track:
   - User creation and deactivation
   - Role changes
   - Failed SSO login attempts
   - API token creation/deletion
3. Schedule monthly access review

### Tutorial 8: Custom Integration with REST API + OAuth

**Goal**: Build a complete custom integration from scratch that authenticates with OAuth 2.0 and performs CRUD operations.

**Step 1: Create Private App in HubSpot**
1. **Settings** > **Integrations** > **Private Apps** > Create private app
2. Name: "My Custom Integration"
3. Scopes:
   - `crm.objects.contacts.read`
   - `crm.objects.contacts.write`
   - `crm.objects.deals.read`
   - `crm.objects.deals.write`
   - `crm.schemas.custom_objects.read`
4. Generate access token
5. Copy token and store securely (never commit to version control)

**Step 2: Python Integration Client**
```python
import requests
import json
from typing import Dict, List, Optional

class HubSpotClient:
    """A complete HubSpot API client with error handling and pagination."""
    
    def __init__(self, access_token: str):
        self.base_url = "https://api.hubapi.com"
        self.headers = {
            "Authorization": f"Bearer {access_token}",
            "Content-Type": "application/json"
        }
    
    def get_contact(self, email: str) -> Optional[Dict]:
        """Get a contact by email."""
        response = requests.post(
            f"{self.base_url}/crm/v3/objects/contacts/search",
            headers=self.headers,
            json={
                "filterGroups": [{
                    "filters": [{
                        "propertyName": "email",
                        "operator": "EQ",
                        "value": email
                    }]
                }],
                "properties": ["email", "firstname", "lastname", "phone", "company"]
            }
        )
        
        if response.status_code == 200:
            results = response.json().get("results", [])
            return results[0] if results else None
        return None
    
    def create_contact(self, properties: Dict) -> Dict:
        """Create a new contact."""
        response = requests.post(
            f"{self.base_url}/crm/v3/objects/contacts",
            headers=self.headers,
            json={"properties": properties}
        )
        response.raise_for_status()
        return response.json()
    
    def update_contact(self, contact_id: str, properties: Dict) -> Dict:
        """Update an existing contact."""
        response = requests.patch(
            f"{self.base_url}/crm/v3/objects/contacts/{contact_id}",
            headers=self.headers,
            json={"properties": properties}
        )
        response.raise_for_status()
        return response.json()
    
    def upsert_contact(self, email: str, properties: Dict) -> Dict:
        """Create or update a contact (upsert by email)."""
        existing = self.get_contact(email)
        if existing:
            return self.update_contact(existing["id"], properties)
        else:
            properties["email"] = email
            return self.create_contact(properties)
    
    def get_all_deals(self, properties: List[str] = None) -> List[Dict]:
        """Get all deals with pagination."""
        if properties is None:
            properties = ["dealname", "amount", "dealstage", "closedate", "pipeline"]
        
        all_deals = []
        after = None
        
        while True:
            params = {
                "limit": 100,
                "properties": properties
            }
            if after:
                params["after"] = after
            
            response = requests.get(
                f"{self.base_url}/crm/v3/objects/deals",
                headers=self.headers,
                params=params
            )
            response.raise_for_status()
            data = response.json()
            
            all_deals.extend(data.get("results", []))
            
            paging = data.get("paging", {})
            next_page = paging.get("next", {})
            after = next_page.get("after")
            
            if not after:
                break
        
        return all_deals

# Usage
client = HubSpotClient("your-private-app-token")

# Upsert a contact
contact = client.upsert_contact("john@example.com", {
    "firstname": "John",
    "lastname": "Doe",
    "phone": "+1-555-0123",
    "company": "Acme Corp",
    "jobtitle": "CTO"
})

# Get all deals this quarter
deals = client.get_all_deals()
print(f"Found {len(deals)} deals")
```

**Step 3: Error Handling Strategy**
| Error | Cause | Retry? | Action |
|-------|-------|--------|--------|
| 200 OK | Success | No | Parse and process |
| 401 Unauthorized | Token expired/invalid | No | Regenerate token |
| 429 Rate Limited | Too many requests | Yes | Wait Retry-After header seconds |
| 502 Bad Gateway | HubSpot temporary | Yes | Wait 5s, retry up to 3 times |
| 503 Service Unavailable | HubSpot overloaded | Yes | Wait 10s, retry up to 3 times |
| 500 Internal Error | HubSpot bug | Yes | Wait 30s, retry once, then alert |

**Step 4: Monitor Integration Health**
1. Create a status page dashboard:
   - **API Calls Today** — Count of API requests made
   - **Error Rate** — % of API calls that failed (target: < 1%)
   - **Average Response Time** — How fast is the API responding
   - **Last Successful Sync** — Timestamp of last full sync
2. Set up alerts:
   - Error rate > 5% in 10 minutes → Page on-call engineer
   - No successful sync in 4 hours → Alert operations team
   - API response time > 3 seconds average → Investigate slowdown
```