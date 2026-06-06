# HubSpot Complete Tutorial — The Definitive Guide

A comprehensive, deeply detailed tutorial covering the **entire HubSpot platform**. From CRM foundation to advanced development — written for marketers, sales teams, service professionals, developers, and operations managers.

**Format**: Tutorial-style with step-by-step instructions, configuration walkthroughs, best practices, real-world examples, common gotchas, and use cases for every feature.

---

## Chapters

| # | Chapter | Words | Covers |
|---|---------|-------|--------|
| 00 | [HubSpot Platform Overview](00_overview.md) | ~7,200 | Architecture, flywheel philosophy, all 6 hubs overview, Breeze AI platform (Copilot, Breeze Intelligence, AI Agents), licensing models, key concepts (objects, properties, pipelines, workflows, lists), getting started step-by-step, ecosystem, migration, security & compliance, sandboxes |
| 01 | [CRM Foundation](01_crm.md) | ~6,500 | Contacts (import CSV, merge, lifecycle stages, enrichment, ownership, GDPR), Companies (domains, hierarchies, insights), Deals (pipelines, stages, line items, splits, Kanban board), Tickets (status, priority, pipelines), Properties (all types, custom, calculated formulas, rollup), Pipelines (creation, stage rules, rotation), Lists (static vs active, criteria, AND/OR logic), Activities (email, calls, meetings, notes, tasks), Associations (labels, cardinality), Reporting (custom report builder, attribution) |
| 02 | [Marketing Hub](02_marketing_hub.md) | ~6,200 | Breeze AI Content Assistant (generation, brand voice, images, translation), Email Marketing (drag-and-drop editor, personalization tokens, smart content, A/B testing, send time optimization, transactional, subscription management), Forms (5 types, progressive profiling, all field types, Captcha, GDPR), Landing Pages (templates, domains, SSL, smart content, SEO), SEO & Blogging (topic clusters, strategy tool, SEO analysis), Social Media (publishing, approval workflows, analytics), Ads (tracking, retargeting, lead ad sync), Campaigns (asset grouping, multi-touch attribution), Marketing Automation (all triggers, actions, branching, goals, re-enrollment), Lead Scoring (fit, behavior, predictive), Analytics (traffic, contacts, ROI, custom dashboards) |
| 03 | [Sales Hub](03_sales_hub.md) | ~4,700 | Email Tracking & Templates (setup, snippets, AI recommendations, document tracking), Sequences (create, enrollment, unenrollment triggers, conditional branching, analytics), Meetings (scheduling, round-robin, group, calendar sync, buffers), Calling (VoIP setup, local presence, recording, transcription, power dialer), Conversation Intelligence (AI summaries, coaching, keyword spotting, sentiment analysis, scorecards, playlists), Deal Management (board view, line items, splits, auto-assignment), Lead Management (scoring, rotation, prospecting workspace), Quotes (builder, templates, approval workflows, e-signature), Playbooks (MEDDIC, BANT, SPIN, Challenger), Forecasting (setup, categories, team hierarchy, AI predictions, what-if analysis), LinkedIn Sales Navigator, Multi-Currency |
| 04 | [Service Hub](04_service_hub.md) | ~4,100 | Ticketing (email-to-ticket, status, priority, pipelines, auto-assignment, collaboration), Knowledge Base (article creation, categories, search, multi-language, ticket deflection), Chatbots (flow-based bots, AI Agent with Breeze, routing rules, human handoff, off-hours behavior), Feedback Surveys (CSAT, NPS, CES creation, distribution, timing, analytics), Customer Success (health scoring, renewal management, lifecycle stages), Help Desk (shared inbox, canned responses, assignment rules), Service Automation (workflows for tickets, SLAs, post-resolution check-ins), SLA Management (metrics, targets, breach actions, business hours, reporting), Analytics (ticket volume, agent performance, CSAT trends, SLA compliance), Breeze AI (ticket summaries, agent, predictive churn) |
| 05 | [Content Hub (CMS)](05_cms_content_hub.md) | ~4,000 | Website Builder (themes, drag-and-drop editor, global content, SEO settings), HubL Templating (variables, filters, control flow, for loops, macros, functions, extends/inheritance), Custom Modules (field schemas, templates, CSS, JS — with code examples), Blogging (setup, content calendar, editor, multi-language, RSS), Content AI (blog generation, image generation, translation, brand voice), Local Development (CLI commands, project structure, git integration), Serverless Functions (Node.js code examples, secrets, logging), HubDB (table creation, row querying, dynamic pages, use cases), Multi-Language (setup, URL structure, language switcher, hreflang), Membership & Gating (password, registration, tiers), Adaptive Testing |
| 06 | [Operations Hub](06_operations_hub.md) | ~3,000 | Data Sync (bi-directional setup, field mapping, conflict resolution, supported connections), Data Quality (deduplication rules, fuzzy matching, property standardization, dashboard), Programmable Automation (custom-coded actions in JavaScript/Python with code examples, webhook actions, environment variables), Datasets/SQL (query syntax, joins, aggregation, scheduled exports), Calculated Properties (formula syntax, functions, IF/AND/OR, date math), Rollup Properties (SUM, COUNT, AVG on associated records), Data Pipeline (Snowflake, BigQuery, Redshift), Automation Patterns (data quality, account-based alerting, lead-to-account matching, revenue recognition) |
| 07 | [Commerce Hub](07_commerce_hub.md) | ~2,400 | Payments (Stripe setup, payment links, checkout experience, dispute management, refunds), Invoicing (creation, templates, recurring invoices, automation), Subscriptions (plan creation, subscriber management, lifecycle, dunning management, plan changes), CPQ (product bundles, pricing rules, volume discounts, tiered pricing, contract term discounts, guided selling, approval flows), Accounting Integrations (QuickBooks, Xero, NetSuite setup and sync), Tax Management (manual, Avalara, VAT/GST, jurisdiction support), Billing Portal (self-service setup), Payment Reporting (revenue dashboard, MRR/ARR, churn rate, LTV, reconciliation) |
| 08 | [Custom Objects & API](08_custom_objects_api.md) | ~3,200 | Custom Objects (create via UI and API, properties, associations, type IDs, records CRUD), REST API (authentication, endpoints, search API with filter operators, batch operations, rate limits, error handling), GraphQL API (queries, nested associations, limitations), Webhooks (event types, setup, HMAC signature verification in JS and Python, payload format, retry policy), Private Apps (create, scopes, token management), Public Apps (OAuth flow, marketplace listing, monetization), SDKs (Python and Node.js with code examples for CRUD, search, batch), Custom Behaviors (cards, actions, bots, timeline events — Enterprise), HubSpot CLI (installation, all commands, project structure) |
| 09 | [Integrations & Automation](09_integrations_automation.md) | ~2,700 | Native Integrations (Gmail, Outlook, Calendar, Slack, Zoom, WhatsApp, Facebook Messenger, Salesforce, Shopify, LinkedIn Sales Nav, WordPress, DocuSign, Asana), iPaaS (Zapier triggers/actions, Make scenarios, Workato enterprise features — with comparison), Advanced Workflow Patterns (multi-branch orchestration, goal-based with escalation, data quality pipeline, revenue recognition), Sequence Automation Patterns (triggered enrollment, re-engagement, post-purchase upsell), Cross-Hub Automation (Marketing→Sales handoff, Sales→Service onboarding, Service→Sales upsell), Custom Integration Architecture (webhook-based, scheduled sync, real-time bidirectional), Testing & Monitoring (sandbox testing, staging, metrics, alert thresholds) |
| 10 | [Pricing, Limits & Best Practices](10_pricing_limits_best_practices.md) | ~3,700 | Pricing breakdown per hub (all tiers with marketing contacts pricing), Add-Ons (Breeze Intelligence, video, dedicated IP, API overages, professional services), Cost Optimization Strategies (right-sizing, reducing marketing contacts, bundling, annual contracts, nonprofit discounts, seat management, Operations Hub vs custom dev), Plan Limits (complete reference table for every resource across all tiers), Scaling Strategies (free→starter→pro→enterprise upgrade paths, multi-portal strategy), Migration Guide (Salesforce step-by-step: audit, clean, setup, migrate, test, train, go live; Zoho/Pipedrive migration; tools), Performance Optimization (CRM, automation, content, API), Vendor Comparisons (HubSpot vs Salesforce, Zoho, Pipedrive, ActiveCampaign/Mailchimp), Best Practices Summary (data management, users, automation, reporting, AI, integrations, security) |

