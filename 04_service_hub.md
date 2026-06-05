# 4. Service Hub

## What It Does
HubSpot Service Hub equips customer support and success teams with tools to manage tickets, build knowledge bases, automate responses (bots), collect feedback, and track CSAT/NPS. It turns support from reactive to proactive.

## Key Features

### Help Desk / Ticketing
- **Ticket management**: track, prioritize, and resolve customer requests
- **Ticket statuses**: New, Waiting on Contact, Waiting on Us, Closed
- **Ticket priorities**: Low, Medium, High, Urgent
- **Ticket types**: Question, Problem, Feature Request, Refund, Cancellation, Other
- **Ticket pipelines**: customize stages for your workflow
- **Pipeline stages**: Up to 10 ticket pipelines (Service Hub Pro+)
- **SLA management**: set, track, and report on response and resolution SLAs
- **SLA breaching notifications**: email and in-app alerts
- **Auto-assignment**: round-robin or rules-based ticket assignment
- **Ticket routing**: route to teams by topic, customer tier, product type
- **Private notes**: internal notes on tickets (not visible to customer)
- **Customer portal**: customers can view and respond to their tickets
- **Conversations**: unified inbox for live chat, email, and bot messages

### Knowledge Base
- **Article creation**: rich text editor with modules (Pro+)
- **AI article generation from tickets**: auto-generate draft knowledge base articles from resolved tickets — Breeze AI extracts the question, solution, and context from ticket threads and produces a complete article draft ready for review and publishing
- **Article categorization**: by topic, product, or custom categories
- **SEO settings**: meta description, URL slug, canonical URL
- **Smart content**: show different articles based on contact properties
- **Domain management**: custom domain for KB site
- **KB analytics**: article views, search terms, helpfulness rating, feedback
- **AI content suggestions**: generate draft articles from existing tickets
- **Content organization**: nested categories, table of contents
- **Password protection**: restrict KB to logged-in customers
- **Multi-language**: publish in multiple languages
- **Search**: built-in full-text search
- **Inline feedback**: thumbs up/down on each article
- **Deep link from bots**: chatbot can automatically suggest KB articles

### Chatbots (Conversational Bots)
- **Bot types**: ticket creation bot, lead qualification bot, meeting booking bot, website chat bot, knowledge base bot
- **Simple bot builder**: rule-based question/answer flows (Free)
- **Advanced bots**: conditional branching, API calls (Pro+)
- **Breeze AI chatbot responses**: LLM-powered replies that understand natural language and intent beyond rigid rule trees — bots can answer complex questions, paraphrase, handle typos, and hold contextual multi-turn conversations without every branch being hand-written
- **Bot handoff**: escalate to human agent when bot can't resolve
- **Bot analytics**: resolved vs handed-off, conversation logs
- **Multi-language bots**: create flows in different languages
- **Bot routing**: route based on contact properties, page URL, time of day
- **Auto-reply**: instant response outside business hours
- **FAQ bot**: answer common questions from KB articles (Pro+)
- **Bot actions**: create ticket, subscribe to list, set property, trigger webhook
- **Bot triggers**: time on page, scroll %, exit intent, specific page visit

### Customer Feedback
- **CSAT surveys**: send after ticket resolution — "How satisfied were you with our support?"
  - Emoji scale (1-5) or numeric scale
  - Follow-up comment optional
- **NPS surveys**: "How likely are you to recommend us?" (0-10 scale)
  - Detractor (0-6), Passive (7-8), Promoter (9-10)
  - Triggered after closed won deals or specific lifecycle transitions
- **CES surveys**: Customer Effort Score
- **Survey templates**: pre-built templates for common use cases
- **Survey triggers**: property change, workflow enrollment, ticket close
- **Survey analytics**: response rate, score trends, segment by team/product
- **Feedback reporting**: sentiment tracking over time, by rep, by issue type
- **Predictive NPS/CSAT scoring**: Breeze AI analyzes ticket language, sentiment, resolution time, and historical patterns to predict a customer's likely CSAT or NPS score before the survey is even sent — flag at-risk accounts proactively

