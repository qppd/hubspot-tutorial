# 0. HubSpot Platform Overview

## What is HubSpot?
HubSpot is a CRM platform that connects marketing, sales, service, CMS, operations, and commerce into one unified system. Unlike standalone tools (e.g., Salesforce + Mailchimp + Zendesk + WordPress), HubSpot gives you a single database where customer data flows across every department.

**Core philosophy:** The "flywheel" model — instead of a linear funnel (attract → convert → close), HubSpot believes happy customers drive growth through referrals and retention.

## Platform Architecture

```
┌─────────────────────────────────────────────────────┐
│              BREEZE AI PLATFORM                      │
│  Breeze Copilot · Breeze Intelligence · AI Agents   │
│  AI Content · AI Lead Scoring · Predictive Analytics│
├─────────────────────────────────────────────────────┤
│                  COMMERCE HUB                        │
│  Payments, Invoicing, Subscriptions, CPQ            │
├─────────────────────────────────────────────────────┤
│              OPERATIONS HUB                          │
│  Data Sync, Data Quality, Programmable Automation   │
├──────────┬──────────┬──────────┬────────────────────┤
│ MARKETING│  SALES   │ SERVICE  │  CMS / CONTENT HUB │
│  HUB     │   HUB    │   HUB    │                    │
│          │          │          │                    │
│ · Email  │ · Deals  │ · Tickets│ · Website Builder  │
│ · Forms  │ · Seq.   │ · KB     │ · Blogging         │
│ · Landing│ · Quotes │ · Chat   │ · HubL Templating  │
│ · Social │ · Calling│ · Survey │ · Custom Modules   │
│ · SEO    │ · Playbk │ · CSAT   │ · Serverless Funcs │
│ · Ads    │ · CI     │ · NPS    │ · Multi-language   │
├──────────┴──────────┴──────────┴────────────────────┤
│                   CRM FOUNDATION                     │
│   Contacts · Companies · Deals · Tickets · Products  │
│   Custom Objects · Properties · Pipelines · Lists    │
│   Activity Timeline · Reporting · Workflows          │
├─────────────────────────────────────────────────────┤
│              DEVELOPER PLATFORM                      │
│   REST API · GraphQL · Webhooks · SDKs              │
│   Private Apps · Public Apps · Marketplace          │
│   CLI · Local Dev · HubL · Custom Behaviors         │
└─────────────────────────────────────────────────────┘
```

## HubSpot Hubs — Quick Comparison

| Hub | Core Feature | Best For | Price Starts |
|-----|-------------|----------|--------------|
| **CRM** | Contact/company/deal/ticket management | Every business | Free (forever) |
| **Marketing Hub** | Email, forms, landing pages, SEO, ads, automation | Inbound marketing teams | Free tier, paid from ~$20/mo |
| **Sales Hub** | Pipelines, sequences, meetings, quotes, forecasting | B2B sales teams | Free tier, paid from ~$15/mo |
| **Service Hub** | Ticketing, KB, chatbots, feedback, CSAT | Customer support/success | Free tier, paid from ~$20/mo |
| **Content Hub** (CMS) | Website builder, blog, HubL, custom modules, AI content | Web dev, content teams | Free tier, paid from ~$25/mo |
| **Operations Hub** | Data sync, data quality, programmable automation | Ops/revenue operations | Free tier, paid from ~$30/mo |
| **Commerce Hub** | Payments, invoicing, subscriptions, CPQ | SaaS, e-commerce, B2B sales | Add-on pricing |

## Hubs Work Together
You don't need all Hubs. Common combos:

| Use Case | Hubs Needed |
|----------|-------------|
| Basic CRM (track contacts, deals) | CRM (Free) |
| B2B inbound + sales pipeline | CRM + Marketing + Sales |
| SaaS with subscriptions | CRM + Sales + Commerce |
| E-commerce + support | CRM + Marketing + Commerce + Service |
| Multi-channel enterprise | All Hubs + Operations + Content Hub |
| Developer platform + custom objects | CRM + Operations (for automation) + Content Hub (for website) |

## Licensing Models

1. **Per-seat (User-based):** Marketing Hub, Sales Hub, Service Hub — pay per user who needs access
2. **Contact-based:** Marketing Hub — pay per marketing contact (contacts you send marketing emails to)
3. **Feature-based:** Operations Hub, Commerce Hub — different tiers unlock more features
4. **Add-ons:** Additional products (data sync, custom-coded actions, etc.)

## Key Concepts

### Objects
The core data types in HubSpot's CRM. Each object has properties (fields) and can be associated to other objects.

**Standard objects:** Contact, Company, Deal, Ticket, Product, Line Item, Quote, Invoice, Payment, Subscription, Goal, Task, Meeting, Call, Email, Communication

**Custom objects:** Define your own (e.g., Vehicle, Course, Project, Property)

### Properties
- Standard properties: hundreds pre-built (name, email, phone, industry, etc.)
- Custom properties: create your own (up to 10,000 per object on Enterprise)
- Property types: text, number, date, dropdown, checkbox, radio, file, calculation, etc.
- Calculated properties: formula-based (Operations Hub)
- Rollup properties: aggregate data from related objects (Operations Hub)

### Pipelines
Visual stages for tracking progress. Available for:
- Deals (sales pipeline)
- Tickets (support pipeline)
- Custom objects (enterprise)

### Lists
- **Static lists**: fixed set of records (manually added or removed)
- **Active lists**: dynamically updated based on criteria
- Use Lists for segmentation, workflows, email sends, reports

