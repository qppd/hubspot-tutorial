# 0. HubSpot Platform Overview — Complete Tutorial

## Table of Contents
1. [What is HubSpot?](#what-is-hubspot)
2. [The Flywheel Philosophy](#the-flywheel-philosophy)
3. [Platform Architecture](#platform-architecture)
4. [The CRM Foundation](#the-crm-foundation)
5. [The Six Hubs — Deep Dive](#the-six-hubs--deep-dive)
6. [Breeze AI Platform](#breeze-ai-platform)
7. [Licensing & Pricing Models](#licensing--pricing-models)
8. [Key Concepts](#key-concepts)
9. [Getting Started Step-by-Step](#getting-started-step-by-step)
10. [HubSpot Ecosystem](#hubspot-ecosystem)
11. [Sandbox Environments](#sandbox-environments)
12. [Security & Compliance](#security--compliance)
13. [Common Use Cases by Business Type](#common-use-cases-by-business-type)
14. [Migration from Other CRMs](#migration-from-other-crms)
15. [Tutorial Structure](#tutorial-structure)

---

## What is HubSpot?

HubSpot is a full-stack CRM platform that unifies marketing, sales, service, CMS/content, operations, and commerce into a single, integrated system. Founded in 2006 by Brian Halligan and Dharmesh Shah at MIT, HubSpot pioneered the concept of **inbound marketing** — attracting customers through valuable content rather than interrupting them with ads.

### What Makes HubSpot Different

Unlike the "best-of-breed" approach where companies stitch together Salesforce + Mailchimp + Zendesk + WordPress + Stripe + Tableau, HubSpot provides a **unified database** where every customer interaction across every department lives in one place. This means:

- **Single source of truth**: A contact's email opens, support tickets, deal stage, website visits, and payment history all live on one record
- **No data silos**: Marketing knows when Sales closed a deal. Service knows what marketing emails the customer received. Sales knows what support tickets are open.
- **Built-in automation**: Workflows can span across hubs — e.g., "When a support ticket reaches 'Critical', alert the sales rep and send a discount coupon"
- **AI everywhere**: Breeze AI is baked into every hub, not bolted on

### HubSpot by the Numbers

- **200,000+** customers in over 120 countries
- **$2+ billion** annual revenue
- **5,000+** app integrations in the marketplace
- **260M+** company profiles in Breeze Intelligence database
- **Free CRM** used by millions of small businesses

---

## The Flywheel Philosophy

HubSpot's core philosophy is the **Flywheel** model. Traditionally, sales and marketing used a **funnel**:

```
          ┌─────────────┐
          │  ATTRACT    │
          ├─────────────┤
          │  CONVERT    │
          ├─────────────┤
          │   CLOSE     │
          ├─────────────┤
          │  DELIGHT    │ ← Often ignored
          └─────────────┘
```

The funnel problem: once a customer goes through, they're out of sight. There's no built-in mechanism for existing customers to drive new business.

### The Flywheel

```
         ┌──────────────────────────┐
    ┌────┤      ATTRACT             │◄──── Energy in
    │    │  (Marketing)             │      (content, SEO, ads)
    │    └──────────────────────────┘
    │               │
    │    ┌──────────▼───────────────┐
    │    │      CONVERT              │
    ├────┤      (Sales)             │
    │    └──────────────────────────┘
    │               │
    │    ┌──────────▼───────────────┐
    └────┤      DELIGHT             │────► Energy out
         │      (Service)           │     (referrals, renewals,
         └──────────────────────────┘      upsells, reviews)
```

The flywheel stores **momentum**. Happy customers become your best marketers through referrals, reviews, case studies, and word of mouth. Every interaction either adds energy (good experience) or creates friction (bad experience).

### How Each Hub Contributes to the Flywheel

| Flywheel Stage | Primary Hub | Activities |
|----------------|-------------|------------|
| **Attract** | Marketing Hub | Blog posts, SEO, social media, ads, landing pages, lead magnets |
| **Convert** | Sales Hub | Deals, sequences, meetings, calls, quotes, proposals |
| **Delight** | Service Hub | Tickets, knowledge base, chatbots, feedback surveys, SLAs |
| **Supporting All** | Content Hub | Website, CMS, blog, HubL templates, AI content |
| **Supporting All** | Operations Hub | Data sync, data quality, automation, calculated properties |
| **Supporting All** | Commerce Hub | Payments, invoices, subscriptions, CPQ |

### Practical Example: The Flywheel in Action

1. A customer writes a glowing review → Marketing creates a case study blog → SEO drives organic traffic → Visitors fill out a form → Sales follows up with a sequence → New deal closes → Service provides onboarding → Customer is delighted → Customer refers a friend → Cycle repeats

This is the flywheel. Every department feeds into the next. HubSpot's platform is specifically designed to enable this flow without data leaks between departments.

---

## Platform Architecture

HubSpot's architecture is layered. Understanding these layers helps you understand where features live and how they interact.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     BREEZE AI PLATFORM (Cross-Cutting)                    │
│  Breeze Copilot · Breeze Intelligence · AI Agents · AI Content           │
│  AI Summaries · Predictive Scoring · AI Coaching · AI Call Summaries    │
├─────────────────────────────────────────────────────────────────────────┤
│                            COMMERCE HUB                                   │
│  Payments · Invoicing · Subscriptions · CPQ · Tax · Accounting Connect   │
├─────────────────────────────────────────────────────────────────────────┤
│                          OPERATIONS HUB                                   │
│  Data Sync · Data Quality · Programmable Automation · Datasets/SQL       │
│  Calculated Properties · Rollup Properties                                │
├────────────┬────────────┬────────────┬───────────────────────────────────┤
│ MARKETING  │   SALES    │  SERVICE   │      CONTENT HUB (CMS)             │
│   HUB      │    HUB     │    HUB     │                                    │
│            │            │            │                                    │
│ · Email    │ · Deals    │ · Tickets  │ · Website Builder                  │
│ · Forms    │ · Sequences│ · KB       │ · HubL Templates                   │
│ · Landing  │ · Meetings │ · Chatbots │ · Custom Modules                   │
│ · Blog/SEO │ · Calling  │ · Surveys  │ · Blogging                         │
│ · Social   │ · Quotes   │ · SLA      │ · Content AI                       │
│ · Ads      │ · CI       │ · CSAT/NPS │ · Serverless Functions             │
│ · Workflows│ · Playbooks│ · Automatn │ · HubDB                            │
│ · Scoring  │ · Forecast │ · Success  │ · Multi-language                   │
│ · Campaigns│ · CI       │            │ · Local Dev / CLI                  │
├────────────┴────────────┴────────────┴───────────────────────────────────┤
│                        CRM FOUNDATION                                      │
│  Contacts · Companies · Deals · Tickets · Products · Line Items           │
│  Custom Objects · Properties · Pipelines · Lists · Tasks · Activities     │
│  Associations · Goals · Calls · Meetings · Notes · Email Log              │
│  Activity Timeline · Reporting Dashboards · Workflow Engine               │
├─────────────────────────────────────────────────────────────────────────┤
│                       DEVELOPER PLATFORM                                   │
│  REST API · GraphQL API · Webhooks · SDKs (Python, Node.js, Ruby)         │
│  Private Apps · Public Apps · App Marketplace · CLI · HubL SDK            │
│  Custom Behaviors (Cards, Actions, Bots, Timeline Events)                 │
└─────────────────────────────────────────────────────────────────────────┘
```

### Layer 1: CRM Foundation (Always Included, Even Free)

The CRM is the core database. It's always there whether you have zero paid hubs or all six. It stores:

- **Standard objects**: Contact, Company, Deal, Ticket, Product, Line Item, Quote, Invoice, Payment, Subscription, Goal, Task, Meeting, Call, Email, Communication
- **Custom objects**: Extend the CRM with your own object types
- **Properties**: Fields on objects (standard + custom)
- **Pipelines**: Visual stages for deals, tickets, and custom objects
- **Lists**: Static and dynamic record groupings
- **Activities**: Timeline of all interactions
- **Workflows**: Automation engine (basic workflows included free)
- **Reporting**: Custom reports and dashboards
- **Tasks**: To-do items assigned to users

### Layer 2: The Hubs (Paid Add-ons)

Each hub sits on top of the CRM and adds features. You can buy them individually or together. They share the same database — a contact created in Marketing Hub is the same contact visible in Sales Hub, Service Hub, etc.

### Layer 3: Developer Platform (Always Available)

APIs and SDKs for building on top of HubSpot. Used by:
- Internal developers building custom integrations
- Third-party developers building marketplace apps
- Power users creating custom-coded workflow actions

### Layer 4: Breeze AI (Cross-Cutting, Paid Add-on or Enterprise Included)

Breeze AI is not a separate hub — it's an AI layer that touches every hub. It includes:
- **Breeze Copilot**: Conversational AI assistant throughout the HubSpot UI
- **Breeze Intelligence**: External data enrichment and intent signals
- **AI Agents**: Autonomous task-completing bots
- **Feature-specific AI**: Content generation, lead scoring, call summaries, coaching suggestions, predictive forecasting

---

## The Six Hubs — Deep Dive

### Marketing Hub

**Purpose**: Attract visitors, convert leads, nurture prospects, and measure campaign ROI.

**Key Features**:
- **Email Marketing**: Drag-and-drop email builder, personalization tokens, smart content (dynamic content blocks based on contact properties), A/B testing, send time optimization, transactional emails, subscription management, email analytics with click maps and device breakdowns
- **Forms**: Embedded forms, pop-up forms, slide-in forms, inline forms, floating footer forms. Progressive profiling (show different fields to returning visitors), smart fields (hide already-known fields), GDPR consent fields, reCAPTCHA, file upload fields
- **Landing Pages**: Template-based pages with drag-and-drop editor, smart content personalization, custom domains, SSL, A/B testing, SEO settings (meta, URL slug, canonical URL), password protection
- **Blogging**: Rich text editor with drag-and-drop modules, topic clusters (pillar + cluster strategy), content strategy tool with keyword suggestions, SEO recommendations, readability analysis, multi-language blogging, content calendar
- **Social Media**: Publishing to Facebook, LinkedIn, Twitter/X, Instagram. Social listening (Enterprise), analytics, approval workflows, bulk scheduling
- **Ads**: Ad tracking for Google Ads, Facebook Ads, LinkedIn Ads, Instagram. Retargeting audiences from HubSpot lists. Lead ad sync. UTM tracking
- **Marketing Automation**: Workflows triggered by form submissions, list membership, property changes, page visits, dates. Actions include send email, create task, set property, trigger webhook, branch logic, delays, goals
- **Lead Scoring**: Positive/negative attribute scoring, fit scoring (demographic fit), behavior scoring (engagement level), predictive lead scoring (ML-based)
- **Campaigns**: Group related assets (emails, landing pages, ads, social posts) for combined attribution tracking
- **Analytics**: Traffic analytics, contact analytics, conversion analytics, ROI reporting, custom dashboards, attribution reporting (first-touch, last-touch, linear, U-shaped, W-shaped, time decay)

**Best For**: Inbound marketing teams, content marketers, demand generation, growth marketing

**Tiers**: Free (limited), Starter (~$20/mo), Professional (~$890/mo), Enterprise (~$3,600/mo)
*Pricing varies by marketing contact count and region*

### Sales Hub

**Purpose**: Manage pipelines, automate outreach, track engagement, close deals faster.

**Key Features**:
- **Email Tracking & Templates**: Open/click tracking with notifications, email templates with personalization tokens, snippets (reusable text blocks), AI Snippet Recommendations (Breeze)
- **Sequences**: Automated multi-step follow-up series. Steps include send email, wait/delay, manual task, automatic task. Conditional branching (skip steps if contact replies). Enrollment criteria, unenrollment triggers (reply detected, meeting booked)
- **Meetings**: Calendar sync (Google/Outlook), meeting link with available times, round-robin routing, group meetings, meeting types (phone, video, in-person), buffers, custom reminders
- **Calling**: HubSpot Calling (VoIP), local presence caller ID, call recording, AI transcription, power dialer (Enterprise), call coaching with scorecards
- **Conversation Intelligence (Enterprise)**: Call transcription, AI summaries, AI coaching suggestions, keyword spotting, talk-to-listen ratio, objection tracking, sentiment analysis, coaching scorecards, playlist creation
- **Deal Management**: Kanban board, custom pipelines, stage probability percentages, line items, discounts, deal splits (Enterprise), recurring revenue tracking, auto-assignment rules
- **Lead Management**: Lead scoring, lead rotation (round-robin), lead status tracking, lead feed, prospecting workspace
- **Quotes**: Quote builder from deal line items, PDF templates, discount management, approval workflows, e-signature (HubSpot native, DocuSign, PandaDoc), quote-to-close tracking
- **Playbooks**: Guided sales methodologies (MEDDIC, BANT, SPIN, Challenger). Question templates, AMA (Ask Me Anything) dynamic responses, triggers based on deal stage
- **Forecasting**: Custom forecast periods, team hierarchy rollups (Enterprise), forecast categories (commit, best case, pipeline), Breeze AI Predictive Forecasting, notifications
- **LinkedIn Sales Navigator Integration**: Sync contacts and lists, activity sync (InMail, profile views), save-to-CRM actions
- **Multi-currency Reporting**: Convert and report deal amounts in any base currency with real-time exchange rates

**Best For**: B2B sales teams, inside sales, SDRs, AEs, sales leadership

**Tiers**: Free, Starter (~$15/mo), Professional (~$100/mo/seat), Enterprise (~$150/mo/seat)

### Service Hub

**Purpose**: Support customers, resolve issues, measure satisfaction, drive retention.

**Key Features**:
- **Ticketing**: Multi-pipeline ticket management, status tracking (New, Waiting on Contact, Waiting on Us, Closed), priority levels, ticket types (Question, Problem, Feature Request, Refund), custom properties, SLA tracking (Enterprise), ticket automation
- **Knowledge Base**: Article creation with rich text editor, categorization, SEO settings, search, feedback collection (helpful/not helpful), multi-language KB
- **Chatbots & Conversational Bots**: Flow-based chatbot builder, LLM-powered AI agents (Breeze), routing rules, human handoff, trigger conditions (page URL, time on page, visitor properties)
- **Feedback Surveys**: CSAT (Customer Satisfaction Score), NPS (Net Promoter Score), CES (Customer Effort Score). Customizable question templates, timing rules, anonymous responses
- **Customer Success**: Health scoring (Enterprise), renewal risk detection, upsell/cross-sell recommendations, customer journey analytics
- **Help Desk Features**: Shared inbox (Team Email), automation rules, canned snippets, ticket status pipelines, customer portal
- **Service Automation**: Workflows triggered on ticket properties, SLA violations, customer feedback. Actions include create ticket, send email, assign owner, trigger webhook
- **Calling**: Log calls, voicemail, call tracking integrated with ticketing
- **Reporting**: Ticket volume, response time, resolution time, CSAT/NPS trends, agent performance, SLA compliance, customer health dashboards

**Best For**: Customer support teams, help desk, customer success managers, service operations

**Tiers**: Free, Starter (~$20/mo), Professional (~$360/mo/seat), Enterprise (~$1,200/mo/seat)

### Content Hub (formerly CMS Hub)

**Purpose**: Build and manage websites, blogs, and content with AI-powered tools.

**Key Features**:
- **Website Builder**: Drag-and-drop page editor, theme marketplace, custom themes, global content (headers, footers, global modules), membership/gated content, SEO settings, multi-language sites, custom domains, SSL
- **HubL Templating**: HubSpot's own templating language (similar to Jinja2/Liquid). Variables, filters, for loops, if/else, macros, functions. Full reference: `{{ }}`, `{% %}`, `{# #}`
- **Custom Modules**: Create reusable content modules with fields (text, image, color, link, boolean, etc.), module styles, module-level JavaScript
- **Blogging**: Content calendar, multi-language blogging, RSS feeds, author pages, topic clustering, SEO recommendations, AI content generation
- **Content AI**: AI blog post generation, AI image generation, AI translation, brand voice settings, tone adjustment, content repurposing
- **Local Development**: HubSpot CLI (`@hubspot/cli`), `hs init`, `hs watch`, `hs upload`, `hs fetch`, `hs create`. VS Code integration. Git integration (Enterprise)
- **Serverless Functions**: Node.js functions that run on HubSpot's edge network. Environment variables, secrets, logging, API access
- **HubDB**: Dynamic database tables for structured content. Query via HubL functions (`hubdb_table_rows()`), REST API, or dynamic pages backed by HubDB rows
- **Membership/Gating**: Password-protected pages, registration-required content, membership tiers
- **Adaptive Testing**: A/B and multivariate page testing
- **CDN**: Global content delivery network for fast page loads

**Best For**: Web developers, content teams, agencies building client sites, marketers needing a CMS

**Tiers**: Free (limited), Starter (~$25/mo), Professional (~$330/mo), Enterprise (~$900/mo)

### Operations Hub

**Purpose**: Sync, clean, and automate data across your tech stack.

**Key Features**:
- **Data Sync**: Bi-directional sync between HubSpot and connected apps (Salesforce, Marketo, Mailchimp, Shopify, etc.). Field mapping with transformations, sync history, conflict resolution, sync scheduling
- **Data Quality**: Deduplication rules (merge duplicate contacts, companies), data property standardization (format phone numbers, capitalize names), data quality automation (schedule cleaning tasks)
- **Programmable Automation**: Custom-coded workflow actions in Node.js or Python. Deployed and managed within HubSpot. Triggered by CRM events. Access to HubSpot API client within code
- **Datasets**: SQL-based query engine for HubSpot data. Write SQL to join and aggregate across objects (contacts, companies, deals, custom objects). Scheduled exports. Used in custom report builder
- **Calculated Properties**: Formula-based properties (e.g., `IF (dealstage = "closedwon", dealamount * 0.1, 0)`). Rollup properties (aggregate values from associated records: sum deal amounts on a contact, count tickets on a company)
- **Data Pipeline**: Move data between HubSpot and external data warehouses (Snowflake, BigQuery, etc.) — Enterprise only

**Best For**: Revenue operations (RevOps), data teams, operations managers, IT admins

**Tiers**: Free (limited), Starter (~$30/mo), Professional (~$600/mo), Enterprise (~$2,000/mo)

### Commerce Hub

**Purpose**: Accept payments, manage invoices, handle subscriptions, and configure price quotes.

**Key Features**:
- **Payments**: Native payment processing (powered by Stripe). Payment links (shareable checkout pages), embedded payment on quotes and invoices, buy now pay later options (Affirm, Afterpay), digital wallets (Apple Pay, Google Pay), dispute management
- **Invoicing**: Create and send invoices, recurring invoices, invoice templates, payment tracking, partial payments, credit notes, invoice automation
- **Subscriptions**: Subscription management, billing cycles (monthly, yearly, custom), plan management, proration, dunning management (failed payment retry), subscription analytics
- **CPQ (Configure, Price, Quote)**: Product bundles, pricing rules (volume discounts, tiered pricing), multi-option product configuration, guided selling, approval flows for complex quotes
- **Accounting Integrations**: QuickBooks Online, Xero, NetSuite. Sync invoices, payments, customers
- **Tax Management**: Automatic tax calculation (Avalara integration), tax codes, tax exemptions, jurisdiction-based rates
- **Billing Portal**: Customer self-service portal for managing payment methods, viewing invoices, updating billing info
- **Payment Reporting**: Revenue dashboard, payment reconciliation, transaction history, refund management

**Best For**: B2B companies that need to invoice, SaaS companies with subscriptions, e-commerce businesses, any business accepting payments

**Tiers**: Available as add-on to paid hubs. Transaction-based pricing (percentage + fixed fee). Enterprise CPQ available separately.

---

## Breeze AI Platform

Launched in 2024 and continuously expanded through 2025-2026, **Breeze AI** is HubSpot's artificial intelligence layer that powers features across every hub.

### Breeze Copilot

Breeze Copilot is a conversational AI assistant embedded throughout the HubSpot interface.

**Where You Find It**:
- The Breeze icon (sparkle) in the top navigation bar
- Typing `/` in any text field triggers Copilot suggestions
- On record pages, the Copilot icon opens contextual assistance
- In workflow builder, Copilot can generate workflow logic
- In email editor, Copilot can draft content

**What Breeze Copilot Can Do**:
- Answer questions about your CRM data ("How many deals closed last quarter?")
- Execute actions: "Create a workflow that sends a welcome email when a contact submits the demo form"
- Generate content: "Write a follow-up email to a lead who attended our webinar"
- Report creation: "Build a dashboard showing open deals by rep"
- Property suggestions: "Auto-fill company industry based on website domain"
- Record summaries: "Summarize this contact's history"
- Workflow troubleshooting: "Why did 20 contacts fail to enroll in this workflow?"
- Cross-object queries: "Show me companies with more than 10 open tickets and no recent deal"

**Context Awareness**: Copilot knows what screen you're on. If you're looking at a contact record, it answers about that contact. If you're in the workflow builder, it helps build workflows.

### Breeze Intelligence

Breeze Intelligence is a data enrichment and buying intent platform built into HubSpot.

**Company Enrichment**:
- 260M+ company profiles with firmographics (industry, revenue, employee count, location)
- Technographics (what software/tech stack they use)
- Recent funding, acquisitions, leadership changes
- Job postings and hiring signals
- News mentions and PR activity

**Contact Enrichment**:
- B2B contact data: job titles, departments, seniority levels
- Phone numbers and direct dials
- LinkedIn profile URLs
- Professional email addresses

**Intent Signals**:
- Track companies researching your product category
- Based on web browsing behavior (content consumption, comparison searches)
- Prioritized in your CRM as "buying intent" scores
- Real-time notifications when high-value accounts show intent

**Data Appending**:
- Auto-enrich new contacts as they enter your CRM
- Batch enrichment of existing records
- Scheduled enrichment runs

**Pricing**: Available as a paid add-on. Usage-based pricing (enrichment credits). Included in some Enterprise tiers.

### AI Agents (2025+)

HubSpot's AI Agents are autonomous bots that can complete tasks end-to-end:

**Types of AI Agents**:
- **Sales Agent**: Prospecting, lead qualification, meeting booking, follow-up sequences
- **Service Agent**: Autonomous ticket resolution, knowledge base answers, refund processing, status updates
- **Marketing Agent**: Campaign creation, content generation, audience segmentation, A/B testing
- **Content Agent**: Blog writing, image creation, social posts, SEO optimization

**How AI Agents Work**:
1. Define the agent's goal and scope
2. Connect it to your CRM data
3. Set guardrails (approval requirements, budget limits)
4. Agent executes autonomously but escalates when needed
5. Review agent activity log for audit trail

### Feature-Specific AI Capabilities

| Feature | Hub | What It Does |
|---------|-----|-------------|
| AI Content Generation | Marketing, Content | Generate blog posts, emails, landing pages, social posts from prompts |
| AI Image Generation | Content, Marketing | Create custom images using built-in AI image generator |
| AI Translation | Content, Marketing | Translate content into 20+ languages with one click |
| AI Subject Lines | Marketing | Auto-generate subject line variations for A/B testing |
| AI Lead Scoring | Marketing (Pro+) | ML-based predictive lead scoring |
| AI Email Campaigns | Marketing | Generate full email campaigns from a brief |
| AI Call Summaries | Sales (Enterprise) | Auto-generated call summaries with key points and action items |
| AI Coaching | Sales (Enterprise) | Identify improvement areas from call recordings |
| AI Forecasting | Sales (Enterprise) | ML-based deal velocity and close predictions |
| AI Snippet Recommendations | Sales, Service | Suggest relevant snippets based on conversation context |
| AI Summaries | Sales, Service | Auto-generated record summaries |
| AI Chatbot/AI Agent | Service, Marketing | LLM-powered conversational bots |
| Predictive Analytics | Sales, Service (Enterprise) | Churn prediction, deal probability |
| Smart CRM | Platform (Pro+) | Auto-suggest properties, auto-enrich records |
| Brand Voice | Marketing, Content | Define and enforce brand voice across AI-generated content |

---

## Licensing & Pricing Models

HubSpot uses four different pricing models across its products. Understanding how you're billed is critical to budgeting.

### Model 1: Per-Seat (User-Based)

**Applies to**: Sales Hub, Service Hub, Content Hub

You pay for each user who needs access to the hub. Additional seats cost a monthly fee.

- Sales Hub Pro: ~$100/mo per seat
- Sales Hub Enterprise: ~$150/mo per seat
- Service Hub Pro: ~$360/mo per seat (includes 5 seats)
- Service Hub Enterprise: ~$1,200/mo per seat (includes 10 seats)
- Content Hub Pro: ~$330/mo per seat (includes 5 seats)
- Content Hub Enterprise: ~$900/mo per seat (includes 10 seats)

**Key Detail**: Some hubs include a base number of seats in the subscription fee (e.g., Service Hub Pro includes 5 seats). Additional seats are priced per user.

### Model 2: Contact-Based

**Applies to**: Marketing Hub

You pay based on the number of **marketing contacts** — contacts you send marketing emails to. Non-marketing contacts (support contacts, past customers you don't market to) don't count toward your bill.

- Starter: ~$20/mo for 1,000 marketing contacts
- Pro: ~$890/mo for 2,000 base marketing contacts + $250/mo per additional 1,000
- Enterprise: ~$3,600/mo for 10,000 base marketing contacts + $225/mo per additional 1,000

**Cost-Saving Strategy**: Set contacts who don't need marketing emails as "non-marketing" to reduce your count. You can have unlimited non-marketing contacts.

### Model 3: Feature-Based

**Applies to**: Operations Hub

You pay for access to features, with each tier unlocking more capabilities.

- Starter: ~$30/mo — Basic data sync, data quality tools
- Pro: ~$600/mo — Programmable automation, datasets/SQL, calculated properties
- Enterprise: ~$2,000/mo — Data pipeline, advanced sync, all features

### Model 4: Transaction-Based (Add-On)

**Applies to**: Commerce Hub, Breeze Intelligence

- Commerce Hub: Per-transaction fees (2.9% + $0.30 for card payments, varies by region). Monthly subscription fee for CPQ.
- Breeze Intelligence: Usage-based credit system. Each enrichment (company or contact) costs credits. Batch pricing available.

### Free Tier

HubSpot's free CRM includes a surprising amount of capability:
- Unlimited contacts, companies, deals, tasks
- 1,000,000 contacts (storage limit, not marketing contacts)
- Up to 2,000 email sends per month
- Live chat
- Meeting scheduling
- Form builder (limited)
- Pipeline management (1 pipeline, up to 10 stages)
- Email tracking
- Basic reporting dashboards
- Mobile apps
- 10 custom objects (10,000 records each)

### Add-Ons to Know

| Add-On | Price | What It Does |
|--------|-------|-------------|
| Breeze Intelligence | Usage-based | Data enrichment, intent signals |
| Commerce Hub Payments | Transaction % | Native payment processing |
| CPQ (Commerce Hub) | ~$1,500/mo | Configure-price-quote, bundles |
| Video Hosting | Included with most paid tiers | Host and track videos |
| Dedicated IP | Varies | For high-volume email senders |
| API Overages | $0.05/1,000 extra calls | Additional API requests beyond tier limits |
| Sandbox | Enterprise included | Isolated testing environments |

---

## Key Concepts

### Objects

Objects are the core data types in HubSpot's CRM. Each object has:
- **Properties** (fields that store data)
- **Records** (individual instances, like one contact)
- **Associations** (links to other objects)
- **Activity Timeline** (history of interactions)

**Standard Objects**:

| Object | Description | Typical Use |
|--------|-------------|-------------|
| Contact | Individual person | Customers, leads, prospects |
| Company | Business/account | B2B accounts, organizations |
| Deal | Sales opportunity | Active sales pipeline items |
| Ticket | Support request | Customer issues, help desk |
| Product | Sellable item | Line items on deals and quotes |
| Line Item | Product on a deal | Quantity, price, discount per product |
| Quote | Sales proposal | Formal offer to customer |
| Invoice | Bill for payment | Request for payment |
| Payment | Received payment | Transaction record |
| Subscription | Recurring billing | SaaS, memberships |
| Goal | Target/metric | Sales quotas, activity targets |
| Task | To-do item | Follow-ups, call tasks, reminders |
| Meeting | Calendar event | Sales meetings, demos |
| Call | Phone call record | Call logs |
| Email | Email engagement | Logged emails, tracked opens/clicks |
| Communication | General interaction | WhatsApp, SMS, other channels |

**Custom Objects**: Create your own objects for your specific domain (e.g., Vehicle, Course, Property, Project, Policy). Up to 10 custom objects on Pro, 200 on Enterprise.

### Properties

Properties are the fields on an object. Every property has:
- **Internal name**: machine-readable, cannot be changed after creation (e.g., `firstname`, `deal_stage`, `my_custom_field`)
- **Label**: human-readable name (e.g., "First Name", "Deal Stage", "My Custom Field")
- **Type**: data type (string, number, date, boolean, etc.)
- **Field type**: how it appears in UI (text input, dropdown, checkbox, etc.)
- **Group**: logical grouping on record pages
- **Required**: whether it must have a value for record creation
- **Read-only**: prevents manual editing

**Property Types**:

| Type | UI Appearance | Examples |
|------|--------------|----------|
| Single-line text | Text input | Name, email, phone |
| Multi-line text | Textarea | Description, notes |
| Number | Numeric input | Amount, quantity, score |
| Date | Date picker | Close date, birthdate |
| Date/Time | DateTime picker | Meeting time, deadline |
| Dropdown | Select menu | Industry, lead source |
| Multiple checkboxes | Checkbox group | Interests, product interest |
| Single checkbox | Single checkbox | GDPR consent, newsletter opt-in |
| Radio select | Radio buttons | Priority, status |
| Boolean | Toggle | Active, verified, opted-in |
| File | File upload | Contract, PDF, image |
| Calculation | Read-only formula | Discounted price, commission |
| Phone | Phone input | With formatting |
| Email | Email input | With validation |
| Domain | URL input | Website, domain |
| Rich text | WYSIWYG editor | Article body, description |
| Recurring | Recurring pattern | Subscription interval |

**Property Limits**:
- Custom properties per object: 1,000 (Free/Starter/Pro), 10,000 (Enterprise)
- Dropdown options: 1,000 per property
- File uploads: 1 file per file-upload property
- Property groups: 100 per object
- Calculated properties: Operations Hub Pro required

### Association Labels

Associations link records across objects. With labels, you can specify the nature of the relationship:

- **Unlabeled**: Simple link (Contact → Company: "associated to")
- **Labeled**: Semantic relationship (Contact → Company: "Employee of" / "Has employee")
- **Custom labels**: Create your own (e.g., "Primary Vendor" vs "Secondary Vendor")
- **One-to-one, one-to-many, many-to-many**: Different cardinalities supported

**Association Limits**:
- 10,000 total associations per record
- 1,000 associations per label per record
- 50 unique labels per object pair (Pro/Enterprise: 100)

### Pipelines

Pipelines visualize progress through stages. Available for:
- **Deals**: Sales pipeline (up to 100 pipelines on Enterprise)
- **Tickets**: Support pipeline (up to 10 pipelines)
- **Custom objects**: Pipeline tracking (Enterprise only, up to 50)

**Pipeline Features**:
- Drag-and-drop stage ordering
- Probability percentages per stage (deals only)
- Stage-to-stage transition rules (which stages can go forward/backward)
- Required properties per stage (e.g., "Close date required after Contract Sent")
- Pipeline rotation rules (round-robin assignment)
- Pipeline-specific views and reporting

### Lists

Lists group records for segmentation and targeting:

**Static Lists**: Fixed membership. Records are manually added or removed. Stays the same until you manually change it.

**Active Lists**: Dynamic membership based on criteria (contact properties, list membership, form submissions, page views, email engagement). Records automatically match or leave based on current criteria.

**List Use Cases**:
- Email send targets (Marketing Hub)
- Workflow enrollment (automations)
- Reporting segments
- Ad retargeting audiences
- Deal/company groupings

**List Limits**:
- 1,000 active lists (Pro), unlimited (Enterprise)
- 1,000 static lists (Pro), unlimited (Enterprise)
- 1M records per list

### Workflows

Workflows are the automation engine. They can be:

**Trigger-based**: Enroll records when a trigger event occurs (form submitted, property changed, list membership added, date arrives)

**Goal-based**: Enroll records and wait until a goal is met (e.g., "Contact becomes customer") or criteria expires

**Manual**: Enroll records on-demand from record pages or list actions

**Workflow Components**:
1. **Enrollment triggers**: What causes a record to enter
2. **Branches**: If/then logic based on properties, list membership, or behavior
3. **Actions**: Emails, tasks, property updates, list management, deal creation, webhooks, sequence enrollment
4. **Delays**: Wait for specific duration or until a specific date/day
5. **Goals**: Wait until condition is met
6. **Re-enrollment**: When should records re-enter (if ever)

**Workflow Limits**:
- Free: 5 active workflows
- Starter: 20
- Pro: 500
- Enterprise: 1,000+

### Teams

Teams are groups of HubSpot users for:
- Record sharing (team sees team's records)
- Reporting (filter by team)
- Permissions (team-specific access)
- Assignment (route records to teams)

**Team Limits**:
- Free: 1 team
- Starter: 3 teams
- Pro: 15 teams
- Enterprise: Unlimited teams

### Roles & Permissions

HubSpot provides granular access control:

**User Roles**: Super Admin, specific hub permissions (Marketing, Sales, Service, etc.), custom roles

**Object Permissions**: View-only, edit, delete per object type

**Property-Level Permissions**: Restrict edit access to specific properties (Enterprise)

**Team-Based Permissions**: Records visible only to team members

**Partitioning (Enterprise)**: Complete data isolation by business unit or brand

---

## Getting Started Step-by-Step

### Step 1: Create Your Account

1. Go to **hubspot.com** and click "Get started free" (or sign up for a paid trial)
2. Enter your email, first name, last name, phone, company name, website
3. Choose your industry from the dropdown (Retail, SaaS, Manufacturing, Healthcare, Real Estate, Education, Financial Services, etc.)
4. Select your role (Owner/CXO, Marketing, Sales, Service, Operations, IT/Dev, Other)
5. Tell HubSpot your primary goal: Get more leads, Close more deals, Support customers better, Build a website, Connect my tools, Other
6. Complete onboarding wizard:
   - Import contacts (CSV, Gmail, Outlook, or skip)
   - Connect your email inbox (Gmail/Google Workspace or Outlook/Office 365)
   - Connect your calendar
   - Install tracking code on your website
   - Connect social accounts
7. You land on the **Dashboard** — your personalized home page

### Step 2: Import Your Data

HubSpot offers several import methods:

**CSV Import**:
1. Navigate to **Contacts** > **Import** (or Settings > Import & Export)
2. Choose file type: CSV, XLSX, or TSV
3. Select object type: Contacts, Companies, Deals, Products, etc.
4. Map columns to HubSpot properties (auto-detect or manual)
5. Set identifier matching: update existing records or create new
6. Configure additional options: create deals for contacts, create companies for contacts
7. Review and complete

**Connected Email Import**:
- Automatically syncs contacts you email with
- Imports email signatures as contact data
- Syncs calendar events

**Integration Import**:
- Connect Gmail/Outlook/Office 365 to sync contacts
- Connect Salesforce, Shopify, or other apps
- Connect LinkedIn Sales Navigator

**Manual Entry**:
- Click **Create contact** on any contact page
- Fill in properties
- Save

### Step 3: Set Up Your Pipeline

For most businesses, the first pipeline to set up is the **Deal Pipeline**:

1. Go to **Sales** > **Pipelines**
2. Click "Create pipeline"
3. Name it (e.g., "Standard Sales Process")
4. Add stages that match your actual sales process:

   **Example: SaaS Sales Pipeline**
   | Stage | Probability | Description |
   |-------|-------------|-------------|
   | New Lead | 10% | Initial inquiry received |
   | Qualified | 20% | BANT criteria met |
   | Demo Scheduled | 40% | Product demo booked |
   | Demo Completed | 50% | Demo presented |
   | Proposal Sent | 70% | Quote/proposal delivered |
   | Negotiating | 80% | Terms being discussed |
   | Closed Won | 100% | Deal closed |
   | Closed Lost | 0% | Deal lost |

5. Set stage-to-stage rules (optional):
   - Lock stages: deals must go through each stage (no skipping)
   - Allow backward movement: deals can return to earlier stages
   - Required properties: set fields that must be filled before moving to next stage

6. Add deal rotation rules (optional):
   - Round-robin: assign deals to team members in rotation
   - Rules-based: assign based on territory, deal size, product type

### Step 4: Configure Users & Permissions

1. Go to **Settings** > **Users & Teams** > **Users**
2. Click "Create user"
3. Enter email address
4. Choose role:
   - **Super Admin**: Full access to everything
   - **Specific Hub Role**: Marketing, Sales, Service, etc.
   - **Custom Role**: Define specific permissions
5. Set object permissions:
   - View, Create, Edit, Delete per object type
   - Read-only, Edit, or No Access
6. Assign to teams (optional)
7. Set property-level permissions (Enterprise):
   - Restrict specific fields from specific roles
   - Example: Sales reps can't see "ACV" property but managers can

### Step 5: Connect Integrations

1. Go to **Settings** > **Integrations** > **Connected apps**
2. Browse available integrations or search for specific apps
3. Common integrations to start with:
   - **Gmail/Outlook**: Track emails, sync calendar
   - **Slack**: Get notifications, create records from messages
   - **Zoom/Google Meet/Teams**: Auto-log meetings
   - **Shopify/WooCommerce**: Sync orders and customers
   - **WordPress**: Install tracking code, sync forms
   - **LinkedIn**: Social selling, Sales Navigator
   - **QuickBooks/Xero**: Sync invoices and payments

### Step 6: Install Tracking Code

1. Go to **Settings** > **Tracking & Analytics** > **Tracking Code**
2. Copy the JavaScript snippet
3. Paste it in your website's `<head>` section (just before `</head>`)
4. Verify installation using HubSpot's tracking code checker
5. Tracked data includes:
   - Page views (which pages, how long)
   - Form submissions
   - CTA clicks
   - Scroll depth
   - Time on site
   - Referral source
   - Device/browser info
   - IP address (for geo-location)

### Step 7: Start Automating

**First Workflow**: Welcome Series for New Leads
1. Go to **Automation** > **Workflows**
2. Click "Create workflow"
3. Choose: Contact-based
4. Trigger: When a contact fills out any form
5. Branch: If lifecycle stage is "Lead", continue. Otherwise, exit.
6. Action 1: Send email (create a welcome email)
7. Action 2: Set property "Lead Status" to "New"
8. Action 3: Create task for assigned sales rep: "Follow up with {{ contact.firstname }}"
9. Turn on workflow

**First Sequence**: Follow-up Sequence for New Leads
1. Go to **Sales** > **Sequences**
2. Create sequence
3. Step 1: Send email (Day 0) — "Thanks for your interest"
4. Step 2: Wait 2 days
5. Step 3: Send email (Day 2) — "Here's more info about our product"
6. Step 4: Wait 3 days
7. Step 5: Send email (Day 5) — "Would you like to schedule a demo?"
8. Step 6: Create task for rep — "Call this lead"
9. Set unenrollment: Unenroll if contact replies or meeting booked
10. Activate and enroll contacts

---

## HubSpot Ecosystem

### HubSpot App Marketplace

The App Marketplace at **marketplace.hubspot.com** contains 1,000+ integrations:

**Categories**:
- CRM & Data Management (Salesforce, Zapier, Mailchimp)
- Marketing (Canva, Unbounce, Google Ads)
- Sales (LinkedIn, ZoomInfo, Outreach)
- Service (Jira, Zendesk, Calendly)
- Content & CMS (WordPress, Cloudflare, YouTube)
- Commerce (Shopify, Stripe, QuickBooks)
- Productivity (Slack, Asana, Trello, Google Workspace)
- Analytics (Tableau, Looker, Google Analytics)

**App Types**:
- **Connected Apps**: Link your accounts, data flows between systems
- **Marketplace Apps**: Publicly listed apps built by HubSpot or partners
- **Private Apps**: Internal-only apps built by your team
- **Custom Integrations**: Built with APIs, not listed on marketplace

### HubSpot Solutions Partners

HubSpot has a global network of **Solutions Partners** (agencies) who:
- Implement and configure HubSpot
- Build custom integrations
- Provide training and coaching
- Offer managed services
- Develop marketplace apps

**Partner Tiers**: Diamond, Platinum, Gold, Silver, Solutions (from highest to lowest)

### HubSpot Academy

Free certification courses:

**Certifications Available**:
- HubSpot CRM Certification
- Inbound Marketing Certification
- HubSpot Marketing Software Certification
- HubSpot Sales Software Certification
- HubSpot Service Software Certification
- HubSpot CMS for Developers Certification
- Revenue Operations Certification
- Growth-Driven Design Certification
- Social Media Certification
- Email Marketing Certification
- Content Marketing Certification
- Inbound Sales Certification
- HubSpot Reporting Certification

Each certification includes video lessons, written guides, quizzes, and a final exam. Free to take.

### HubSpot Community

- **HubSpot Community Forums**: Discussion boards for users to ask questions and share tips
- **HubSpot User Groups**: Local meetups (virtual and in-person)
- **HubSpot Blog**: Product updates, marketing tips, sales advice
- **Spotlight**: HubSpot's annual customer conference

---

## Sandbox Environments

Enterprise accounts include sandbox environments for testing.

### Standard Sandbox
- Full copy of your production portal (data, settings, integrations)
- Safely test workflows, automation, custom objects
- Test API integrations before deploying
- Refresh from production periodically

### Developer Sandbox
- Lightweight environment for API and custom code testing
- No production data copy
- Best for: testing custom behaviors, private apps, webhooks
- Faster refresh cycle

### What Sandboxes Can Test:
- Workflow logic and enrollment criteria
- Custom object schemas and associations
- API integrations and webhook handling
- Email templates and content
- Permissions and roles
- Automation rules
- Calculated properties
- Custom-coded actions

### What Sandboxes Cannot Test:
- Email deliverability (separate from production sending reputation)
- Payment processing (Commerce Hub transactions)
- Real ad spend (ad accounts are separate)

---

## Security & Compliance

### Data Security

- **Encryption at rest**: AES-256 for all stored data
- **Encryption in transit**: TLS 1.2+ for all data transfer
- **SOC 2 Type II**: Certified annually
- **ISO 27001**: Certified
- **GDPR**: Full compliance tools (consent tracking, data processing amendment, DPA)
- **CCPA**: California Consumer Privacy Act compliance
- **HIPAA**: Available on Business Enterprise plans (BA required)
- **PCI DSS**: Level 1 certified for payment processing
- **Data center locations**: US, EU (Frankfurt), Australia (Sydney) — choose where your data lives
- **Data retention**: Configurable retention policies per object
- **Audit log**: Track who changed what and when (Enterprise)

### Privacy Features

- **GDPR consent fields**: Add to forms and properties
- **Consent tracking**: Track opt-in/opt-out per communication type
- **Data Processing Agreement (DPA)**: Available on request
- **Sub-processors** list: Published and updated regularly
- **Data Subject Access Request (DSAR) tools**: Built-in
- **Cookie consent**: Built-in cookie banner for websites
- **IP anonymization**: Optional for tracking
- **Double opt-in**: Optional for email subscriptions

### Compliance Certifications

- SOC 2 Type II
- ISO 27001
- PCI DSS Level 1
- HIPAA (Business Enterprise)
- GDPR
- CCPA
- ePrivacy (EU cookie law)
- CAN-SPAM Act compliance
- CASL (Canada) compliance

---

## Common Use Cases by Business Type

### Small Business / Solopreneur (1-10 employees)
- **Needs**: Basic CRM, email tracking, simple pipeline
- **Hubs**: CRM (Free) + Sales Hub Starter
- **Cost**: $15-50/mo
- **Setup time**: 1-2 hours
- **Key features**: Contact management, deal pipeline, email tracking, meeting scheduling, basic forms

### B2B SaaS (10-50 employees)
- **Needs**: Lead generation, sales pipeline, customer support, reporting
- **Hubs**: Marketing Hub Pro + Sales Hub Pro + Service Hub Starter
- **Cost**: $1,000-2,500/mo
- **Setup time**: 2-4 weeks
- **Key features**: Marketing automation, lead scoring, sequences, ticketing, knowledge base, custom reporting

### E-commerce (10-100 employees)
- **Needs**: Customer tracking, email marketing, support, payments
- **Hubs**: Marketing Hub Pro + Sales Hub Pro + Commerce Hub
- **Cost**: $1,500-3,500/mo
- **Setup time**: 2-6 weeks
- **Key features**: Shopify/WooCommerce integration, abandoned cart emails, order sync, payment links, invoicing

### Enterprise / Multi-brand (100-1000+ employees)
- **Needs**: Full stack, custom objects, data sync, SLAs, AI
- **Hubs**: All hubs Enterprise tier
- **Cost**: $5,000-25,000+/mo
- **Setup time**: 2-6 months
- **Key features**: Custom objects, programmable automation, Conversation Intelligence, data sync, partitions, AI agents, sandboxes

### Agency / Services (10-50 employees)
- **Needs**: Client management, project tracking, billing
- **Hubs**: Sales Hub Pro + Service Hub + Commerce Hub
- **Cost**: $500-2,000/mo
- **Setup time**: 1-3 weeks
- **Key features**: Custom objects (Projects), deal pipeline, invoicing, time tracking, quotes

### Nonprofit / Education
- **Needs**: Donor management, event tracking, communication
- **Hubs**: CRM (Free) + Marketing Hub (discount available)
- **Cost**: Free to $500/mo (HubSpot offers 40-90% discounts for nonprofits)
- **Setup time**: 1-3 weeks
- **Key features**: Contact management, email, forms, landing pages, donor tracking

---

## Migration from Other CRMs

### From Salesforce

**Challenges**:
- Salesforce's data model is deep (many custom objects, complex relationships)
- Salesforce's permission model is granular (profile-based)
- Report migration requires rebuilding

**Migration Process**:
1. **Audit**: Map all objects, fields, workflows, and reports
2. **Clean**: Deduplicate and normalize data before export
3. **Export**: Use Salesforce's Data Export Service or a migration tool
4. **Prepare HubSpot**: Create equivalent custom objects and properties
5. **Import**: Use HubSpot's import tool or Operations Hub Data Sync
6. **Rebuild**: Workflows, reports, dashboards, automations
7. **Train**: Users need to learn HubSpot's interface
8. **Go live**: Cut over, deactivate Salesforce

**Tools**: HubSpot provides a Salesforce migration toolkit. Operations Hub Data Sync can run both in parallel during transition.

### From Zoho

- Zoho's data model is simpler (fewer custom objects)
- Main challenge: Zoho's customization approach differs from HubSpot
- Import is straightforward via CSV export/import
- Workflow migration requires rebuilding in HubSpot's workflow engine

### From Pipedrive

- Clean data export (Pipedrive's CSV export is well-structured)
- Pipeline stages map directly to HubSpot deal pipelines
- Activities and notes import well
- Pipedrive's custom fields become HubSpot custom properties
- Pipedrive's email sync carries over if using same inbox

### From HubSpot Free to Paid

- No migration needed — your data stays in place
- You unlock feature gates as you upgrade
- Marketing contacts reclassified: existing contacts may need marketing contact assignment

---

## Tutorial Structure

This tutorial covers each Hub in exhaustive detail. Each chapter is a standalone deep-dive you can read independently.

| # | Chapter | Covers | Approx. Length |
|---|---------|--------|----------------|
| 00 | **HubSpot Platform Overview** | Platform architecture, flywheel, all hubs overview, Breeze AI, concepts, getting started | ~20,000 words |
| 01 | **CRM Foundation** | Contacts, companies, deals, tickets, properties, pipelines, lists, activities, reporting | ~20,000 words |
| 02 | **Marketing Hub** | Email, forms, landing pages, SEO/blog, social, ads, workflows, lead scoring, campaigns, analytics | ~20,000 words |
| 03 | **Sales Hub** | Sequences, meetings, calling, conversation intelligence, deals, quotes, playbooks, forecasting | ~20,000 words |
| 04 | **Service Hub** | Ticketing, KB, chatbots, feedback, CSAT/NPS, SLA, customer success, help desk | ~20,000 words |
| 05 | **Content Hub (CMS)** | Website builder, HubL, custom modules, blog, content AI, local dev, serverless, HubDB | ~20,000 words |
| 06 | **Operations Hub** | Data sync, data quality, programmable automation, datasets/SQL, calculated properties | ~20,000 words |
| 07 | **Commerce Hub** | Payments, invoicing, subscriptions, CPQ, accounting integrations, tax | ~20,000 words |
| 08 | **Custom Objects & API** | Custom objects, REST API, GraphQL, webhooks, apps, SDKs, custom behaviors | ~20,000 words |
| 09 | **Integrations & Automation** | Native integrations, iPaaS, workflow patterns, sequence automation, advanced automation | ~20,000 words |
| 10 | **Pricing, Limits & Best Practices** | Pricing tiers, plan limits, scaling strategies, performance, migration, cost optimization | ~20,000 words |

|

---

## HubSpot Mobile App — Complete Guide

### Available Apps
iOS and Android apps available. Covers all core CRM functionality.

### Mobile Features by Role

**Sales reps on mobile**:
- View and edit contacts, companies, deals
- Log calls, emails, meetings, notes
- View and update deal stages (drag-and-drop on Kanban)
- Access meeting links and calendar
- Email tracking on the go
- Receive push notifications for deal changes, task assignments
- QR code scanning for business card -> contact creation
- Voice-to-text for notes

**Service reps on mobile**:
- View and respond to tickets
- Chat with customers from the Conversations inbox
- View knowledge base articles
- Log calls and update ticket status
- Push notifications for new tickets and SLA breaches

**Marketers on mobile**:
- View email performance
- Approve social posts
- View dashboards and reports
- Monitor campaign performance

**Managers on mobile**:
- View pipeline dashboards
- Team performance metrics
- Deal and activity reports
- Forecasting snapshots

### Mobile-Specific Features
- **Offline mode**: View and edit contacts, companies, deals without internet. Syncs when connection returns.
- **Quick actions**: 3D Touch / long-press shortcuts for quick contact creation, call logging, meeting scheduling
- **Widget**: iOS widget shows today's tasks, upcoming meetings, recent deals
- **Push notifications**: Configurable alerts for deal stage changes, task assignments, ticket updates, form submissions
- **Face ID / Touch ID / biometric login**: Security without typing password
- **Share to HubSpot**: From any app, share a contact or email directly to HubSpot
- **Calendar integration**: Native calendar app sync for meeting availability

### Mobile Limitations vs Desktop
- Cannot create workflows or sequences
- Limited reporting (view dashboards but not create/edit reports)
- Cannot manage users, permissions, or settings
- Cannot build landing pages or emails
- File upload limited to photos from camera roll
- Offline mode has limited functionality (contacts, companies, deals only)

### Best Practices for Mobile CRM
1. Enable push notifications for deal stage changes and task assignments
2. Use voice-to-text for notes instead of typing on small screen
3. Set up Quick Actions for tasks you do daily
4. Download offline data before traveling (flights, areas without coverage)
5. Use the Share extension to add contacts from other apps

---

## HubSpot Data Architecture — Deep Dive

### How HubSpot Stores Data
HubSpot uses a multi-tenant PostgreSQL-based architecture with custom indexing for CRM objects. Understanding the data architecture helps in designing scalable integrations and custom objects.

### Object Storage Model
- Each object type (contact, company, deal, ticket, custom object) has its own table/schema
- Properties are stored as JSONB columns for flexibility
- Associations are stored in separate association tables with indexes on both sides
- Activity events are stored in time-series optimized tables
- List membership is stored in a join table with snapshot capability

### Record IDs
- Every record has a unique, auto-incrementing numeric ID
- IDs are NOT reused when records are deleted
- Format: Simple integer (e.g., 123456789)
- Maximum ID length: up to 15 digits
- When creating records via API, you cannot specify the ID
- IDs are portal-specific (same ID in different portals are different records)

### Property Value Storage

**Standard properties**: Stored in dedicated columns (faster querying, indexed)

**Custom properties**: Stored in a JSONB properties column (flexible schema)

**Multi-value properties**: Checkboxes and multi-select dropdowns store values as semicolon-separated strings

**Property history**: Changes are tracked in a separate history table with old_value, new_value, timestamp, and change_source

### Association Storage
- Each association type has a type ID
- Directional: Association from A to B is stored separately from B to A
- Labels: Association labels have their own type IDs
- Indexes: Associations are indexed on both object IDs and type IDs

### Search Index
HubSpot maintains a dedicated search index for the Search API:
- Index is separate from the primary database
- Updated asynchronously (typically within 1-5 minutes of record change)
- Full-text search indexes text properties
- Filter queries use the search index for property conditions
- The search API has a 5-second query timeout

### Data Retention & Deletion

**Soft delete**: When you delete a record in the UI, it goes to the recycle bin:
- Free/Starter: 7 days
- Pro: 30 days
- Enterprise: 30 days (configurable extension available)

**Hard delete**: After recycle bin period, records are permanently deleted:
- Properties: Data loss is permanent
- Associations: Removed from association tables
- Activities: Timeline events are removed
- List membership: Removed

**Data export**: Before hard deletion, you can export data via:
- UI export (CSV, up to 10,000 records)
- API export (batch, up to 100 per call, paginate)
- Operations Hub Data Pipeline (enterprise, to warehouse)
- Dataset scheduled exports (SQL queries to CSV)

### Storage Limits by Object

| Object Type | Free | Starter | Pro | Enterprise |
|------------|------|---------|-----|------------|
| Contacts | 1,000,000 | 1,000,000 | Unlimited | Unlimited |
| Companies | 100,000 | 500,000 | 1,000,000 | Unlimited |
| Deals | Unlimited (perf degrades >5M) | Same | Same | Same |
| Tickets | Unlimited (perf degrades >5M) | Same | Same | Same |
| Custom objects | 10 obj / 10k records | 10 / 100k | 10 / 1M | 200 / Unlimited |
| Activities | 10,000 per contact (rolling) | Same | 50,000 per contact | Unlimited |
| Files | 5GB | 25GB | 100GB | 500GB+ |
| Emails (stored) | Unlimited | Unlimited | Unlimited | Unlimited |

### Performance Optimization by Scale

**At 10,000 records**: No special considerations needed

**At 100,000 records**: 
- Use active lists with specific criteria (avoid blanket conditions)
- Archive records older than 2 years
- Use rollup properties sparingly (every rollup adds query time)

**At 1,000,000 records**:
- Archive heavily
- Use search API with specific filters (avoid unfiltered queries)
- Consider custom objects limits
- Monitor API daily limit usage
- Use batch operations for bulk updates

**At 10,000,000+ records**:
- Enterprise tier required
- Consider data partitioning (by region, business unit, or product line)
- Use Operations Hub Data Pipeline for analytics (don't query CRM directly)
- Implement data archiving strategy (move old records to archive object)
- Reduce custom properties to minimum
- Work with HubSpot solutions engineer on optimization

---

## HubSpot APIs — Use Cases & Best Practices

### Choosing the Right API

| If you need to... | Use... |
|------------------|--------|
| Create/update/delete a single CRM record | Basic API (REST) |
| Create/update/delete 10-100 records | Batch API |
| Find records matching complex criteria | Search API (POST) |
| Fetch a record and all its associations | GraphQL API |
| React to changes in real-time | Webhooks |
| Sync data continuously to another system | Operations Hub Data Sync |
| Query CRM data with SQL | Datasets |
| Build a custom UI card on record pages | Custom-coded card |
| Build a public marketplace app | OAuth + Public App |

### API Authentication Recommendations

| Use Case | Authentication | Why |
|----------|---------------|-----|
| Internal automation script | Private App Token | Simple, scoped, easy to rotate |
| Public marketplace app | OAuth 2.0 Authorization Code | Required for marketplace, handles user consent |
| Server-to-server integration | Private App Token | No user interaction needed |
| Mobile/desktop app | OAuth 2.0 PKCE | Secure for public clients |
| Workflow custom-coded action | Environment variable | Token stored securely at portal level |
| Embed in web app (frontend) | OAuth 2.0 Implicit (deprecated, use PKCE) | Never expose tokens in frontend |

### API Error Code Reference

| Code | Meaning | Common Cause | Fix |
|------|---------|-------------|-----|
| 400 | Bad Request | Invalid property name, wrong data type | Check property internal names, validate data types |
| 401 | Unauthorized | Expired or invalid token | Refresh OAuth token or regenerate private app token |
| 403 | Forbidden | Token lacks required scope | Add scope to private app or request user consent for scope |
| 404 | Not Found | Wrong object ID or endpoint URL | Verify record exists, check endpoint path |
| 409 | Conflict | Duplicate detected, version mismatch | Use upsert with idProperty, check for existing records |
| 429 | Too Many Requests | Rate limit exceeded | Implement exponential backoff, batch requests |
| 500 | Internal Server Error | HubSpot server issue | Retry with backoff, check status.hubspot.com |
| 502 | Bad Gateway | Temporary infrastructure issue | Retry with backoff |
| 503 | Service Unavailable | HubSpot in maintenance | Retry after maintenance window |

### API Pagination Reference

HubSpot APIs use cursor-based pagination (not page numbers):

```javascript
// Get first page
const response = await fetch('/crm/v3/objects/contacts?limit=100');
const data = await response.json();
// data.paging.next.after contains cursor for next page

// Get next page
const nextResponse = await fetch('/crm/v3/objects/contacts?limit=100&after=' + data.paging.next.after);
```

```python
# Python SDK handles pagination automatically
all_contacts = []
after = None
while True:
    page = client.crm.contacts.basic_api.get_page(limit=100, after=after)
    all_contacts.extend(page.results)
    if not page.paging or not page.paging.next:
        break
    after = page.paging.next.after
```

### Batch Operation Limits

| Operation | Max Batch Size | Notes |
|-----------|---------------|-------|
| Batch create | 100 records | Per object type per call |
| Batch read | 100 records | Returns full records with properties |
| Batch update | 100 records | Updates specified properties only |
| Batch upsert | 100 records | Matches on idProperty (email, domain, custom ID) |
| Batch archive | 100 records | Soft delete (goes to recycle bin) |
| Association batch | 100 records | Create/remove associations in bulk |

### Webhook Event Types — Full Reference

| Event Type | Triggered When | Payload Includes |
|------------|---------------|------------------|
| contact.creation | New contact created | objectId, portalId, occurredAt |
| contact.deletion | Contact deleted | objectId, portalId |
| contact.propertyChange | Contact property value changes | objectId, propertyName, propertyValue, changeSource |
| company.creation | New company created | objectId, portalId |
| company.deletion | Company deleted | objectId, portalId |
| company.propertyChange | Company property value changes | objectId, propertyName, propertyValue |
| deal.creation | New deal created | objectId, portalId |
| deal.deletion | Deal deleted | objectId, portalId |
| deal.propertyChange | Deal property value changes | objectId, propertyName, propertyValue |
| deal.stageChange | Deal moves between stages | objectId, propertyValue (stage ID) |
| ticket.creation | New ticket created | objectId, portalId |
| ticket.deletion | Ticket deleted | objectId, portalId |
| ticket.propertyChange | Ticket property value changes | objectId, propertyName, propertyValue |
| product.creation | New product created | objectId, portalId |
| product.propertyChange | Product property changes | objectId, propertyName, propertyValue |
| line_item.creation | New line item created | objectId, portalId |
| line_item.propertyChange | Line item property changes | objectId, propertyName, propertyValue |
| form.submission | Form submitted | objectId (contact), formId, formTitle |
| conversation.creation | New conversation started | objectId, channel (chat/email/social) |

---

## HubSpot Security — Deep Dive

### Authentication Methods Compared

| Method | Security Level | User Experience | Best For |
|--------|---------------|-----------------|----------|
| Password + 2FA | High | Moderate | All users (should be mandatory) |
| SSO/SAML | Highest | Best (no separate password) | Enterprise companies |
| Google Sign-In | High | Best (one-click) | Google Workspace users |
| Microsoft SSO | High | Best (one-click) | Office 365 users |
| API only | N/A | N/A | Integrations (no UI login needed) |

### SSO/SAML Setup

Supported Identity Providers:
- Okta
- Azure Active Directory
- OneLogin
- Google Workspace (SAML)
- Any SAML 2.0 compliant IdP

Setup process:
1. Settings > Security > Single Sign-On
2. Choose IdP
3. Enter SAML metadata URL or upload metadata XML
4. Map attributes (email, first name, last name)
5. Set enforcement: Optional (users can choose) or Required (must use SSO)
6. Test with a test user before enforcing

### Audit Log Features (Enterprise)

The audit log tracks every significant action:

**Tracked events**:
- User logins (success and failure)
- Settings changes
- Permission changes
- User creation/deletion
- Property creation/deletion
- Workflow activation/deactivation
- Integration connections/disconnections
- API token creation/revocation
- Import/export operations
- Record deletion

**Audit log access**:
- Settings > Security > Audit Log
- Filter by: User, action type, date range, object type
- Export to CSV
- 90-day retention (Enterprise; shorter for lower tiers)
- Real-time (within minutes of event)

### IP Restrictions (Enterprise)

Restrict HubSpot access to specific IP ranges:
1. Settings > Security > IP Restrictions
2. Add allowed IP ranges (CIDR notation, e.g., 203.0.113.0/24)
3. Enable enforcement
4. Users outside allowed ranges cannot access HubSpot
5. API tokens from non-allowed IPs are rejected
6. Exceptions: HubSpot mobile app IPs may need to be whitelisted

### Data Residency (Enterprise)

Choose where your data is stored:
- United States (default)
- European Union (Frankfurt, Germany)
- Australia (Sydney)

**Setting data residency**:
1. Purchase Enterprise tier with data residency add-on
2. Select region during portal setup
3. All future data stored in selected region
4. Existing data may need to be migrated (contact HubSpot support)
5. Processing data (transient) may still route through US

### Sub-Processors

HubSpot uses sub-processors for specific services. As of 2026, key sub-processors include:
- Amazon Web Services (infrastructure)
- Google Cloud Platform (infrastructure, AI/ML)
- Stripe (payment processing)
- Avalara (tax calculation)
- OpenAI (Breeze AI content generation - opt-in)
- Snowflake (Data Pipeline - Enterprise)

---

## HubSpot AI — Technical Architecture

### How Breeze AI Works

Breeze AI is built on a multi-model architecture:

**Breeze Copilot**:
- Uses a large language model (LLM) fine-tuned on HubSpot's product documentation and common CRM patterns
- Queries are scoped to the user's portal data with RLS (Row-Level Security)
- Actions are executed via API calls (Copilot generates the API call, not free-form SQL)
- Context-aware: The prompt includes the current page, record, and user's permissions
- Rate limited: 50 queries per user per day (varies by plan)

**Breeze Intelligence**:
- Separate ML models for company enrichment, contact enrichment, and intent signals
- Company data sourced from firmographic databases (D&B, ZoomInfo partnerships)
- Intent signals from co-browsing behavioral data network
- Batch enrichment runs on schedules (typically 24-hour refresh)
- Models are retrained quarterly

**AI Content Generation**:
- Uses OpenAI models for text generation
- Images use DALL-E or Stable Diffusion (depending on plan)
- Brand voice profiles are injected as system prompts
- Content is generated on-the-fly (not cached across users)
- All generated content is reviewable before publishing

**Predictive Lead Scoring**:
- Trained on the specific portal's historical data
- Features: contact properties, behavioral data, deal outcomes
- Model type: Gradient boosted decision tree (XGBoost-like)
- Retraining: Weekly, with minimum 1,000 closed deals for reliable predictions
- Output: Probability score (0-100%) that a contact will convert

### Breeze AI Privacy

- AI training data: HubSpot does NOT train models on customer data without explicit opt-in
- Content generation: Prompts are sent to OpenAI but not stored by OpenAI (zero-retention agreement)
- Enrichment data: Breeze Intelligence sources data from third-party data providers, not from customer CRM data
- Opt-out: Customers can disable Breeze AI features at Settings > Privacy > AI
- GDPR: AI features comply with GDPR when used with standard HubSpot data processing terms

---

## HubSpot for Specific Industries — Deep Dive

### HubSpot for SaaS

**Key features**:
- Subscription management (Commerce Hub)
- Lead scoring for free trial → paid conversion
- Automated onboarding sequences
- Churn prediction (Breeze AI)
- NPS surveys for customer health
- Custom objects for features/environments

**Common setup**:
1. Commerce Hub for payment processing
2. Marketing Hub for trial nurture emails
3. Sales Hub for demo booking
4. Service Hub for support and onboarding
5. Custom object "Feature" associated to deals

**Metrics to track**:
- MRR/ARR (Commerce Hub reporting)
- Trial-to-paid conversion rate (workflow + custom property)
- Churn rate (subscription analytics)
- Customer acquisition cost (CAC) by source (attribution reporting)
- Net revenue retention (custom report with dataset SQL)

### HubSpot for E-commerce

**Key features**:
- Shopify/WooCommerce integration
- Abandoned cart automation (workflow)
- Product sync and line items
- Customer segmentation by purchase history
- Post-purchase email sequences
- Payment links for invoicing

**Common setup**:
1. Connect Shopify/WooCommerce via native integration or Operations Hub
2. Sync orders as deals in HubSpot
3. Create abandoned cart workflow: "Cart abandoned → email 1 hr → email 24 hrs → offer"
4. Segment customers by RFM (Recency, Frequency, Monetary) — use custom properties
5. Create post-purchase nurture: "Thank you → Usage tips → Review request → Cross-sell"

**Metrics to track**:
- Customer lifetime value (calculated property on contact)
- Average order value (rollup from deals)
- Repeat purchase rate (active list: customers with 2+ deals)
- Cart abandonment rate (workflow enrollment rate)
- Revenue by product line (line item reporting)

### HubSpot for Real Estate

**Key features**:
- Custom objects for Properties, Listings, Showings
- Deal pipeline for property transactions
- Contact segmentation by property type interest
- Automated showing follow-ups
- Transaction document management (file uploads)

**Common setup**:
1. Custom object "Property" with fields: address, price, bedrooms, bathrooms, square footage, status (For Sale, Pending, Sold)
2. Custom object "Showing" associated to contacts and properties
3. Deal pipeline: Lead → Tour Scheduled → Offer Made → Under Contract → Closed
4. Smart lists: "Looking for 3BR+ homes under $500k"
5. Workflow: "New property matching saved search → email notification"

**Metrics to track**:
- Days on market per property
- Offer-to-close ratio
- Average commission per deal
- Client referral rate
- Property views vs showings

### HubSpot for Nonprofits

**Key features**:
- Nonprofit discount (40-90%)
- Custom objects for Donations, Grants, Volunteers
- Donor lifecycle tracking
- Campaign ROI for fundraising
- Automated thank-you sequences
- NPS for donor satisfaction

**Common setup**:
1. Marketing Hub for campaign outreach
2. Custom object "Donation" with amount, campaign, recurring flag
3. Rollup property on contact: Total donations, Last donation date, Donation frequency
4. Segmentation: Major donors, Monthly donors, Lapsed donors, First-time donors
5. Workflow: "Donation received → Send thank-you email → Add to donor list → Set next ask date"

**Metrics to track**:
- Donor retention rate
- Average gift size
- Fundraising cost per dollar raised
- Volunteer-to-donor conversion
- Campaign ROI

### HubSpot for Healthcare

**Key features**:
- HIPAA compliance (Business Associate Agreement required)
- Custom objects for Patients, Appointments, Procedures
- Automated appointment reminders
- Patient portal for self-service
- Secure messaging (Compliance requirements)
- Custom-coded actions for PHI data handling

**HIPAA requirements in HubSpot**:
- Business Enterprise tier
- Signed Business Associate Agreement (BAA)
- Data residency in US region
- Audit logging enabled
- IP restrictions enabled
- SSO with 2FA enforced
- Automated session timeout
- Encryption at rest (AES-256) and in transit (TLS 1.2+)

**Common setup**:
1. Custom object "Patient" with associated medical records (stored as file uploads)
2. Custom object "Appointment" with provider, date, time, status
3. Deal pipeline for treatment/procedure sales
4. Workflow: "Appointment created → SMS reminder 48 hrs → Email reminder 24 hrs → Follow-up after appointment"
5. Service Hub for patient inquiries and support

---

## HubSpot Implementation Project Plan

### Phase 1: Foundation (Week 1-2)

**Week 1: Setup & Data Import**
- Day 1: Create HubSpot account, configure basic settings
- Day 2: Connect email inboxes and calendars
- Day 3: Install tracking code on website
- Day 4: Import contacts from CSV/current CRM
- Day 5: Verify data accuracy, clean duplicates

**Week 2: Pipeline & User Setup**
- Day 1: Create deal pipeline matching sales process
- Day 2: Create user accounts with appropriate permissions
- Day 3: Create teams
- Day 4: Create custom properties needed for sales process
- Day 5: Set up lead routing rules

### Phase 2: Marketing (Week 3-4)

**Week 3: Content & Forms**
- Day 1: Create 3-5 standard email templates
- Day 2: Build website forms (Contact, Demo Request, Newsletter)
- Day 3: Create first 2 landing pages
- Day 4: Set up blog and create first 2 posts
- Day 5: Connect social media accounts

**Week 4: Automation & Scoring**
- Day 1: Create welcome workflow for new contacts
- Day 2: Create lead scoring model (basic fit + behavior)
- Day 3: Create first nurture sequence (3-5 step)
- Day 4: Set up lead assignment workflow (new MQL → assign to SDR)
- Day 5: Create first campaign to track marketing ROI

### Phase 3: Sales Enablement (Week 5-6)

**Week 5: Sales Tools**
- Day 1: Create email templates and snippets
- Day 2: Set up meeting links for all sales reps
- Day 3: Create first sequence (cold outreach)
- Day 4: Set up calling (HubSpot Calling or integration)
- Day 5: Create playbooks for discovery and demo calls

**Week 6: Quotes & Forecasting**
- Day 1: Set up product library
- Day 2: Create quote templates
- Day 3: Configure approval workflows for quotes
- Day 4: Set up forecasting
- Day 5: Create sales dashboards

### Phase 4: Service (Week 7-8)

**Week 7: Support Setup**
- Day 1: Set up team email (support@company.com)
- Day 2: Create ticket pipeline
- Day 3: Set up email-to-ticket automation
- Day 4: Create knowledge base articles (10-15 most common issues)
- Day 5: Set up chatbot with FAQ flow

**Week 8: Feedback & Success**
- Day 1: Create CSAT survey (post-ticket closure)
- Day 2: Create NPS survey (quarterly)
- Day 3: Set up SLA targets (Enterprise)
- Day 4: Create customer health scoring (Enterprise)
- Day 5: Create service dashboards

### Phase 5: Optimization & Scale (Week 9-12)

**Weeks 9-10: Advanced Automation**
- Create cross-hub workflows (Marketing → Sales → Service)
- Build custom-coded actions for unique processes
- Set up Operations Hub data sync with key integrations
- Create SQL datasets for advanced reporting

**Weeks 11-12: Training & Go-Live**
- Train team on HubSpot (certifications via HubSpot Academy)
- Create internal documentation for processes
- Run A/B tests on top-performing emails and landing pages
- Review and optimize workflows based on first month data
- Plan ongoing optimization schedule

---

## HubSpot Glossary — Complete Reference

| Term | Definition |
|------|-----------|
| **Active list** | A list that automatically updates based on membership criteria |
| **Association** | A link between two CRM records (e.g., contact to company) |
| **Association label** | A semantic label for an association (e.g., "Primary contact") |
| **Attribution** | Assigning credit for revenue to marketing touchpoints |
| **Breeze AI** | HubSpot's artificial intelligence platform (Copilot, Intelligence, Agents) |
| **Breeze Copilot** | Conversational AI assistant across the HubSpot UI |
| **Breeze Intelligence** | Data enrichment and intent signal platform |
| **Calculated property** | A property whose value is computed from other properties |
| **Campaign** | A group of marketing assets for tracking combined performance |
| **Chatflow** | A chatbot flow for website conversations |
| **Contact** | An individual person record in the CRM |
| **Conversation Intelligence** | AI-powered sales call analysis (Enterprise) |
| **CPQ** | Configure, Price, Quote — product bundling and pricing rules |
| **Custom behavior** | A UI card, workflow action, or bot built with custom code |
| **Custom module** | A reusable content block for Content Hub pages |
| **Custom object** | A user-defined object type extending the standard CRM |
| **Dataset** | A SQL query against CRM data for reporting |
| **Deal** | A sales opportunity tracked through pipeline stages |
| **Dunning** | Automated retry logic for failed subscription payments |
| **Flywheel** | HubSpot's growth model: Attract → Convert → Delight → Refer |
| **Goal-based workflow** | A workflow that runs until a specific condition is met |
| **HubDB** | A database for structured content within Content Hub |
| **HubL** | HubSpot's templating language for CMS development |
| **iPaaS** | Integration Platform as a Service (Zapier, Make, Workato) |
| **Lifecycle stage** | A contact's position in the customer journey |
| **Line item** | A product/service on a deal with quantity and price |
| **Marketing contact** | A contact you send marketing emails to (billed) |
| **Pipeline** | Visual stages for tracking deal/ticket/custom object progress |
| **Playbook** | A guided sales methodology script for reps |
| **Private app** | An internal integration authenticated with a scoped API token |
| **Progressive profiling** | Showing different form fields on repeat visits |
| **Property** | A field on a CRM object |
| **Rollup property** | A property that aggregates values from associated records |
| **Round-robin** | Even distribution of leads/meetings among team members |
| **Sequence** | An automated multi-step follow-up email series |
| **Smart content** | Dynamic content that changes based on viewer properties |
| **Static list** | A list with fixed, manually managed membership |
| **Ticket** | A customer support request or issue |
| **Workflow** | An automated series of triggers, conditions, and actions |
| **Workspace** | A focused view for specific workflows (Prospecting, etc.) |

---

*This is Chapter 0 of the HubSpot Complete Tutorial series. Continue to Chapter 1: CRM Foundation for the deep dive into HubSpot's core data platform.*

---

## Choosing the Right HubSpot Plan — Decision Framework

### Starter Plan Is For You If...
- You have 1-5 employees using the system
- You need shared inbox (Conversations) and basic CRM
- Basic email marketing and meeting scheduling
- Simple contact management
- You don't need custom reporting, workflows, or automation
- Monthly budget under €100

### Professional Plan Is For You If...
- You have 5-50 employees on the platform
- You need automation: workflows, sequences, lead scoring
- Custom reporting and dashboards
- A/B testing for email and landing pages
- Custom objects and properties
- Team-based access control
- HubDB, custom modules, serverless functions (Content Hub)
- Monthly budget under €1,000

### Enterprise Plan Is For You If...
- You have 50+ employees across multiple teams/departments
- You need data partitioning (multi-brand, multi-region)
- Single sign-on (SSO) and advanced security
- Multiple sandbox environments
- Custom roles with property-level permissions
- Predictive lead scoring
- Custom event triggers and advanced workflow capabilities
- Hierarchical teams and rollup reporting
- Audit logs and data loss prevention
- Monthly budget over €1,000

### Plan Upgrade Path — What to Expect
| Upgrade | Additional Cost/Month | Key Benefits |
|---------|---------------------|--------------|
| Free → Starter | ~€50-100 | Conversations inbox, meeting scheduling, basic email |
| Starter → Pro | ~€450-800 | Workflows, automation, custom reporting, lead scoring |
| Pro → Enterprise | ~€1,000-3,000+ | SSO, partitions, custom roles, sandboxes, audit logs |

*Note: Actual pricing varies. Marketing Hub contacts, Sales Hub seats, and Service Hub seats are separate line items that add cost beyond the base plan.*

---

## Implementation Roadmap — 90-Day Plan

### Week 1-2: Foundation
- [ ] Purchase and configure HubSpot subscription
- [ ] Set up user accounts and roles (Admin, Marketing, Sales, Service)
- [ ] Connect email (Gmail/Outlook integration)
- [ ] Install HubSpot tracking code on website
- [ ] Import initial contact list (CSV)
- [ ] Set up company and deals CRM structure

### Week 3-4: CRM Setup
- [ ] Create custom properties for your business (industry-specific fields)
- [ ] Set up deal pipeline stages matching your sales process
- [ ] Configure lead scoring model (basic)
- [ ] Create active lists for key segments
- [ ] Set up team structure and permissions
- [ ] Create first dashboards

### Week 5-6: Marketing
- [ ] Build first email template with brand styling
- [ ] Create forms and landing pages for lead capture
- [ ] Set up first marketing workflow (lead nurture)
- [ ] Configure blog and SEO settings
- [ ] Create first campaign
- [ ] Connect social media accounts

### Week 7-8: Sales
- [ ] Set up sequences for sales outreach
- [ ] Configure meeting scheduling (meetings link)
- [ ] Set up call logging (HubSpot Calling or integration)
- [ ] Create deal stages with required properties
- [ ] Configure pipeline rotation settings
- [ ] Train sales team on CRM usage

### Week 9-10: Service
- [ ] Set up Conversations inbox
- [ ] Create ticket pipeline and SLAs
- [ ] Configure knowledge base
- [ ] Build chatbot (basic flows)
- [ ] Set up email-to-ticket forwarding
- [ ] Configure customer feedback surveys

### Week 11-12: Optimization
- [ ] Review analytics and adjust workflows
- [ ] A/B test email subject lines and landing pages
- [ ] Refine lead scoring based on historical data
- [ ] Build executive dashboards
- [ ] Document processes and best practices
- [ ] Schedule regular data quality audits

---

## HubSpot Glossary — Key Terms

| Term | Definition |
|------|-----------|
| **Contact** | An individual person in your CRM (customer, lead, prospect) |
| **Company** | An organization record, can have multiple contacts |
| **Deal** | A sales opportunity with stages, amount, close date |
| **Ticket** | A support request or customer issue |
| **Custom Object** | A user-defined object (e.g., Project, Course, Property) |
| **Property** | A data field on any object (e.g., "Phone Number", "Annual Revenue") |
| **Pipeline** | A sequence of stages for tracking deal progress |
| **List** | A group of contacts (static = manual, active = dynamic) |
| **Workflow** | Automated sequences of actions triggered by events |
| **Sequence** | A series of sales emails/tasks (Sales Hub) |
| **Smart Content** | Content that changes based on contact properties (e.g., industry) |
| **Progressive Profiling** | Shows new form fields on repeat visits |
| **Lifecycle Stage** | A contact's stage (Subscriber → Lead → MQL → SQL → Opportunity → Customer → Evangelist) |
| **Lead Score** | Numeric score based on fit + behavior |
| **UTM Parameters** | URL tags to track campaign performance |
| **CTA** | Call-to-action (button, link, or image prompting action) |
| **HubDB** | A database system for structured content (Content Hub) |
| **HubL** | HubSpot's templating language (like Liquid or Jinja2) |
| **OAuth 2.0** | Authentication protocol for HubSpot API integrations |
| **Webhook** | HTTP callback that triggers an action when an event occurs |
| **Sandbox** | An isolated testing environment (Enterprise) |
| **Partitioning** | Data isolation between business units (Enterprise) |
| **Rollup Property** | Aggregated value from associated records (Operations Hub) |
| **Calculated Property** | Formula-based property (Operations Hub) |