### Customer Success Workspace (Pro+)
- **Health scoring**: custom health score formulas based on usage, engagement, support history
- **Renewal tracking**: upcoming subscription renewals
- **Account overview**: single view of one customer's health, tickets, deals, activity
- **Customer journey**: timeline of all interactions across marketing, sales, and service
- **Playbooks for success**: guided workflows for onboarding, QBRs, renewals
- **Goal tracking**: track adoption milestones, usage goals
- **Upsell/cross-sell alerts**: auto-flag when customer behavior indicates expansion opportunity
- **Segmentation**: group customers by health tier (Healthy, At Risk, Churn Risk)
- **Automated check-ins**: set recurring checklists for customer success managers

### Multi-Channel Inbox
- **Email**: connect shared inbox (support@, help@, etc.)
- **Live chat**: website chat widget
- **Messaging channels (Pro+)**: Facebook Messenger, **WhatsApp** (full integration — connect WhatsApp Business Account, send/receive messages, share media/files, use templates for proactive outreach, reply from inbox, trigger workflows from WhatsApp messages), Instagram DM (limited)
- **Bot conversations**: seamlessly continue from bot → human
- **Omnichannel view**: all channels in one inbox with unified history
- **AI summarization**: Breeze AI auto-summarizes long conversation threads into a concise bullet-point synopsis so agents can catch up instantly without scrolling through pages of chat history
- **Macros**: pre-written replies for common scenarios
- **AI-suggested reply macros**: Breeze AI proposes relevant reply macros based on the conversation context, ticket type, and customer history — agents can insert with one click instead of hunting through a list
- **Canned responses**: shared snippets across team
- **Collision detection**: see when another agent is viewing/replying to a ticket
- **Team mentions**: @mention to pull in another agent
- **Status management**: online, away, offline with auto-response
- **Assignment rules**: round-robin, skill-based, least-recently-assigned

### Automations
- **Ticket automation**: auto-create tickets from email, chat, web form
- **Email-to-ticket**: forward emails to a pipeline address → auto-creates ticket
- **Workflow triggers**: ticket creation, property change, pipeline stage change, SLA breach
- **Workflow actions**: send email, assign ticket, set priority, notify team, webhook
- **SLA escalations**: auto-escalate tickets approaching SLA breach
- **Automatic ticket closure**: close tickets after X days of no customer response
- **Feedback survey automation**: auto-send after ticket resolution
- **Routing rules**: auto-assign based on expertise, load balancing, custom rules

### Reporting
- **Ticket analytics**: volume by channel, type, priority, rep, time to close
- **Team productivity**: tickets closed per rep, average response time, resolution time
- **SLA metrics**: SLA compliance %, breached tickets, average breach time
- **Customer satisfaction**: CSAT, NPS, CES trends
- **Knowledge base analytics**: most viewed articles, top search queries, article helpfulness
- **Bot performance**: resolution rate, hand-off rate, conversations handled
- **Custom dashboards**: build and share with stakeholders
- **Sentiment analysis**: track positive vs negative language in tickets (AI)

## Step-by-Step: Creating a Ticket Pipeline

1. Service > Tickets > Pipelines
2. Create new pipeline
3. Name and add stages (example):
   - New
   - Investigating (Waiting on Us)
   - Waiting on Contact
   - Solution Proposed
   - Resolved
   - Closed
4. Set SLA targets per stage or pipeline-wide:
   - Response time: e.g., 1 hour for Urgent, 4 hours for High
   - Resolution time: e.g., 8 hours for Urgent
5. Configure auto-assignment: round-robin, by ticket type, by priority
6. Save

## Step-by-Step: Setting Up a Knowledge Base