---

## Structure

Each chapter is a self-contained tutorial with:

- **What It Is** — Plain English explanation of the feature
- **Where to Find It** — Exact navigation path (Menu > Submenu > Feature)
- **Step-by-Step Instructions** — Numbered steps with all configuration options explained
- **Multiple Examples** — Different scenarios showing feature in practice
- **Best Practices** — Real-world recommendations from experienced users
- **Common Mistakes** — Pitfalls and how to avoid them
- **Limits That Matter** — Hard caps per plan tier (Free, Starter, Pro, Enterprise)
- **Use Cases** — When and why to use each feature

---

## How to Use This Tutorial

1. **Start with Chapter 00** (Platform Overview) if you're new to HubSpot
2. **Jump to any chapter** based on your role:
   - **Marketers**: Chapter 02 (Marketing Hub) + Chapter 05 (Content Hub)
   - **Sales teams**: Chapter 03 (Sales Hub)
   - **Service/support**: Chapter 04 (Service Hub)
   - **Developers**: Chapter 08 (Custom Objects & API) + Chapter 05 (Content Hub dev)
   - **Operations**: Chapter 06 (Operations Hub) + Chapter 09 (Integrations)
   - **Finance/execs**: Chapter 10 (Pricing & Best Practices)
3. **Read relevant chapters together** for cross-functional workflows:
   - Marketing → Sales: Chapters 02 + 03 + 09
   - Sales → Service: Chapters 03 + 04 + 09
   - Full stack: Chapters 01 + 02 + 03 + 04 + 06

---

## Target Lengths

| Chapter | Current | Target |
|---------|---------|--------|
| 00. Overview | ~7,200 words | 20,000 |
| 01. CRM | ~6,500 words | 20,000 |
| 02. Marketing | ~6,200 words | 20,000 |
| 03. Sales | ~4,700 words | 20,000 |
| 04. Service | ~4,100 words | 20,000 |
| 05. Content Hub | ~4,000 words | 20,000 |
| 06. Operations | ~3,000 words | 20,000 |
| 07. Commerce | ~2,400 words | 20,000 |
| 08. API/Dev | ~3,200 words | 20,000 |
| 09. Integrations | ~2,700 words | 20,000 |
| 10. Pricing | ~3,700 words | 20,000 |
| **Total** | **~48,600 words** | **~220,000 words** |

---

*Created with HubSpot Complete Tutorial series. Last updated: June 2026.*
