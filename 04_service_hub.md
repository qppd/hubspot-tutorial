# 4. Service Hub — Complete Tutorial

## Table of Contents
1. [Introduction to Service Hub](#introduction-to-service-hub)
2. [Ticketing — Complete Guide](#ticketing--complete-guide)
3. [Knowledge Base — Complete Guide](#knowledge-base--complete-guide)
4. [Chatbots & Conversational Bots — Complete Guide](#chatbots--conversational-bots--complete-guide)
5. [Feedback Surveys — Complete Guide](#feedback-surveys--complete-guide)
6. [Customer Success — Complete Guide](#customer-success--complete-guide)
7. [Help Desk Features — Complete Guide](#help-desk-features--complete-guide)
8. [Service Automation (Workflows) — Complete Guide](#service-automation-workflows--complete-guide)
9. [SLA Management — Complete Guide](#sla-management--complete-guide)
10. [Service Analytics & Reporting — Complete Guide](#service-analytics--reporting--complete-guide)
11. [Breeze AI in Service Hub](#breeze-ai-in-service-hub)
12. [Limits That Matter](#limits-that-matter)
13. [Common Gotchas](#common-gotchas)
14. [Use Cases](#use-cases)

---

## Introduction to Service Hub

Service Hub transforms customer support from a cost center into a growth driver. Instead of just answering tickets, Service Hub helps you track satisfaction, build a knowledge base, automate responses, and identify at-risk customers before they churn.

### What You Get by Tier

| Feature | Free | Starter | Pro | Enterprise |
|---------|------|---------|-----|------------|
| Ticketing | ✓ | ✓ | ✓ | ✓ |
| Ticket pipelines | 1 | 1 | 10 | 10 |
| Knowledge base | ✗ | ✓ | ✓ | ✓ |
| Chatbots | ✓ (basic) | ✓ | ✓ | ✓ |
| AI Chatbot (Breeze) | ✗ | ✗ | ✓ | ✓ |
| Feedback surveys | ✗ | ✓ | ✓ | ✓ |
| CSAT/NPS/CES | ✗ | ✓ | ✓ | ✓ |
| SLA management | ✗ | ✗ | ✗ | ✓ |
| Customer health scoring | ✗ | ✗ | ✗ | ✓ |
| Team email (shared inbox) | ✗ | ✓ | ✓ | ✓ |
| Automation (workflows) | ✓ (basic) | ✓ | ✓ | ✓ |
| Conversation routing | ✗ | ✗ | ✓ | ✓ |
| Goals & targets | ✗ | ✗ | ✓ | ✓ |

### Navigation

- **Service** > **Tickets** — Ticket management, pipelines, boards
- **Service** > **Knowledge Base** — Article creation, categories, management
- **Service** > **Chatflows** — Chatbot builder and management
- **Service** > **Feedback** — Survey templates, NPS/CSAT/CES, reporting
- **Service** > **Customer Success** — Health scores, renewals, risk (Enterprise)
- **Conversations** > **Inbox** — Shared team inbox (email, chat, social)
- **Automation** > **Workflows** — Service automation
- **Reports** > **Service** — Ticket, CSAT, NPS, SLA dashboards

---

## Ticketing — Complete Guide

### Ticket Record Structure

Tickets represent customer issues or requests. Key fields:

**Standard Fields**:
- **Ticket name**: Summary of the issue (required)
- **Status**: New, Waiting on Contact, Waiting on Us, Closed
- **Priority**: Low, Medium, High, Urgent
- **Type**: Question, Problem, Feature Request, Refund, Order Issue, Cancellation, Other
- **Pipeline**: Which support pipeline it belongs to
- **Ticket owner**: The support agent assigned
- **Source**: Email, Chat, Phone, Form, Internal, Social
- **Time to first response**: Automated SLA metric
- **Time to close**: Automated SLA metric
- **Related contact/company**: Who submitted and what account
- **Associated deal**: If related to a specific deal

**Custom Fields**: Create custom properties specific to your support process.

### Creating Tickets

**Method 1: Email-to-Ticket**
1. **Settings** > **Service** > **Email to ticket**
2. Create a support email address: `support@yourcompany.com`
3. Emails to this address automatically become tickets
4. Subject line → ticket name
5. Email body → ticket description
6. Sender → linked to existing contact or new contact created
7. Attachments → attached to the ticket

**Method 2: Form Submission**
1. Create a "Contact Support" form
2. Fields: Subject, Description, Priority, Attachment
3. Form submission creates a ticket automatically
4. Workflow can trigger on creation for routing

**Method 3: Chatbot**
1. Chatbot conversation ends with "Create a ticket"
2. Conversation transcript becomes ticket description
3. Contact auto-linked to the ticket

**Method 4: Manual Creation**
1. **Service** > **Tickets** > Create ticket
2. Enter ticket details
3. Associate to contact and company
4. Click Create

**Method 5: Automation/Workflow**
- Workflow action: "Create a ticket"
- Useful for: Failed payment → auto-create billing ticket
- Deal closed won → auto-create onboarding ticket

### Ticket Statuses Explained

| Status | Meaning | Next Step |
|--------|---------|-----------|
| **New** | Ticket created, not yet assigned or reviewed | Assign owner, acknowledge |
| **Waiting on Contact** | Agent needs information from customer | Follow up with customer |
| **Waiting on Us** | Agent is actively working on the solution | Resolve, update customer |
| **Closed** | Issue resolved or no longer actionable | Confirm closure, send survey |

### Ticket Priority Levels

| Priority | Meaning | Response SLA |
|----------|---------|-------------|
| **Low** | General inquiry, nice-to-have | 24-48 hours |
| **Medium** | Common issue, functional impact | 8-24 hours |
| **High** | Major functionality affected | 2-4 hours |
| **Urgent** | System down, data loss, security issue | < 1 hour |

### Ticket Pipelines

Separate pipelines for different support flows:

**Example pipelines**:
| Pipeline | Used For | Stages |
|----------|----------|--------|
| Standard Support | General customer issues | New → Open → In Progress → Resolved → Closed |
| Billing | Payment and invoicing | New → Review → Contact Customer → Resolved → Closed |
| Escalations | Critical issues | New → Triage → Assigned → Escalated → Resolved → Closed |
| Internal | QA items, bugs | New → Assessed → In Dev → QA → Deployed |

**Creating ticket pipelines**:
1. **Settings** > **Data Management** > **Pipelines** > **Tickets**
2. Create pipeline, add stages, set stage rules

### Ticket Automation

**Automation rules** (without workflows):
- Auto-close tickets after N days of inactivity
- Auto-reply with "We received your request" on new tickets
- Auto-assign based on ticket type (Billing goes to billing team)

### Ticket Collaboration

Multiple agents can work on a ticket:
- **Internal notes**: Notes visible only to agents, not customer
- **Mentions**: @mention another agent to bring them in
- **CC/BCC**: Include other agents on email replies
- **Ticket visibility**: Teams can have ticket-level permissions

---

## Knowledge Base — Complete Guide

### What is a Knowledge Base?

A KB is a self-service library of help articles. Customers can search and read articles to solve their own issues, reducing ticket volume.

### Creating Articles — Step-by-Step

1. **Service** > **Knowledge Base** > Create article
2. **Title**: Clear, search-optimized (e.g., "How to reset your password")
3. **Content**: Rich text editor with:
   - Formatting: Bold, italic, lists, quotes, code blocks
   - Images: Upload, URL, or AI-generated
   - Videos: Embed YouTube, Wistia, or MP4
   - Tables: For comparison or pricing data
   - Link to other articles: Internal linking
   - Note/Info/Warning callout boxes
   - Step-by-step numbered instructions
4. **Categories**: Group related articles (Getting Started, Account, Billing, Troubleshooting)
5. **Tags**: Additional keywords for search
6. **SEO settings**:
   - Page title
   - Meta description
   - URL slug
   - NOINDEX option (for internal-only articles)
7. **Author**: Display name shown on article
8. **State**: Draft → Published (or schedule for later)
9. **Domain**: Choose which connected domain the KB lives on

### KB Structure

**Best practices for KB organization**:

```
Knowledge Base
├── Getting Started
│   ├── Creating your account
│   ├── Setting up your profile
│   └── First project guide
├── Account Management
│   ├── Billing & Plans
│   ├── Changing your password
│   └── Deleting your account
├── Troubleshooting
│   ├── Login issues
│   ├── Payment failures
│   └── Error codes
└── FAQs
    ├── What's included in Pro plan?
    └── How do I cancel?
```

### KB Search

- Full-text search across all articles
- Search results ranked by relevance and popularity
- Auto-suggest as customer types
- "Did this help?" feedback on each article
- Search analytics: What are customers looking for?

### Multi-Language KB

1. Publish article in primary language
2. Click "Add translation"
3. Choose target language
4. Add translated content
5. URL structure: `/en/article`, `/es/article`, `/fr/article`
6. Language switcher on KB homepage

### KB Reporting

- **Article performance**: Views, helpful votes, search appearances
- **Top articles**: Most viewed, highest search appearances
- **Zero-result searches**: What customers search for but can't find
- **Ticket deflection**: How many customers found the answer before filing a ticket

---

## Chatbots & Conversational Bots — Complete Guide

### Types of Chatbots

**1. Flow-based chatbot**:
- Pre-built conversation flows with decision trees
- Triggers: Time on page, URL, scroll %, page exit
- Actions: Route to sales, create ticket, answer FAQ, collect info
- Best for: Simple, predictable conversations (FAQ, lead capture)

**2. AI Agent (Breeze AI chatbot)**:
- LLM-powered conversational AI with natural language understanding
- Access to your KB articles and CRM data
- Can handle complex, multi-turn conversations
- Escalates to human when needed
- Best for: Tier-1 support, complex troubleshooting

### Creating a Flow-Based Chatbot

1. **Service** > **Chatflows** > Create chatflow
2. Choose type:
   - **Website chat**: Live chat widget on your site
   - **Messaging chat**: For WhatsApp, Facebook Messenger (beta)
   - **Phone/IVR**: Automated phone tree (limited)
3. **Chatflow type**: Simple flow, custom flow, or round-robin
4. **Build the flow**:

   **Example: FAQ Bot**
   ```
   [Welcome]
   "Hi {{ contact.firstname }}! What can I help with?"
   
   [Button options]
   ○ Billing question
   ○ Technical issue
   ○ Talk to a human
   
   [Billing path]
   "Common billing questions:"
   ○ "How do I update my payment method?"
   ○ "Can I get a refund?"
   ○ "Talk to billing team"
   
   [Technical issue path]
   "Describe your issue briefly:"
   [Free text input]
   → Search KB for matches
   → Suggest relevant articles
   → Offer to create ticket
   
   [Talk to human]
   → Send to live chat queue
   ```

5. **Trigger rules**:
   - **Page URL**: Show on specific pages (e.g., /pricing)
   - **Time on page**: Show after 30 seconds
   - **Scroll**: Show when 50% scrolled
   - **Exit intent**: Show when mouse moves to close tab
   - **Device type**: Desktop only, mobile only, or both
   - **Visitor type**: New vs returning, known vs unknown
   - **Custom property**: Show only to Pro/Enterprise customers

6. **Targeting**: Which pages to show (specific pages, all pages, or all except specific pages)

7. **Routing**: Who gets the conversation?
   - **Round-robin**: Distribute evenly among team
   - **Skills-based**: Route technical issues to tech team
   - **Custom rules**: Route based on contact properties

8. **Off-hours behavior**: What happens when no agents are available?
   - Show "We're offline" message with hours
   - Offer to leave a message (creates a ticket)
   - Suggest KB articles

9. **Publish**: Add code snippet to website or use HubSpot tracking code

### AI Agent (Breeze Chatbot)

1. **Service** > **Chatflows** > Create chatflow > **AI Agent**
2. **Knowledge sources**: Connect your KB articles
3. **Personality**: Friendly, Professional, Casual — defines how the bot communicates
4. **Capabilities**:
   - Answer questions from KB
   - Check order status (CRM data)
   - Update subscription (if permitted)
   - Create tickets
   - Book meetings
   - Check billing info
5. **Guardrails**:
   - Topics it CAN discuss: Products, support, billing, account
   - Topics it CANNOT discuss: Legal advice, medical advice, pricing for competitors
   - Confidentiality: Never share customer's personal data with other customers
   - Escalation: When to transfer to human (sentiment analysis, repeated questions, specific trigger words)
6. **Human handoff**: Smooth transition to live agent with full conversation history
7. **Publish**: Same as flow-based chatbot

---

## Feedback Surveys — Complete Guide

### Survey Types

**1. CSAT (Customer Satisfaction Score)**:
- Question: "How satisfied were you with the support you received?"
- Scale: 1-5 (Very Dissatisfied → Very Satisfied)
- Sent after ticket closure
- Goal: Measure satisfaction with specific interactions

**2. NPS (Net Promoter Score)**:
- Question: "How likely are you to recommend us to a friend or colleague?"
- Scale: 0-10
- Categories: Promoters (9-10), Passives (7-8), Detractors (0-6)
- NPS = % Promoters − % Detractors
- Sent periodically (quarterly, post-onboarding, or post-milestone)

**3. CES (Customer Effort Score)**:
- Question: "How easy was it to resolve your issue?"
- Scale: 1-5 (Very Difficult → Very Easy)
- Sent after specific interactions (ticket closed, feature used)
- Goal: Measure friction in the customer experience

### Creating a Survey

1. **Service** > **Feedback** > **Surveys** > Create survey
2. Choose type: CSAT, NPS, or CES
3. **Design**:
   - Question text: Customizable
   - Scale labels: Customize the endpoint labels
   - Follow-up question: "What's the main reason for your score?" (open text)
   - Branding: Logo, colors, font (matches your brand kit)
   - Layout: Single question, multi-step, inline
4. **Distribution**:
   - **Email**: Sent automatically after ticket closure (CSAT) or on schedule (NPS)
   - **Website**: Embed survey on pages
   - **Chat**: Ask after chatbot interaction
   - **Link**: Shareable survey URL
5. **Timing**:
   - CSAT: 1 hour after ticket closed
   - NPS: 7 days after onboarding completed
   - CES: Immediately after resolution
6. **Automation rules**:
   - Send only if ticket was resolved (not rejected)
   - Send only one survey per ticket
   - Don't send if contact already received survey in last 30 days

### Survey Analytics

- **Response rate**: % of surveys sent vs completed
- **Score trends**: Over time, by team, by agent
- **Score breakdown**: Distribution of responses
- **Comments**: Open-text analysis of follower responses
- **Benchmark**: Compare to industry averages (when available)
- **Segmentation**: Scores by plan type, customer age, region

---

## Customer Success — Complete Guide

### Customer Health Scoring (Enterprise)

Predict which customers are at risk of churning and which are primed for expansion.

**Health Score Components**:
| Factor | Weight | Example |
|--------|--------|---------|
| Product usage | 30% | Logged in 15+ days this month |
| Support interactions | 20% | Open tickets < 2, priority < High |
| Engagement | 20% | Email opens, meeting attendance, webinar |
| Payment status | 15% | No overdue invoices |
| NPS/CSAT | 15% | Recent survey score > 4 |

**Health statuses**:
| Status | Score | Action |
|--------|-------|--------|
| Healthy | 80-100 | Upsell, cross-sell, ask for referral |
| Neutral | 50-79 | Monitor, send educational content, check-in |
| At Risk | 20-49 | Reach out, schedule health check, offer training |
| Critical | 0-19 | Immediate executive intervention, retention offer |

**Setting up health scoring**:
1. **Service** > **Customer Success** > **Health Scoring**
2. Define criteria and weights
3. Test against known at-risk customers
4. Adjust weights based on historical churn data
5. Turn on automated scoring

### Renewal Management

Track and manage subscription renewals:
- **Service** > **Customer Success** > **Renewals**
- See all customers with upcoming renewals
- Filter by: Time to renewal, health score, deal value
- Create tasks: "Renewal call — 30 days before expiration"
- Workflow: Auto-notify CSM when renewal is approaching

### Customer Lifecycle

Track customers through stages:
| Stage | Description | Activities |
|-------|-------------|------------|
| Onboarding | First 30 days | Welcome call, setup, training |
| Adoption | Months 1-3 | Feature adoption, usage monitoring |
| Growth | Months 3-12 | Upsell, cross-sell, advocacy |
| Maturity | 12+ months | Expansion, referrals, case studies |
| Risk | Churn signals detected | Retention intervention |
| Churned | Customer lost | Win-back campaign later |

---

## Help Desk Features — Complete Guide

### Team Email (Shared Inbox)

A shared email address for your support team:

1. **Conversations** > **Inbox** > Connect email
2. Connect `support@yourcompany.com` or `help@yourcompany.com`
3. Emails to this address appear in the shared inbox
4. Any team member can respond
5. Responses are tracked as interactions on the contact timeline

**Inbox features**:
- **Assignment**: Assign conversations to specific agents
- **Status**: Open, Pending, Closed
- **Priority**: Standard, High, Urgent
- **Snooze**: Re-open at specific time or when contact replies
- **Canned responses**: Pre-written replies for common questions
- **Internal notes**: Notes visible only to agents
- **Mentions**: @mention to alert another agent
- **Typing indicator**: See when another agent is typing
- **Response templates**: Quick replies using saved templates

### Automation in Help Desk

**Preset responses**: Create snippets for common replies:
- "We've received your request and will respond within 24 hours."
- "Can you please share a screenshot of the issue?"
- "This has been escalated to our billing team."

**Assignment rules**:
- Auto-assign conversations to available agents (round-robin)
- Assign based on conversation source (email vs chat)
- Assign based on contact properties (plan type, industry)

**Auto-reply**: Send automatic acknowledgment when new conversation arrives

---

## Service Automation (Workflows) — Complete Guide

### Service Workflow Triggers

| Trigger Type | Example |
|-------------|---------|
| Ticket property changed | Priority becomes "Urgent" |
| Ticket created | New ticket from form submission |
| SLA breached | Time to first response exceeded |
| Survey submitted | CSAT score is 1 or 2 (dissatisfied) |
| Contact property | Customer lifecycle becomes "At Risk" |
| Deal property | Renewal deal stage changes |

### Service Workflow Actions

| Action | Example |
|--------|---------|
| Send email | "Thank you for your patience" auto-reply |
| Set property value | Set ticket priority to "High" |
| Create task | "Follow up with customer about resolution" |
| Enroll in sequence | "Post-resolution check-in" sequence |
| Trigger webhook | Notify external system (Jira, PagerDuty) |
| Create ticket | Auto-create for internal QA |
| Assign owner | Assign to specific team based on ticket type |
| Branch | If ticket type = "Billing" → send to billing team |

### Example: Urgent Ticket Workflow

1. **Trigger**: Ticket priority is set to "Urgent"
2. **Branch**: If ticket source is "Email"
   - Yes: Send auto-reply "We've escalated your issue"
   - No: Continue silently
3. **Action**: Set ticket owner to "Escalations" team
4. **Action**: Send Slack notification to #urgent-alerts
5. **Action**: Set property "Escalation time" to current timestamp
6. **Goal**: Ticket status = "Resolved"
7. **Expiration**: If not resolved in 4 hours → notify manager

### Example: Post-Resolution Check-in

1. **Trigger**: Ticket status becomes "Closed"
2. **Delay**: Wait 24 hours
3. **Send survey**: CSAT survey
4. **Branch**: If CSAT score < 3 (dissatisfied)
   - Action: Create task for agent — "Follow up with unhappy customer"
   - Action: Set property "Needs retention call" = true
5. **Branch**: If CSAT score ≥ 4 (satisfied)
   - Action: Add to "Happy Customers" list for referrals

---

## SLA Management — Complete Guide

### What are SLAs?

Service Level Agreements define response and resolution time commitments for tickets.

**Common SLA metrics**:
- **First response time**: Time from ticket creation to first agent response
- **Time to close**: Time from ticket creation to closure
- **Resolution time**: Time from first response to resolution
- **Breach**: When SLA target is not met

### Setting Up SLAs (Enterprise)

1. **Settings** > **Service** > **SLA Management**
2. Create SLA:
   - **Name**: "Standard Support SLA"
   - **Applies to**: All tickets, specific pipelines, specific ticket types
   - **Targets**:
     - First response: Within 4 hours
     - Time to close: Within 24 hours
   - **Business hours**: Mon-Fri, 9 AM-6 PM (or 24/7 for premium)
   - **Priority adjustments**: Urgent = 1 hour, High = 4 hours, Medium = 8 hours, Low = 24 hours
3. **Breach actions**:
   - Send email to ticket owner: "SLA breach imminent"
   - Notify manager
   - Escalate ticket to senior agent
   - Change priority automatically
4. **Save and activate**

### SLA Reporting

- **SLA compliance %**: Tickets resolved within SLA targets
- **SLA breaches**: Tickets that missed targets
- **SLA by pipeline**: Which pipelines have best/worst compliance
- **SLA by agent**: Individual performance
- **SLA trends**: Over time, by team
- **Time to first response**: Average, median, percentile breakdown

---

## Service Analytics & Reporting — Complete Guide

### Pre-Built Service Dashboards

**Ticket volume report**:
- Tickets created per day/week/month
- Tickets by status, priority, type, pipeline
- Ticket trends over time

**Agent performance**:
- Tickets closed per agent
- Average response time per agent
- Average resolution time per agent
- CSAT score per agent
- Ticket reopen rate

**CSAT & NPS dashboards**:
- Overall score trends
- Score by agent, team, plan type
- Score distribution (how many rated 1-5)
- Comment word cloud

**SLA compliance**:
- % within SLA
- Breaches by type, priority, agent
- Time to first response
- Time to resolution

### Custom Service Reports

Create reports combining ticket data with contacts, companies, and deals:
- "Show me tickets from companies with revenue over $1M"
- "Tickets created by customers who opened a support case in the last 30 days"
- "CSAT scores for customers on Professional plan"
- "Resolution time by product category"

### Key Metrics to Track

| Metric | What It Measures | Target |
|--------|-----------------|--------|
| Ticket volume | How many issues are coming in | Trend monitoring |
| First response time | How fast agents acknowledge | < 1 hour |
| Time to resolution | How fast issues are solved | < 24 hours |
| CSAT | Customer satisfaction with support | > 4.0 |
| NPS | Overall customer loyalty | > 50 |
| Ticket reopen rate | Were issues really resolved? | < 10% |
| KB article views | Are customers self-serving? | Increasing trend |
| Ticket deflection | % of visitors using KB instead of tickets | > 20% |
| Agent utilization | % of agent time on tickets | 70-80% |

---

## Breeze AI in Service Hub

### AI Ticket Summaries

When a ticket is being worked on, Breeze AI provides:
- **Summary**: What the issue is about
- **Key points**: Most important details from the conversation
- **Suggested actions**: What the agent should do next
- **Related KB articles**: Articles that might help resolve the issue

### AI Agent (Chatbot)

See [Chatbots section](#ai-agent-breeze-chatbot) above. The AI Agent can:
- Resolve common issues autonomously (password resets, account updates)
- Deflect tickets by answering from KB
- Create tickets when unable to resolve
- Seamlessly hand off to human agents with full context

### AI Email Replies

When responding to ticket emails, Breeze AI suggests:
- Complete response drafts based on the customer's question
- Tone adjustments: Make it warmer, more professional, or shorter
- Quick actions: "Mark as resolved", "Create follow-up task"

### Predictive Churn Detection

Breeze AI analyzes patterns to flag at-risk customers:
- Decreased product usage
- Increased support ticket volume
- Negative sentiment in support conversations
- Missed payments
- No engagement with success team

---

## Limits That Matter

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Ticket pipelines | 1 | 1 | 10 | 10 |
| Knowledge base articles | — | 50 | Unlimited | Unlimited |
| Knowledge base domains | — | 1 | 5 | 10 |
| Chatbot flows | 1 | 3 | 10 | Unlimited |
| Feedback surveys | — | 5 | Unlimited | Unlimited |
| Team emails | — | 1 | 3 | 10 |
| SLA targets | — | — | — | Unlimited |
| Customer health scores | — | — | — | Unlimited |
| Service dashboards | 3 | 5 | 15 | Unlimited |
| Ticket automation rules | 5 | 20 | 200 | Unlimited |
| Agent seats | Unlimited | Unlimited | Unlimited | Unlimited |

---

## Common Gotchas

### 1. Email-to-Ticket Formatting
Emails to the ticket address convert the entire email body into the ticket description. Forwarded emails with long chains of previous responses included can create messy tickets.

### 2. KB Search Accuracy
KB search relies on article titles and content. Articles with poor titles (e.g., "Issue #42") won't be found by customers using natural language.

### 3. Chatbot Off-Hours
If you don't configure off-hours behavior, the chatbot simply shows "No agents available" which frustrates customers. Always set up a fallback (leave message, suggest KB, offer callback).

### 4. Survey Fatigue
Don't send surveys after every single interaction. Limit to 1 CSAT per ticket and 1 NPS per quarter per contact. Multiple surveys annoy customers and lower response rates.

### 5. SLA Business Hours
SLA calculations depend on business hours. If your agents work 9-5 but your system runs 24/7, a ticket created at 10 PM might appear to be breaching SLA when no agent was online.

### 6. Ticket Reopen
When a customer replies to a closed ticket, it can automatically reopen. Configure reopen rules: reopen if reply within 7 days, or create a new ticket for older threads.

### 7. AI Agent Limitations
The AI Agent is powerful but can't do everything. It doesn't have access to external systems (payment gateways, shipping carriers, product APIs) unless you build custom integrations.

### 8. Health Score Accuracy
Health scores are only as good as your data quality. If product usage data isn't syncing or surveys aren't being sent, health scores will be incomplete or misleading.

---

## Service Hub Tutorials

### Tutorial 1: Setting Up a Complete Help Desk

**Goal**: Configure a fully functional help desk with ticket pipelines, email-to-ticket, auto-assignment, SLA tracking, and performance dashboards.

**Step 1: Configure Email-to-Ticket**
1. **Settings** > **Service** > **Email-to-ticket** > Set up address
2. Choose your support email: `support@yourcompany.com`
3. Configure: New email → Create ticket (or existing thread → update ticket)
4. Set default pipeline: "Standard Support"
5. Default ticket type: "Question" (adjust per topic detection)
6. Default priority: "Medium" (adjust per sender property)

**Step 2: Build Ticket Pipelines**
1. **Settings** > **Data Management** > **Pipelines** > **Tickets**
2. Create pipeline: "Standard Support"
   - Stage 1: New (auto-assigned)
   - Stage 2: Open (agent acknowledged)
   - Stage 3: In Progress (agent working)
   - Stage 4: Waiting on Customer (need info)
   - Stage 5: Resolved (solution provided)
   - Stage 6: Closed (customer confirmed)
3. Create pipeline: "Escalations"
   - Stage 1: Triage (initial assessment)
   - Stage 2: Technical Review (engineering review)
   - Stage 3: Development (bug fix in progress)
   - Stage 4: QA (testing fix)
   - Stage 5: Deployed (fix live)
   - Stage 6: Confirmed Closed (customer verified)

**Step 3: Set Up Auto-Assignment Rules**
1. **Settings** > **Service** > **Ticket assignment**
2. Create rules:
   - Ticket type = "Billing" → assign to Billing team (round-robin)
   - Priority = "Urgent" → assign to Senior team (round-robin)
   - Company size > 500 employees → assign to Enterprise support team
   - Default: Any unassigned → assign to General support (round-robin)

**Step 4: Create Canned Responses**
1. **Conversations** > **Canned Responses** > Create
2. Common responses:
   - "Thanks for reaching out. We'll respond within 4 hours."
   - "Can you please provide a screenshot of the error?"
   - "We've escalated this to our engineering team. Reference: TICKET-XXXX"
   - "This issue is resolved. Please confirm or respond within 3 days."

**Step 5: Build Service Dashboard**
1. **Reports** > **Dashboards** > Create dashboard
2. Name: "Service Desk Performance"
3. Add reports:
   - Tickets created vs resolved (daily line chart)
   - Open tickets by priority (bar chart)
   - Average first response time (single number)
   - CSAT score trend (line chart)
   - Agent workload (table: agent name, open tickets, avg response time)
   - SLA compliance rate (gauge chart: target 95%+)
4. Schedule email to service manager every morning at 8 AM

### Tutorial 2: Building an AI-Powered Support Bot

**Goal**: Create a chatbot that autonomously resolves common issues using Breeze AI and your knowledge base.

**Step 1: Build Your Knowledge Base**
1. **Service** > **Knowledge Base** > Create article
2. Create articles for the 10 most common issues:
   - How to reset password
   - How to update billing info
   - How to cancel subscription
   - How to invite team members
   - Troubleshooting login errors
   - Understanding your invoice
   - etc.
3. For each article: Write clear title, step-by-step instructions, add images/screenshots, categorize correctly
4. Publish and verify search works

**Step 2: Create AI Agent**
1. **Service** > **Chatflows** > Create chatflow > AI Agent
2. Name: "Support Bot — Tier 1"
3. Connect knowledge base: Select all published articles
4. Set personality: "Friendly and helpful. Explain technical concepts simply."
5. Capabilities:
   - Answer questions from KB ✓
   - Create tickets ✓
   - Check order status ✓
   - Book meetings ✓
   - Update account info (password, email) ✓
6. Guardrails:
   - CAN discuss: Account management, billing, troubleshooting, features
   - CANNOT discuss: Legal terms, medical advice, competitor pricing
   - Always escalate if customer asks for refund (requires human)
   - Always escalate if customer expresses frustration 3+ times

**Step 3: Configure Handoff Rules**
1. AI Agent → Human handoff conditions:
   - Customer says "talk to agent" or "human"
   - Customer expresses frustration (sentiment analysis)
   - Same question asked 3+ times (AI can't resolve)
   - Request involves refund or account deletion
2. Handoff behavior: Transfer full conversation history to agent
3. Agent sees: Chat transcript, AI suggestions for resolution, related KB articles

**Step 4: Monitor Bot Performance**
1. **Service** > **Chatflows** > Select your bot > Analytics
2. Key metrics to track:
   - Resolution rate: % of conversations resolved by bot without human handoff
   - Handoff rate: % escalated to human
   - Customer satisfaction: CSAT for bot vs human interactions
   - Average conversation length: Bot vs human
   - Common unresolved topics: What people ask that bot can't answer → create new KB articles

### Tutorial 3: Customer Health Scoring & Proactive Retention

**Goal**: Identify at-risk customers before they churn using health scoring and automated interventions.

**Step 1: Define Health Score Components**
1. **Service** > **Customer Success** > **Health Scoring** (Enterprise)
2. Add component: Product Usage — 30% weight
   - Active in last 7 days: 100 points
   - Active in last 30 days: 60 points
   - Active in last 90 days: 30 points
   - No activity in 90+ days: 0 points
3. Add component: Support Engagement — 25% weight
   - 0 open tickets: 100 points
   - 1-2 open tickets (normal): 70 points
   - 3-5 open tickets: 30 points
   - 5+ open tickets: 0 points
4. Add component: Payment Status — 25% weight
   - Up to date: 100 points
   - Past due < 15 days: 50 points
   - Past due 15-30 days: 20 points
   - Past due 30+ days: 0 points
5. Add component: NPS/CSAT — 20% weight
   - NPS 9-10 or CSAT 5: 100 points
   - NPS 7-8 or CSAT 4: 70 points
   - NPS 0-6 or CSAT 1-3: 20 points
   - No survey data: 50 points (neutral)

**Step 2: Set Health Score Thresholds**
- Healthy (80-100): Green — Good standing, upsell ready
- Neutral (50-79): Yellow — Monitor, send check-in
- At Risk (20-49): Orange — Proactive outreach needed
- Critical (0-19): Red — Immediate intervention required

**Step 3: Build Proactive Workflows**

**Workflow: At-Risk Customer Alert**
1. Trigger: Health score drops below 50 (becomes "At Risk")
2. Actions:
   - Create high-priority task for CSM: "Health check — [company name]"
   - Send notification to CSM via Slack or email
   - Set contact property "Risk Flag" = true
   - If no action in 48 hours: Escalate to CS manager

**Workflow: Churn Prevention Sequence**
1. Trigger: Health score "At Risk" for 7+ days
2. Actions:
   - Step 1: Send personalized email from CSM with usage tips
   - Step 2: 3 days later — Offer free training session
   - Step 3: 5 days later — Offer discount or extended trial
   - Step 4: 7 days later — Create task: "Executive retention call needed"

**Workflow: Happy Customer → Upsell Opportunity**
1. Trigger: Health score > 85 for 30+ days
2. Actions:
   - Add to "Expansion Candidates" list
   - Set property "Upsell Ready" = true
   - Notify account manager
   - Enroll in upsell sequence

### Tutorial 4: Building a Self-Service Customer Portal

**Goal**: Create a knowledge base and support portal that empowers customers to help themselves, reducing ticket volume.

**Step 1: Organize Knowledge Base**
1. **Service** > **Knowledge Base** > Manage categories
2. Create categories:
   - Getting Started (onboarding, setup, first steps)
   - Account Management (profile, password, settings)
   - Billing & Plans (invoices, upgrades, cancellations)
   - Troubleshooting (common errors, fixes)
   - FAQs (frequent questions)
3. Create content for each category — aim for 5+ articles per category
4. Set up SEO: Custom meta descriptions, URL slugs, NOINDEX for internal-only articles

**Step 2: Configure KB Search**
1. KB search is automatic — HubSpot indexes all published articles
2. Optimize articles for search:
   - Use clear, question-based titles: "How do I reset my password?"
   - Include keywords: "password reset, forgot password, can't log in"
   - Use step-by-step formatting with numbered lists
   - Add "See also" links to related articles
3. Check "Zero result searches" in KB analytics — create content for what customers can't find

**Step 3: Measure Ticket Deflection**
1. Create report: "KB Influence on Tickets"
2. Metrics to track:
   - KB article views before ticket creation
   - % of visitors who find answer in KB vs filing ticket
   - Top deflected issues: Articles with high views and low related tickets
3. Goal: 20%+ of potential tickets deflected by KB articles

---

## Service Hub Metrics — What to Track

| Category | Metric | Target | Why |
|----------|--------|--------|-----|
| **Volume** | Tickets created/week | Varies | Identifies trends, seasonality |
| **Volume** | Tickets by source | Varies | Which channels are busiest? |
| **Efficiency** | First response time | < 1 hour | Impact on CSAT |
| **Efficiency** | Average resolution time | < 24 hours | Efficiency metric |
| **Efficiency** | Ticket reopen rate | < 10% | Quality of resolution |
| **Efficiency** | Agent utilization | 70-80% | Workload balance |
| **Quality** | CSAT score | > 4.0 / 5.0 | Customer happiness |
| **Quality** | NPS | > 50 | Overall loyalty |
| **Quality** | SLA compliance | > 95% | Meeting commitments |
| **Self-service** | KB article views | Increasing | Self-service adoption |
| **Self-service** | Ticket deflection rate | > 20% | KB preventing tickets |
| **Self-service** | Chatbot resolution rate | > 60% | AI handling issues |
| **Health** | Customer health score avg | > 70 | Portfolio health |
| **Health** | Churn rate (service-related) | < 5%/year | Retention success |