1. Service > Knowledge Base > Create new
2. Name your KB (e.g., "Customer Help Center")
3. Choose template or start blank
4. Create categories: Getting Started, Billing, Troubleshooting, Account Management
5. Write articles in rich text editor
6. Add SEO metadata (title, description, URL)
7. Associate articles with categories
8. Configure domain: subdomain.yourdomain.com or custom domain
9. Add search filters: by category, by product, by topic
10. Publish → add link in your website footer, email signatures, chatbots

## Step-by-Step: Creating a Feedback Survey

1. Service > Feedback > Create survey
2. Choose type: CSAT, NPS, CES
3. Name the survey
4. Configure custom questions (optional):
   - NPS follow-up: "What's the main reason for your score?"
   - CSAT follow-up: "How could we improve?"
5. Set design: color scheme, logo, layout
6. Trigger rules:
   - Send immediately after ticket closure
   - Send after deal closed won
   - Send after lifecycle stage change to Customer
7. Set delay (e.g., send 1 hour after trigger)
8. Configure follow-up actions:
   - If Detractor → create high-priority ticket, notify CS manager
   - If Promoter → add to list, trigger workflow
9. Activate

## Step-by-Step: Creating a Chatbot

1. Conversations > Chatflows > Create a bot
2. Choose bot type: Lead qualification, Ticket creation, Knowledge base, Meeting booking, Custom
3. Build the conversation flow:
   - Greeting message
   - Decision points (e.g., "Are you a new customer?")
   - Branching logic (each answer leads to different path)
   - End actions: create ticket, book meeting, show KB article, handoff to agent
4. Configure targeting:
   - Show on specific pages
   - Show after X seconds on page
   - Show to specific visitor segments
   - Language selection
   - Time/day of week rules
5. Set business hours: auto-reply outside hours, handoff during hours
6. Test the bot (preview mode)
7. Publish → add tracking code to website

## Limits That Matter

- Tickets: Free (1,000 lifetime), Starter (5,000 lifetime), Pro (unlimited), Enterprise (unlimited)
- Pipelines: Free (1), Starter (3), Pro (10), Enterprise (unlimited)
- Knowledge base articles: Free (100), Starter (2,500), Pro (unlimited), Enterprise (unlimited)
- Chatbots: Free (1), Starter (1), Pro (5), Enterprise (unlimited)
- Chatbot users: Free (100), Starter (1,000), Pro (unlimited)
- Feedback surveys: Free (3), Starter (10), Pro (100), Enterprise (unlimited)
- Survey responses: Free (500 lifetime), Starter (10,000 lifetime), Pro (unlimited)
- SLA: Pro (time tracking only), Enterprise (full SLA management with auto-escalation)
- Customer portal: Free/Starter (read-only tickets), Pro/Enterprise (respond to tickets)
- CS users: contact-based pricing (paid seats for CS reps)
- Macro/snippets: Free (5), Starter (20), Pro (unlimited), Enterprise (unlimited)

## Use Cases

- Centralize customer support across email, chat, and social
- Build a self-service knowledge base to reduce ticket volume
- Automate common Q&A with chatbots
- Track customer satisfaction with CSAT and NPS surveys
- Set and monitor SLA compliance for enterprise customers
- Manage renewals and health scores for customer success
- Escalate critical issues automatically
- Train agents with call coaching and quality assurance

## Common Gotchas

- SLA times only count during business hours unless configured for 24/7
- Feedback surveys sent too soon after ticket closure may get lower scores (customer still frustrated)
- Email-to-ticket requires specific forwarding address and SPF/DKIM configured
- Merging two tickets is irreversible — pick the primary record carefully
- Deleting a bot's conversation history is permanent
- Knowledge base articles don't support advanced CSS customization on Free/Starter
- Customer portal shows only tickets with portal visibility enabled (default: all customer tickets)
- Macros are per-user unless shared via properties/teams
- CES questions require more than just "Very Easy" — must match CES scale wording exactly to be valid