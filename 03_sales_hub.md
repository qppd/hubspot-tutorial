# 3. Sales Hub — Complete Tutorial

## Table of Contents
1. [Introduction to Sales Hub](#introduction-to-sales-hub)
2. [Email Tracking & Templates](#email-tracking--templates)
3. [Sequences — Complete Guide](#sequences--complete-guide)
4. [Meetings — Complete Guide](#meetings--complete-guide)
5. [Calling — Complete Guide](#calling--complete-guide)
6. [Conversation Intelligence (Enterprise)](#conversation-intelligence-enterprise)
7. [Deal Management — Complete Guide](#deal-management--complete-guide)
8. [Lead Management — Complete Guide](#lead-management--complete-guide)
9. [Quotes — Complete Guide](#quotes--complete-guide)
10. [Playbooks — Complete Guide](#playbooks--complete-guide)
11. [Forecasting — Complete Guide](#forecasting--complete-guide)
12. [LinkedIn Sales Navigator Integration](#linkedin-sales-navigator-integration)
13. [Multi-Currency Reporting](#multi-currency-reporting)
14. [Limits That Matter](#limits-that-matter)
15. [Common Gotchas](#common-gotchas)
16. [Use Cases](#use-cases)

---

## Introduction to Sales Hub

Sales Hub equips sales teams with tools to manage pipelines, automate outreach, track buyer engagement, and close more deals. It integrates directly with the CRM so every email, call, meeting, and quote is tracked against the contact's record.

### What You Get by Tier

| Feature | Free | Starter | Pro | Enterprise |
|---------|------|---------|-----|------------|
| Email tracking | ✓ | ✓ | ✓ | ✓ |
| Email templates | 5 | Unlimited | Unlimited | Unlimited |
| Meeting scheduling | ✓ | ✓ | ✓ | ✓ |
| Sequences | ✗ | ✗ | ✓ | ✓ |
| Calling (VoIP) | ✗ | ✗ | ✓ | ✓ |
| Conversation Intelligence | ✗ | ✗ | ✗ | ✓ |
| Quotes with e-signature | ✗ | ✗ | ✓ | ✓ |
| Playbooks | ✗ | ✗ | ✓ | ✓ |
| Forecasting | ✗ | ✗ | ✓ | ✓ |
| Deal splits | ✗ | ✗ | ✗ | ✓ |
| Multi-currency | ✗ | ✗ | ✓ | ✓ |
| LinkedIn Sales Nav | ✗ | ✗ | ✓ | ✓ |

### Navigation

- **Sales** > **Dashboard** — Sales KPIs at a glance
- **Sales** > **Deals** — Pipeline board, list, table views
- **Sales** > **Contacts** — Contact management
- **Sales** > **Companies** — Account management
- **Sales** > **Leads** — Lead management (Prospecting workspace)
- **Sales** > **Quotes** — Quote creation and management
- **Sales** > **Sequences** — Automated outreach sequences
- **Sales** > **Meetings** — Meeting links and scheduling
- **Sales** > **Calls** — Call log and calling
- **Sales** > **Conversations** — Live chat, email, social inbox
- **Sales** > **Forecasting** — Revenue forecasting
- **Sales** > **Playbooks** — Sales methodology guides
- **Sales** > **Tasks** — Task tracking and queues
- **Sales** > **Pipelines** — Deal pipeline management

---

## Email Tracking & Templates

### Email Tracking Setup

HubSpot tracks emails you send from your connected inbox (Gmail, Outlook, or Office 365).

**Setting up email tracking**:
1. **Settings** > **Integrations** > **Email**
2. Click "Connect your email" or "Connect inbox"
3. Choose provider: Gmail/Google Workspace, Outlook/Office 365, Exchange
4. Authenticate with OAuth 2.0
5. Enable tracking:
   - **Email open tracking**: Adds a 1x1 invisible tracking pixel
   - **Click tracking**: Rewrites links to track clicks
   - **Attachment tracking**: Tracks when attachments are opened (Sales Hub Pro+)
6. Select default behavior: Track all emails, or offer a toggle button
7. **Tracking notification**: Get notified when someone opens/clicks

**When tracking works best**:
- Gmail/Google Workspace: Full tracking
- Outlook/Office 365: Full tracking
- Third-party SMTP: Limited tracking (no read receipts)
- Mobile email apps: Opens may be under-reported (Apple Mail Privacy Protection)

### Email Templates

Save and reuse emails with personalization tokens.

**Creating a template**:
1. **Sales** > **Templates** > Create template
2. Write your email body
3. Insert personalization tokens: `{{ contact.firstname }}`, `{{ contact.company }}`, `{{ contact.jobtitle }}`
4. **Folder organization**: Create folders (Prospecting, Follow-up, Meeting requests, etc.)
5. **Sharing**: Share with team (private, team, or organization-wide)
6. **Favorite**: Star frequently used templates

**Template examples by scenario**:

**Cold outreach**:
```
Subject: Quick question about {{ contact.company }}

Hi {{ contact.firstname }},

I noticed {{ contact.company }} has been in the {% if contact.industry %}{{ contact.industry }} industry{% else %}industry{% endif %} for a while now, and I had a thought that might be relevant to your work.

We've been helping companies like yours {{ value_proposition }}.

Would you be open to a 15-minute chat next week to discuss?

Best,
{{ owner.firstname }}
```

**Follow-up after demo**:
```
Subject: Following up on our demo

Hi {{ contact.firstname }},

Thanks again for your time on our demo call. Based on our conversation, I think the {{ deal.dealname }} opportunity at {{ contact.company }} is a great fit for our [Product Name] solution.

I've attached the proposal for your review. Key highlights:
- {{ deal.line_items.0.name }}
- {{ deal.dealname }} timeline

Let me know if you have any questions.

Best,
{{ owner.firstname }}
```

**Meeting request**:
```
Subject: {{ contact.firstname }}, meet {{ owner.firstname }}?

Hi {{ contact.firstname }},

I'd love to learn more about {{ contact.company }}'s goals for {{ contact.year }}. Do you have 15 minutes free next week?

Here's my calendar link to find a time that works for you:
{{ owner.meetings_link }}

Looking forward to connecting.

Best,
{{ owner.firstname }}
```

### Snippets

Snippets are short reusable text blocks for common replies:

1. **Sales** > **Snippets** > Create snippet
2. Example snippets:
   - "Let me check with my team" (1-2 day reply)
   - "Here's the pricing page link"
   - "Thanks for your time" (post-meeting thank you)
   - "Can you forward me the PO number?"
3. Insert snippets in any email with a keyboard shortcut or dropdown

**AI Snippet Recommendations** (Pro+/Breeze):
- Based on email context and conversation history
- Breeze AI suggests relevant snippets while you type
- Click to insert, saving time on common responses

### Document Tracking

Upload and share documents with tracking:

1. **Sales** > **Documents** > Upload
2. Choose file: PDF, DOCX, XLSX, PPTX
3. Set sharing permissions: Anyone with link, only specific contacts
4. Share link via email or sequence
5. **Tracking**: You'll see:
   - Who viewed the document
   - How long they spent on each page
   - Whether they forwarded it
   - Time of first view

---

## Sequences — Complete Guide

Sequences are automated multi-step outreach campaigns. They send follow-up emails and create tasks on a schedule until the lead responds or the sequence ends.

### Creating a Sequence — Step-by-Step

1. **Sales** > **Sequences** > Create sequence
2. **Name** your sequence: "Post-Demo Follow-up" or "Cold Outreach — 5 Steps"
3. **Set a goal**: What does success look like?
   - Meeting booked
   - Reply received
   - Call me back
   - Custom
4. **Add steps**:

   **Step types**:
   - **Send email**: Choose template or write from scratch; personalization tokens available
   - **Wait/Delay**: Specific days, hours, or "next business day" (respects business hours)
   - **Manual task**: Creates a to-do for the rep (e.g., "Call this lead")
   - **Automatic task**: Creates a task automatically without rep action required
   - **Conditional branch** (Pro+): Skip steps based on recipient behavior

   **Example: 7-Step Cold Outreach Sequence**:
   | Step | Type | Content | Delay |
   |------|------|---------|-------|
   | 1 | Send email | Initial outreach — value proposition | Day 0 |
   | 2 | Wait | — | 2 days |
   | 3 | Send email | Follow-up — social proof/case study | Day 2 |
   | 4 | Wait | — | 3 days |
   | 5 | Send email | Final outreach — "Should I close this out?" | Day 5 |
   | 6 | Wait | — | 5 days |
   | 7 | Create task | "Move to inactive or try alternate channel" | Day 10 |

5. **Set enrollment criteria**: Who can be enrolled?
   - Contact must have email address
   - Contact not currently enrolled in another sequence
   - Lifecycle stage filter (e.g., Lead or SQL only)
   - Company size, industry, or other property filters

6. **Unenrollment triggers**: When should a contact automatically exit?
   - Contact replies to any sequence email
   - Meeting booked
   - Deal stage changed to "Closed Won" or "Closed Lost"
   - Contact unsubscribes
   - Specific keyword detection in reply (e.g., "unsubscribe", "not interested")
   - Custom property change

7. **Send limits**:
   - Max emails per week per contact (default: 5)
   - Max emails per day per contact
   - These prevent burning out your database

8. **Schedule**: Active immediately or set start date

9. **Save and activate**

### Enrolling Contacts

**Manual enrollment**:
1. Open a contact record
2. In the "Sequences" section, click "Enroll in sequence"
3. Select the sequence
4. Optional: Set first email send time (or send immediately)
5. Click "Enroll"

**Bulk enrollment**:
1. From a contact list, select multiple contacts
2. Actions > Enroll in sequence
3. Choose sequence
4. Confirm

**Automated enrollment via workflows**:
1. Create a workflow
2. Trigger: When lifecycle becomes MQL
3. Action: Enroll in sequence — "New MQL outreach"

### Sequence Analytics

Monitor sequence performance:

**Dashboard metrics**:
- **Active enrollments**: Contacts currently in the sequence
- **Completed**: Contacts who finished the sequence
- **Replied**: Contacts who replied at any step
- **Meeting booked**: Goal completions
- **Bounced**: Email bounces
- **Unsubscribed**: Contacts who unsubscribed
- **Unenrolled**: Contacts removed by other triggers

**Per-step metrics**:
- Open rate for each step
- Click rate for each step
- Reply rate for each step
- Step-by-step conversion

**Sequence comparison**: Compare multiple sequences side-by-side to see which performs best.

### Sequence Best Practices

1. **Start with value**: First email should offer value, not just "checking in"
2. **Mix email types**: Not all emails need to be text — try case studies, video messages, social proof
3. **Respect busy people**: 3-5 steps is usually enough. 10+ emails in a sequence rarely perform better.
4. **Use conditional branching**: If a contact clicks a specific link on step 2, skip steps 3-4 and go straight to the demo offer
5. **Personalize aggressively**: Use personalization tokens for company, industry, role
6. **Include a clear CTA**: Every email should have one specific ask
7. **Test subject lines**: A/B test your sequence subject lines
8. **Monitor unsubscribe rate**: If >1%, your sequence may be too aggressive

---

## Meetings — Complete Guide

### Meeting Link Setup

1. **Sales** > **Meetings** > Create meeting link
2. **Calendar integration**: Connect Google Calendar or Office 365 (required)
3. **Meeting name**: "Discovery Call" or "Product Demo"
4. **Duration**: 15, 30, 45, or 60 minutes
5. **Availability**:
   - Specific days of the week
   - Time range (e.g., 9 AM - 5 PM)
   - Buffer time between meetings (5-30 min)
   - Lunch break (block off specific time)
6. **Meeting type**: Phone call, Video call (Zoom/Google Meet/Teams), In-person
7. **Location or link**: Auto-join URL for video conferences
8. **Reminders**: Custom email reminders (1 hour before, 24 hours before)
9. **Customize URL**: `meetings.hubspot.com/yourname/discovery-call`

### Round-Robin Meeting Scheduling

Distribute meetings among team members:

1. **Settings** > **Sales** > **Meetings** > **Round-robin**
2. Add team members
3. Choose assignment method:
   - **Even distribution**: New meeting goes to the person with fewest meetings
   - **Sequential**: Pre-set order, each person gets one, then cycle repeats
4. Link: Share a single meeting link for the team

### Meeting Types

| Type | Best For |
|------|----------|
| **Discovery Call** | Initial qualification — 30 min |
| **Product Demo** | Show product in action — 45-60 min |
| **Proposal Review** | Review quote/contract — 30 min |
| **Technical Deep Dive** | Technical evaluation — 60 min |
| **Check-in** | Ongoing account review — 30 min |
| **QBR (Quarterly Business Review)** | Strategic review — 60 min |

### Group Meetings

Multiple people on one meeting link:
1. Create meeting link
2. Add "Round-robin" or "Collective" group
3. **Collective**: Contact sees combined availability of all team members
4. **Round-robin**: Contact books with one specific person from the team

### Calendar Sync

Two-way sync with:
- **Google Calendar**: Full sync (events created in either direction)
- **Office 365 / Exchange**: Full sync
- **iCloud**: One-way (HubSpot reads but doesn't write)

When a contact books a meeting, an event is created in your calendar with the contact name, company, and any intake questions answered.

---

## Calling — Complete Guide

### HubSpot Calling Setup

1. **Settings** > **Sales** > **Calling**
2. Enable HubSpot Calling (Sales Hub Pro+)
3. Choose phone number: Use your existing business number or get a new one
4. **Local presence** (US only): Caller ID shows a local number matching the recipient's area code
5. **Call recording**: Enable recording (check local laws — consent required in some jurisdictions)
6. **Voicemail**: Drop pre-recorded or typed voicemails

### Making a Call

From a contact record:
1. Click the phone icon next to the contact's phone number
2. HubSpot Calling dialer opens in your browser
3. Click "Call" → browser requests microphone access
4. Connect via computer (VoIP) with headset or handset
5. Call connects — duration, notes, outcome options appear
6. After call: Log outcome (Connected, Left voicemail, No answer, Busy, Wrong number, Other)
7. Add notes
8. Recording is saved to the contact timeline (if enabled)

### Call Analytics

Available in Sales Hub Pro+ and Enterprise:

- **Total calls**: Daily, weekly, monthly
- **Call duration**: Average per rep
- **Call outcomes**: Connected vs not connected
- **Call volume by rep**: Who's making the most/fewest calls
- **Call-to-meeting conversion**: How many calls result in booked meetings

### Power Dialer (Enterprise)

Auto-dial through a list of contacts:

1. Create or select a call list (filtered contacts)
2. Click "Power dial" in the calling section
3. HubSpot dials the first contact
4. If no answer → auto-moves to next contact
5. If connected → log outcome, auto-dials next contact when you finish
6. Logs all call attempts

---

## Conversation Intelligence (Enterprise)

Conversation Intelligence records, transcribes, and analyzes sales calls to provide coaching insights.

### Call Recording & Transcription

1. Enable call recording in Settings > Sales > Calling
2. When a call is recorded, transcription starts automatically
3. Transcription appears in the call timeline entry within minutes
4. Full text search across all call transcriptions

### AI Call Summaries (Breeze AI)

After each recorded call, Breeze AI generates:
- **Summary**: 2-3 sentence overview of the call
- **Key points**: Main topics discussed (product features, pricing, timeline, competitors)
- **Action items**: Follow-up tasks extracted from the conversation
- **Next steps**: Recommended next action for the rep
- **Sentiment**: Overall tone of the conversation (positive, neutral, negative)

### AI Coaching Suggestions

Breeze AI analyzes call patterns and suggests coaching opportunities:

- **Talk-to-listen ratio**: Who dominated the conversation? (Ideal: 50/50 or customer talks more)
- **Objection handling**: How did the rep handle pricing objections? Competitor questions?
- **Discovery questions**: Did the rep ask about budget, authority, need, timeline (BANT)?
- **Next steps**: Did the rep clearly define next steps?
- **Competitive mentions**: How were competitors discussed?
- **Value proposition**: Was the value proposition clearly stated?
- **Closing**: Did the rep ask for the business?

### Keyword Spotting

Set keywords to auto-flag in calls:

1. **Settings** > **Sales** > **Conversation Intelligence** > **Keywords**
2. Add keywords: "Competitor", "Budget", "Pricing too high", "Decision maker"
3. When a keyword is mentioned, it's highlighted in the transcript
4. Notifications can be set for high-priority keywords

### Coaching Scorecards

Managers can review calls with structured scorecards:

1. **Sales** > **Conversation Intelligence** > **Review call**
2. Listen to recording or read transcript
3. Fill in scorecard:
   - Opening (1-5): Did rep introduce themselves and set agenda?
   - Discovery (1-5): Did rep ask qualification questions?
   - Presentation (1-5): Was value prop clear?
   - Objection handling (1-5): Were objections addressed well?
   - Closing (1-5): Was next step clearly defined?
4. Add comments: "Great objection handling on pricing. Work on asking more discovery questions."
5. Assign coaching action: "Schedule role-play session on discovery"

### Call Playlists

Group calls by topic for training:
1. Create playlist: "Objection handling examples"
2. Add calls where objections were handled well
3. Share with team for training
4. Team members can listen, rate, and comment

---

## Deal Management — Complete Guide

### Deal Record Anatomy

Each deal has:

- **Pipeline & Stage**: Where the deal is in the sales process
- **Amount**: Deal value in your base currency
- **Close date**: Expected close date
- **Owner**: The sales rep responsible
- **Contact**: Who the buyer is at the company
- **Company**: The account
- **Line items**: Products/services, quantities, prices, discounts
- **Activities**: Emails, calls, meetings, notes logged against the deal
- **Associations**: Quotes, invoices, tickets related to the deal
- **Forecast category**: Commit, Best case, Pipeline, Closed won, Closed lost
- **Deal type**: New business, Upgrade, Renewal, Cross-sell

### Creating a Deal

**From contact record**:
1. Open contact → Deals section → Create deal
2. Enter deal name, pipeline, stage, amount, close date
3. Set deal owner (defaults to contact owner)
4. Click Create

**From company record**: Same process, associates deal to company

**From email**: Reply to a prospect's email → Click "Create deal" from the email timeline → Pre-fills contact/company

**From form submission**: Workflow auto-creates deal when "Request a demo" form is submitted

**From import**: CSV import from another CRM

### Deal Pipeline Board (Kanban View)

The most commonly used view:

```
| New Lead | Qualified | Demo Scheduled | Demo Done | Proposal | Closed Won | Closed Lost |
|----------|-----------|----------------|-----------|----------|------------|-------------|
| [Card]   | [Card]    | [Card]         | [Card]    | [Card]   | [Card]     | [Card]      |
| Acme Corp| Globex    | Initech        | MegaCorp  | Stark    | Wayne      | Oscorp      |
| $50k     | $100k     | $75k           | $200k     | $150k    | $50k       | $30k        |
| John S.  | Jane D.   | Bob M.         | Alice K.  | Tom H.   | Sara L.    | Mike P.     |
```

**Card details**: Deal name, amount, contact name, owner, last activity date. Click card to open deal record.

**Drag and drop**: Move deals between stages. Confirmation may be required for locked stages.

### Line Items

Products and services on a deal:

1. Open a deal → **Line items** section
2. Click "Add line items"
3. **From product library**: Search existing products (from **Settings** > **Products**)
4. **Custom line item**: Enter name, description, quantity, unit price
5. **Discount**: Per-line or overall discount (flat amount or percentage)
6. **Recurring**: For subscription products — monthly, yearly, quarterly

**Product library management**:
1. **Settings** > **Products** > **Products**
2. Create product: Name, SKU, description, price, unit, category
3. Organize products into product categories
4. Set currency (can be different from portal default)

### Deal Splits (Enterprise)

Split deal credit among multiple reps:

1. Open a deal → Click "Split" in the deal header
2. Add reps and their percentage share
3. Must total 100%
4. Each rep's forecast reflects their split amount
5. Splits are visible in reporting

### Auto-Assignment Rules

Automatically assign new deals to reps:

1. **Settings** > **Sales** > **Deals** > **Assignment rules**
2. Create rule:
   - **Round-robin**: Distribute evenly among team
   - **Rules-based**: If industry = "Technology" → assign to Tech team. If deal amount > $50k → assign to Enterprise team.
3. Rules can stack: First matching rule applies

---

## Lead Management — Complete Guide

### Lead Scoring (Sales Hub Enterprise)

Score leads based on fit and behavior:

1. **Sales** > **Lead Scoring** > Create scoring model
2. **Fit scoring**: Demographic match (industry, job title, company size)
3. **Behavior scoring**: Engagement (email opens, page visits, form submissions)
4. **Combine scores**: Total score = fit + behavior
5. **Thresholds**: Score ranges determine lead status

### Predictive Lead Scoring via Breeze Intelligence

ML-based scoring that auto-adjusts:
- Based on your CRM's historical conversion data
- Identifies patterns: "Leads from manufacturing companies with VP-level titles who visited our pricing page close at 3× the rate of other leads"
- Auto-updates as new data comes in
- Provides a single "Likelihood to close" score (0-100%)

### Lead Rotation (Round-Robin)

Distribute new leads fairly:
1. **Settings** > **Sales** > **Lead rotation**
2. Create rotation rule: "New MQLs → rotate among SDR team"
3. Set: Who gets assigned, how many per person before next person
4. Overassignments: If a rep is on PTO, exclude from rotation

### Prospecting Workspace

A focused view for outreach:
- **Sales** > **Leads** > **Prospecting workspace**
- Shows: Your leads that need attention
- Filters: By source, by score, by last activity date
- Quick actions: Enroll in sequence, create task, log call, send email
- Custom queues: "Call today", "Follow up by email", "Research company"

---

## Quotes — Complete Guide

### Creating a Quote — Step-by-Step

1. Open a deal → **More** → **Create quote**
2. **Select template**: Choose a quote template or start from a saved template
3. **Add line items**: From the deal or select from product library
4. **Set discounts**: Per-line or overall discount
5. **Terms & conditions**: Add your standard terms (reusable snippets)
6. **Payment options** (if Commerce Hub enabled):
   - Pay in full, pay by invoice, payment plan
   - Attach payment link for immediate payment
7. **Expiration date**: Default 30 days
8. **Signature options**:
   - **HubSpot native e-signature**: Free, unlimited signatures
   - **DocuSign**: Connect your DocuSign account
   - **PandaDoc**: Connect your PandaDoc account
9. **Preview**: See PDF version of the quote
10. **Send**: Quote is emailed to contact, logged on deal timeline

### Quote Templates

Create reusable templates:
1. **Settings** > **Sales** > **Quotes** > **Templates**
2. Create template: Logo placement, color scheme, font, header/footer
3. Template sections: Header, summary, line items, terms, signature area
4. Default vs custom: Templates can be for specific teams or products

### Approval Workflows

Require manager approval for quotes over certain thresholds:

1. **Settings** > **Sales** > **Quotes** > **Approval settings**
2. Enable approval workflow
3. Set rules:
   - Quote amount > $10,000 → requires manager approval
   - Discount > 20% → requires VP approval
   - Specific products → requires sales engineering approval
4. Approvers get notification → approve/reject from email or in HubSpot

### E-Signature

HubSpot's native e-signature:
- Included with Sales Hub Pro+
- No additional cost per signature
- Legally binding in most jurisdictions (ESIGN Act, eIDAS)
- Audit trail: IP address, timestamp, email verification
- Automatic quote status updates: Sent → Viewed → Signed → Closed Won

---

## Playbooks — Complete Guide

Playbooks are guided sales methodologies embedded in HubSpot. They help reps ask the right questions, follow a process, and close more deals.

### Creating a Playbook — Step-by-Step

1. **Sales** > **Playbooks** > Create playbook
2. **Name**: "Discovery — MEDDIC" or "Competitor Displacement"
3. **Description**: Brief overview of when to use this playbook
4. **Trigger**: Which deal stage or event auto-suggests this playbook?
   - Deal stage: "When deal moves to Demo stage → suggest 'Demo Best Practices' playbook"
   - Manual: Rep opens playbook on demand
5. **Content**:
   - **Question templates**: Guided questions for reps
   - **Ask Me Anything (AMA)**: Dynamic responses based on rep input
   - **Scripts**: Suggested talking points
   - **Email templates**: Templates to send to prospect
   - **Documents**: Attach PDFs, case studies, proposals
   - **Videos**: Embed training videos
   - **Links**: Quick links to internal resources
6. **Sales methodologies**:
   - **MEDDIC**: Metrics, Economic buyer, Decision criteria, Decision process, Identify pain, Champion
   - **BANT**: Budget, Authority, Need, Timeline
   - **SPIN**: Situation, Problem, Implication, Need-payoff
   - **Challenger**: Teach, Tailor, Take control
   - **Command of the Message**: Value proposition, capabilities, proof points
7. **Save and publish**: Share with specific teams or all sales

### Using a Playbook

1. Open a deal → Click "Playbooks" in the sidebar
2. Select the appropriate playbook
3. Answer guided questions → answers are saved to the deal record
4. Follow suggested scripts during the call
5. Complete the playbook → summary logged to deal timeline

---

## Forecasting — Complete Guide

Forecasting predicts your team's revenue for a given period.

### Setting Up Forecasting

1. **Sales** > **Forecasting** > Configure
2. **Forecast period**: Monthly, Quarterly, Custom
3. **Forecast categories**:
   - **Commit**: Deals you're very confident will close (your "promise" number)
   - **Best case**: Deals you expect to close but aren't 100% sure
   - **Pipeline**: All open deals regardless of confidence
   - **Closed won / Closed lost**: Historical data
4. **Probability override**: Default probability per stage, or manual entry
5. **Team hierarchy** (Enterprise):
   - Set up reporting structure: Rep → Team Lead → VP → CRO
   - Manager sees rollup of their team's forecast
6. **Forecast filters**:
   - Include/exclude specific pipelines
   - Include/exclude specific deal types
   - Include/exclude specific products
7. **Notifications**: Email alerts when key deals move stages

### Breeze AI Forecasting Predictions

ML-enhanced forecasting that auto-adjusts:

- **Deal velocity**: How fast deals typically move through each stage
- **Historical close rates**: Actual close rates per rep, per team, per pipeline
- **Stuck deals**: Deals inactive for X days flagged for attention
- **Predicted close date**: ML estimate based on historical patterns
- **Confidence score**: How reliable each forecast number is
- **What-if analysis**: "If all deals at 70%+ close, revenue = $X"

### Forecast Reporting

- **View by**: Pipeline, rep, team, product, region
- **Forecast vs quota**: How each rep/team is tracking
- **Trend lines**: Compare to previous periods
- **Weighted pipeline**: Deal value × stage probability

---

## LinkedIn Sales Navigator Integration

### Setting Up

1. **Settings** > **Integrations** > **LinkedIn Sales Navigator**
2. Click "Connect"
3. Authenticate with your LinkedIn Sales Navigator account
4. Grant permissions for: Profile access, InMail access, CRM sync

### Features

- **Profile sync**: LinkedIn profiles linked to HubSpot contacts
- **Activity sync**: InMail messages, profile views, saves logged to CRM
- **Save to CRM**: Save LinkedIn profiles directly to HubSpot
- **List sync**: LinkedIn list → HubSpot list, and vice versa
- **Icebreakers**: LinkedIn shows mutual connections and talking points
- **Notes**: Sync notes between platforms

---

## Multi-Currency Reporting

**Supported on**: Sales Hub Pro+

### Setup

1. **Settings** > **Sales** > **Currencies**
2. Set base currency (your reporting currency)
3. Add additional currencies you deal in (USD, EUR, GBP, JPY, etc.)
4. Exchange rates: Manual or auto-updated (daily)

### How It Works

- Deals can be created in any configured currency
- Amounts are converted to base currency for reporting
- Exchange rates update daily for automatic mode
- Reports show amounts in both original and base currency
- Forecasting converts all deals to base currency

---

## Limits That Matter

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Email tracked/day | 200 | 200 | 1,000 | 1,000 |
| Email templates | 5 | Unlimited | Unlimited | Unlimited |
| Sequences active/user | 0 | 0 | 1,000 | 2,000 |
| Sequence steps | — | — | 50 | 50 |
| Meeting links/user | 5 | Unlimited | Unlimited | Unlimited |
| Playbooks | — | — | 50 | 500 |
| Deal pipelines | 10 | 10 | 50 | 100 |
| Deal stages/pipeline | 30 | 30 | 30 | 30 |
| Quotes/deal | — | — | 20 | 100 |
| Line items/quote | — | — | 50 | 50 |
| Deal splits/deal | — | — | — | 15 |
| Forecast periods | — | — | 8 | Unlimited |
| Forecasting teams | — | — | — | Unlimited |

---

## Common Gotchas

### 1. Sequence Unenrollment
If you don't set unenrollment triggers, contacts will receive the entire sequence even after they reply. Always configure unenrollment conditions.

### 2. Email Tracking Limitations
Apple Mail Privacy Protection and some Android clients block tracking pixels. Opens from these clients may not be tracked accurately.

### 3. Call Recording Compliance
In many jurisdictions (US 10+ states require two-party consent), you must inform the other party that the call is being recorded. HubSpot provides an optional consent tone.

### 4. Quote Template Editing
Quotes created without a template CANNOT be edited after sending. You must clone the quote and create a new one with a template.

### 5. Forecasting Accuracy
Forecast accuracy depends on accurate deal stage probability. If deals at "Demo" stage close at 30% but probability is set to 50%, your forecast is inflated. Regularly review and adjust.

### 6. LinkedIn Sales Nav Permissions
Integration requires each user to have their own LinkedIn Sales Navigator seat. Shared licenses don't work.

### 7. Deal Splits Affect Reporting
Each rep's split of a deal affects their individual forecast independently. Misconfigured splits can inflate forecast totals (100% rep A + 100% rep B = 200% of actual deal value — but splits should total 100%).

### 8. Multi-Currency Rounding
Exchange rate conversions can produce rounding differences in reporting. Auto-update rates help but manual adjustments may be needed for audit accuracy.

---

## Sales Hub Tutorials

### Tutorial 1: Building a Complete Sales Outreach System

**Goal**: Set up an end-to-end outbound sales process from prospecting to meeting booked.

**Step 1: Configure Email Infrastructure**
1. **Settings** > **Integrations** > **Email** — Connect your email account
2. Enable open tracking, click tracking, and attachment tracking
3. Create 3 starter templates:
   - Cold outreach template (personalized, value-first)
   - Follow-up template (social proof, case study link)
   - Break-up template ("Should I close this out?")

**Step 2: Build Your First Sequence**
1. **Sales** > **Sequences** > Create sequence
2. Name: "Standard Outbound — 5 Steps"
3. Steps:
   - Day 0: Send cold outreach email (personalized subject line with company name)
   - Day 2: Wait (2 business days)
   - Day 2: Send follow-up email with case study link
   - Day 4: Wait (3 business days)
   - Day 4: Send break-up email with meeting link
   - Day 7: Create task: "Try alternate contact or move to nurture"
4. Enrollment criteria: Contact must have email AND company
5. Unenrollment triggers: Contact replies OR meeting booked
6. Send limits: Max 3 emails per week per contact

**Step 3: Create Prospecting Workspace**
1. **Sales** > **Leads** > **Prospecting Workspace**
2. Set filters: Lifecycle stage = Lead, Lead status = New
3. Add columns: Company, Industry, Lead score
4. Save view as "Priority Prospects"
5. Create queues: "Call Today", "Send Email", "Follow Up"

**Step 4: Build a Meeting Scheduling Cadence**
1. Create meeting link: "Discovery Call" — 30 min
2. Set availability: Mon-Fri, 9 AM-5 PM with 15 min buffer
3. Add intake questions: "What's your biggest challenge with [product area]?"
4. Enable automatic reminders: 24 hours and 1 hour before

**Step 5: Monitor and Optimize**
1. After 30 days, review sequence analytics
2. Compare open rates, reply rates, meeting booking rates
3. A/B test subject lines and email content
4. Identify best-performing template and use as new default

### Tutorial 2: Setting Up Sales Forecasting

**Goal**: Configure accurate revenue forecasting for your sales team.

**Step 1: Verify Deal Stage Probabilities**
1. **Sales** > **Forecasting** > Configure
2. Review each stage's probability:
   | Stage | Current Probability | Actual Close Rate | Adjust? |
   |-------|-------------------|-------------------|---------|
   | New Lead | 10% | 8% | No (close enough) |
   | Qualified | 25% | 22% | No |
   | Demo Scheduled | 40% | 30% | Yes → 30% |
   | Demo Completed | 50% | 35% | Yes → 35% |
   | Proposal Sent | 70% | 60% | Yes → 60% |
   | Negotiation | 85% | 75% | Yes → 75% |
   | Closed Won | 100% | 98% | No |

**Step 2: Configure Forecast Categories**
1. **Commit**: Deals at "Negotiation" stage or later (75%+ confidence)
2. **Best case**: Deals at "Demo Completed" or "Proposal Sent" (35-60%)
3. **Pipeline**: All open deals

**Step 3: Set Up Team Hierarchy** (Enterprise)
1. Settings > Users & Teams > Create team hierarchy
2. Rep → Team Lead → Regional VP → CRO
3. Each manager sees rollup of their team's forecast
4. Breeze AI provides predicted close dates and confidence scores

**Step 4: Create Forecast Reports**
1. **Reports** > **Dashboards** > Create dashboard
2. Name: "Weekly Forecast Review"
3. Add reports:
   - Forecast by rep (table)
   - Weighted pipeline by stage (bar chart)
   - Deals closing this month (list)
   - Quarter-over-quarter comparison (line chart)
4. Schedule email delivery every Monday at 9 AM

### Tutorial 3: Conversation Intelligence for Sales Coaching

**Goal**: Use recorded calls and AI analysis to improve your team's sales conversations.

**Step 1: Enable Recordings**
1. **Settings** > **Sales** > **Calling** > Enable call recording
2. Choose consent method: Play consent tone before recording begins
3. Set retention policy: 90 days for coaching purposes

**Step 2: Train Your Team**
1. Ensure all sales reps use HubSpot Calling for outbound
2. Explain that recordings are for coaching, not surveillance
3. Show reps how to access their own recordings and scores
4. Reps can flag calls where they want specific feedback

**Step 3: Manager Review Process**
1. **Sales** > **Conversation Intelligence** > Review calls
2. Filter by: Rep, date range, call outcome
3. Listen to 2-3 calls per rep per week
4. Fill in coaching scorecard for each reviewed call
5. Assign coaching actions:
   - "Great discovery questions. Work on handling price objections."
   - "Talk-to-listen ratio was 70/30 — aim for 40/60"
   - "Missed the buying signal at 12:30 — discuss in 1:1"

**Step 4: Use AI Insights for Team Training**
1. Review Breeze AI's coaching suggestions
2. Identify common patterns across the team:
   - Are reps struggling with the same objection?
   - Are discovery questions being skipped?
   - Is the value proposition being communicated clearly?
3. Create training session based on patterns
4. Build call playlists for onboarding new hires: "Best Discovery Calls"

### Tutorial 4: Advanced Quote-to-Close Workflow

**Goal**: Automate the quote-to-close process with approvals, e-signatures, and payment collection.

**Step 1: Create Quote Templates**
1. **Settings** > **Sales** > **Quotes** > **Templates**
2. Create 3 templates: Standard, Express (under $5k), Enterprise
3. Each template includes: Header with logo, line items, terms, signature block

**Step 2: Configure Approval Flows**
1. Auto-approve: Deals under $10,000 with standard terms
2. Manager approval: Deals $10,000-$50,000 or discount > 20%
3. VP approval: Deals $50,000-$250,000 or custom terms
4. Executive approval: Deals over $250,000

**Step 3: Build Approval Workflow**
1. Trigger: Quote created with amount > $10,000
2. Action: Set quote status to "Pending Approval"
3. Action: Send notification to approver with quote details
4. Action: If approved in 24 hours → send to customer
5. Action: If not approved in 24 hours → notify requester

**Step 4: Automate Post-Signature Actions**
1. Trigger: Quote signed
2. Action: Move deal to "Closed Won"
3. Action: Attach signed PDF to deal record
4. Action: Create invoice (Commerce Hub)
5. Action: Enroll customer in onboarding sequence
6. Action: Notify fulfillment team via Slack

---

## Sales Metrics — What to Track

### Activity Metrics
| Metric | Formula | Target | Why It Matters |
|--------|---------|--------|---------------|
| Emails sent/day | Count | 40-60 | Volume drives pipeline |
| Calls made/day | Count | 30-50 | Direct outreach effectiveness |
| Meetings booked/week | Count | 3-5 | Opportunity creation rate |
| Activities per deal | Count | 8-12 | Engagement correlates with close rate |
| Time to first touch | Hours | < 1 hour | Speed-to-lead impacts conversion |
| Follow-up attempts | Count | 5-8 | Persistence increases contact rate |

### Pipeline Metrics
| Metric | Formula | Target |
|--------|---------|--------|
| Pipeline coverage | Pipeline value / Quota | 3-4× quota |
| Win rate | Won deals / Total closed deals | 25-35% average |
| Average deal size | Total won revenue / Won deals | Varies by industry |
| Sales cycle length | Avg days from creation to close | Varies by deal size |
| Stalled deals | Deals with no activity in 14+ days | < 10% |
| Stage conversion | % who move from stage N to N+1 | Monitor per stage |

### Rep Performance Metrics
| Metric | Formula | Target |
|--------|---------|--------|
| Quota attainment | Actual / Quota | 80-100% |
| Forecast accuracy | Actual vs forecasted | ±10% |
| Activities/rep/day | Total / Reps | 50-80 |
| Call-to-meeting conversion | Meetings / Calls | 5-10% |
| Pipeline created/rep | Value of new deals added | 3-4× quota |

### Sequence Metrics
| Metric | Target | Red Flag |
|--------|--------|---------|
| Open rate | 50-70% | < 40% |
| Reply rate | 10-20% | < 5% |
| Meeting booking rate | 3-8% | < 2% |
| Unsubscribe rate | < 0.5% | > 1% |
| Bounce rate | < 3% | > 5% |
| completion rate | N/A (goal is to unenroll early) | > 80% completion = no goals being met |

### Conversation Intelligence Metrics
| Metric | Target |
|--------|--------|
| Talk-to-listen ratio | 40/60 (rep/customer) |
| Discovery questions asked | 5+ per call |
| Objections handled | 80%+ handled well |
| Next steps defined | 90%+ of calls |
| Sentiment score | Positive or neutral in 80%+ of calls |