### Workflows
Automation rules that trigger actions when certain conditions are met. Available for contacts, companies, deals, tickets, custom objects.

### Campaigns
Group related marketing assets (emails, landing pages, ads, social posts) to track combined performance and attribution.

### Teams
Groups of HubSpot users for sharing records, reporting, and permissions.

### Roles & Permissions
Granular access control:
- User roles: Super Admin, specific Hub permissions, custom roles
- Object permissions: view-only, edit, delete
- Property-level permissions: restrict edit access to specific properties
- Teams: isolate data by geography, business unit, or product line

## AI & Breeze Intelligence

HubSpot's **Breeze AI** platform (launched 2024–2025) embeds artificial intelligence across every Hub. Breeze consists of two layers:

**Breeze Copilot**
- Conversational AI assistant available throughout the HubSpot UI
- Answers questions about your CRM data, suggests next actions
- Can create workflows, write email copy, generate reports, and auto-fill properties
- Context-aware — knows which record, list, or dashboard you're viewing
- Triggered via the Breeze icon or by typing "/" in any text field

**Breeze Intelligence**
- Enriches CRM records with firmographic and technographic data from 260M+ company profiles
- Intent signals (buying signals based on web research behavior)
- AI-powered lead scoring and predictive analytics
- Automated data cleansing and deduplication
- Available as a paid add-on to any Hub

**AI Features by Hub**

| Feature | Hub Availability |
|---------|-----------------|
| **AI Content Generation** (blog posts, emails, landing page copy, social posts) | Marketing Hub, Content Hub |
| **AI Lead Scoring** (predictive scoring based on behavioral data) | Marketing Hub (Pro+) |
| **AI Snippet Recommendations** (suggested email/reply content) | Sales Hub, Service Hub |
| **AI Chatbot / Agent** (conversational bots with LLM-powered replies) | Service Hub, Marketing Hub |
| **Predictive Analytics** (forecast deal probability, churn risk) | Sales Hub, Service Hub (Enterprise) |
| **AI Summaries** (auto-generated call summaries, ticket recaps) | Sales Hub, Service Hub |
| **Content AI** (generate images, rewrite tone, translate content) | Content Hub |
| **Smart CRM** (auto-suggest properties, auto-enrich records) | CRM Platform (Pro+) |

> Breeze AI is included in **Enterprise** tiers and available as an add-on for **Professional** tiers. Breeze Intelligence is a paid add-on available to all paid tiers.

## Sandbox Accounts

Enterprise accounts get access to **Sandbox** environments — isolated copies of your HubSpot portal for testing:
- **Standard Sandbox**: full copy of your production portal (data, settings, integrations)
- **Developer Sandbox**: lightweight environment for API and custom code testing
- Sandboxes are safe spaces to test workflows, automation, custom objects, and integrations before deploying to production

## Getting Started

### Step 1: Sign up
- Create a free HubSpot account at hubspot.com
- Free CRM includes contacts, deals, tasks, meetings, basic email, live chat, forms, pipelines

### Step 2: Import your data
- Import CSV files for contacts, companies, deals
- Connect Gmail/Outlook to track email opens
- Install HubSpot tracking code on website
- Connect social accounts (Facebook, LinkedIn, Twitter)

### Step 3: Set up your pipeline
- Create deal stages that match your sales process
- Set property requirements for each stage
- Configure email notifications for stage changes

### Step 4: Configure users & permissions
- Invite team members
- Assign roles and permissions
- Create teams for different departments

### Step 5: Connect integrations
- Connect Salesforce, Shopify, QuickBooks, or other tools
- Install HubSpot CRM tracking on your website

### Step 6: Start automating
- Create your first workflow (e.g., assign new leads to sales)
- Create your first sequence (follow-up emails for new leads)
- Set up lead routing rules

## Chapter Structure

This tutorial covers each Hub in detail:

| # | Chapter | Covers |
|---|---------|--------|
| 00 | **HubSpot Platform Overview** | This chapter — platform architecture, concepts, getting started |
| 01 | **CRM Foundation** | Contacts, Companies, Deals, Tickets, Properties, Pipelines, Lists |
| 02 | **Marketing Hub** | Email, Forms, Landing Pages, SEO/Blog, Social, Ads, Campaigns, Automation |
| 03 | **Sales Hub** | Sequences, Meetings, Calling, Deals, Quotes, Playbooks, Forecasting, CI |
| 04 | **Service Hub** | Ticketing, Knowledge Base, Chatbots, Feedback, CSAT/NPS, SLA, Customer Success |
| 05 | **Content Hub** (CMS) | Website Builder, HubL, Custom Modules, Blogging, Content AI, Local Dev |
| 06 | **Operations Hub** | Data Sync, Data Quality, Programmable Automation, Datasets, Calculated Properties |
| 07 | **Commerce Hub** | Payments, Invoicing, Subscriptions, CPQ, Accounting Integration |
| 08 | **Custom Objects & API** | Custom Objects, REST API, GraphQL, Webhooks, Private/Public Apps, SDKs |
| 09 | **Integrations & Automation** | Native Integrations, iPaaS, Workflow Patterns, Sequence Automation |
| 10 | **Pricing, Limits & Best Practices** | Pricing tiers, plan limits, scaling strategies, performance tips |

### Pricing note
HubSpot pricing changes regularly. Visit [hubspot.com/pricing](https://www.hubspot.com/pricing) for current prices. The limits listed in this tutorial are based on publicly available data as of mid-2025 and may vary by region and plan.