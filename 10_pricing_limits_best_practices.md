# 10. Pricing, Limits & Best Practices

## What It Does
This chapter helps you plan your HubSpot implementation by understanding pricing tiers, hard limits, soft limits, and proven best practices for scaling on the platform.

## Pricing Summary (Approximate — Mid 2025)

| Hub | Free | Starter | Professional | Enterprise |
|-----|------|---------|-------------|------------|
| **CRM** | ✓ Full | — | — | — |
| **Marketing Hub** | ✓ Limited | ~$20/mo | ~$890/mo | ~$3,600/mo |
| **Sales Hub** | ✓ Limited | ~$15/mo | ~$100/mo/seat | ~$150/mo/seat |
| **Service Hub** | ✓ Limited | ~$20/mo | ~$100/mo/seat | ~$200/mo/seat |
| **CMS/Content Hub** | ✓ Limited | ~$25/mo | ~$450/mo | ~$1,500/mo |
| **Operations Hub** | — | ~$30/mo | ~$800/mo | ~$2,000/mo |
| **Commerce Hub** | — | Add-on | Add-on | Add-on |

**Breeze AI & Breeze Intelligence add-ons:**
- Breeze Copilot: included in Enterprise; add-on for Professional (price varies)
- Breeze Intelligence: paid add-on available to all paid tiers (~$200–$500/mo depending on contact volume)
- AI content generation: included in Content Hub; Marketing Hub Pro add-on

**Pricing factors:**
- Marketing Hub price scales with **marketing contact count** (more contacts = higher base tier)
- Sales/Service/CMS Hub price scales with **seat count**
- Enterprise typically requires an annual contract (monthly available for lower tiers)
- Contact HubSpot sales for custom enterprise and bundled pricing
- Prices are in USD — regional pricing may vary

## Hard Limits Checklist

### CRM & Objects

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Contacts | 1M | 1M | Unlimited | Unlimited |
| Companies | 100k | 500k | 1M | Unlimited |
| Deals | No limit | No limit | No limit | No limit |
| Custom objects | 0 | 0 | 10 | 200 |
| Custom object records | — | 100k | 1M | 10M+ |
| Custom properties/object | 1k | 1k | 1k | 10k |
| Property options/dropdown | 1k | 1k | 1k | 1k |
| Pipelines (deals) | 1 | 10 | 50 | 100 |
| Pipeline stages (deals) | 10 | 30 | 30 | 30 |
| Lists (active) | 1k | 2k | 5k | 10k |
| Lists (static) | 1k | 5k | 10k | 20k |
| Teams | 1 | 3 | 15 | Unlimited |

### Marketing

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Marketing contacts | 0 | 1k | 2k base | 10k base |
| Blog posts | 250 | 2,500 | Unlimited | Unlimited |
| Website pages | 25 | 100 | Unlimited | Unlimited |
| Landing pages | 20 | 70 | 100 | Unlimited |
| Forms | 1k | 5k | 50k | Unlimited |
| Workflows | 5 | 20 | 500 | 1,000+ |
| Emails per month | 2k | Varies | 10x contacts | 12x contacts |
| A/B tests | — | — | 5 concurrent | 10 concurrent |
| Smart content rules | — | — | 100 | 1,000 |
| Custom domains | 1 | 5 | 15 | Unlimited |
| Social accounts | 5 | 10 | Unlimited | Unlimited |

### Sales

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Meeting links/user | 5 | 5 | 5+ | 5+ |
| Sequences | 1 | 3 | 20 | Unlimited |
| Active sequence enrollments | 50 | 250 | 1k/user | 2k/user |
| Sequence steps | 5 | 10 | 50 | 50 |
| Email templates | 5 | 100 | 500 | Unlimited |
| Playbooks | — | — | 50 | 500 |
| Quotes | — | — | ✓ | ✓ |
| Forecasting | — | — | 8 periods | Unlimited |
| Calling minutes | — | — | US included | US included |
| Conversation Intelligence | — | — | — | ✓ |
| Deal splits | — | — | — | Up to 15 |

### Service

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Tickets | 1k lifetime | 5k lifetime | Unlimited | Unlimited |
| Ticket pipelines | 1 | 3 | 10 | Unlimited |
| KB articles | 100 | 2,500 | Unlimited | Unlimited |
| Chatbots | 1 | 1 | 5 | Unlimited |
| Feedback surveys | 3 | 10 | 100 | Unlimited |
| SLA | — | — | Tracking | Full + escalations |
| Customer portal | Read-only | Read-only | Respond | Respond |
| CSAT/NPS | — | — | ✓ | ✓ |

### CMS / Content Hub

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Bandwidth | 10GB | 100GB | 300GB | 2TB+ |
| Storage | 1GB | 10GB | 25GB | 100GB+ |
| Custom modules | 50 | 100 | Unlimited | Unlimited |
| HubDB tables | 5 | 20 | 100 | 500 |
| HubDB rows/table | 100 | 5k | 10k | 50k |
| Serverless functions | — | — | — | ✓ |
| Content staging | — | — | ✓ | ✓ |
| Content branches | — | — | — | ✓ |

### API & Development

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| API rate limit | 100/10s | 100/10s | 150/10s | 200/10s |
| API daily limit | 250k | 500k | 1M | Varies |
| Private apps | 3 | 10 | 50 | Unlimited |
| Webhook subscriptions | 10 | 50 | 200 | 500 |
| Custom-coded actions | — | — | 10 (Ops Hub) | 200 (Ops Hub) |
| Custom-coded cards | — | — | — | ✓ |
| SDKs | ✓ | ✓ | ✓ | ✓ |

## Best Practices

### CRM Data Management

1. **Plan your properties before creating them**
   - Property internal names cannot be changed — plan carefully
   - Use naming conventions: `is_paying_customer`, `last_contacted_date`, `preferred_channel`
   - Group related properties — keep your CRM organized with property groups

2. **Use custom objects for complex domains**
   - Don't cram everything into Contact properties
   - If a data type has its own lifecycle, it's probably a custom object
   - Example: Courses (each with start date, instructor, curriculum) → custom object, not contact property

3. **Deduplicate regularly**
   - Run dedup reports monthly
   - Set up duplicate prevention at import
   - Merge thoughtfully — check both records before merging

4. **Set property validation**
   - Make email required on contacts
   - Set phone number format rules (data quality automation in Operations Hub)
   - Use dropdowns instead of free text for standard fields

### Marketing Best Practices

5. **Marketing contacts vs non-marketing contacts**
   - Only pay for contacts you send marketing emails to
   - Set contacts to "non-marketing" if they're only transactional or support-only
   - Save on costs — don't mark all contacts as marketing

6. **Progressive profiling for long-term data collection**
   - Don't ask for everything on the first form
   - Collect over time: email → name → company → role → budget → timeline
   - Higher conversion rates with shorter initial forms

7. **Workflow hygiene**
   - Name workflows clearly: "Campaign Name — Trigger — Goal"
   - Archive old workflows instead of deleting (delete undoes enrollment)
   - Set re-enrollment limits to prevent infinite loops
   - Monitor workflow error logs weekly

8. **Email deliverability**
   - Warm up new sending domains (start with low volume)
   - Monitor bounce rate (keep under 2%)
   - Use double opt-in for critical lists
   - Don't send more than 1 marketing email per day per contact
   - Authenticate your sending domain (SPF, DKIM, DMARC)

### Sales Best Practices

9. **Pipeline hygiene**
   - Keep deal stages accurate — stale deals skew forecasting
   - Move lost deals to Closed Lost (don't delete — keep data for analysis)
   - Use deal probability aligned with actual conversion rates
   - Review pipeline weekly — flag deals stuck in same stage > 30 days

10. **Sequence best practices**
    - Keep sequences 3-6 steps max
    - Add manual tasks between emails (calls, research)
    - Set reply detection — unenroll immediately when contact replies
    - Don't sequence existing customers without segmenting
    - Personalize first email (not just `{{ contact.firstname }}`)

11. **Forecasting accuracy**
    - Train reps on proper stage probability
    - Review commit vs best case vs pipeline weekly
    - Use historical data to calibrate stage probabilities
    - Don't let reps pad pipeline with unlikely deals

### Service Best Practices

12. **SLA configuration**
    - Set realistic SLA targets based on current performance + improvement goal
    - Monitor SLA breach rate weekly
    - Escalate breached tickets immediately (auto-assign to senior)
    - Consider 24/7 vs business-hours SLAs

13. **Knowledge base optimization**
    - Analyze top search queries — create articles for the most searched terms
    - Link KB articles in chatbot flows
    - Track article helpfulness — rewrite articles with low ratings
    - Review and update articles quarterly

### Development Best Practices

14. **API usage**
    - Use OAuth 2.0 or Private App tokens (not shared API keys) for security
    - Implement proper retry logic with exponential backoff
    - Batch API calls where possible (max 100 records per batch)
    - Monitor rate limit headers — implement client-side throttling
    - Use Private App tokens for internal integrations (scoped permissions)

15. **Custom objects**
    - Plan internal names carefully — they're permanent
    - Start with a few properties, iterate
    - Set primary display property early (affects search results)
    - Test association labels with real-world use cases

16. **Webhooks**
    - Always verify HMAC signatures on incoming webhooks
    - Process webhooks idempotently (implement duplicate detection)
    - Respond quickly (< 5 seconds) to avoid retries
    - Use webhooks for real-time sync, not bulk operations

### General Platform Best Practices

17. **Regular audits**
    - Monthly: Review unused properties, pipelines, workflows
    - Quarterly: Clean up contacts, companies, lists
    - Bi-annual: Review roles and permissions, archive stale content

18. **Training your team**
    - Document your internal HubSpot conventions
    - Train new users on data entry standards
    - Create internal playbooks for common processes
    - Use sandbox account for testing (Enterprise feature)

19. **Scaling up**
    - Start with Free CRM + one paid Hub
    - Add Hubs as processes mature (don't buy all at once)
    - Use Operations Hub when data sync/quality becomes painful
    - Add Commerce Hub when you need built-in billing and subscriptions
    - Enterprise features (custom-coded cards, content branches, sandbox) solve specific advanced needs

20. **Performance optimization**
    - Archive old active lists (active lists scan all contacts — impacts load times)
    - Limit property count on records (fewer properties = faster loads)
    - Use custom objects for large datasets (not overloaded properties)
    - Monitor workflow execution time — complex workflows with many branches can timeout
    - API search queries over large datasets may need pagination + filters

21. **Leverage Breeze AI**
    - Use Breeze Copilot to build workflows and reports faster
    - Enable Breeze Intelligence enrichment for cleaner, richer CRM data
    - Use AI content generation for blog posts, emails, and landing pages
    - Review AI-suggested automations — HubSpot often catches patterns you missed

22. **Cost management**
    - Regularly audit marketing contact counts — convert inactive contacts to non-marketing
    - Review seat usage — remove inactive users to reduce paid seats
    - Use bundles (Marketing + Sales + Service) for lower combined pricing
    - Start with free/Starter tiers, upgrade only when limits are consistently hit

## Common Mistakes to Avoid

| Mistake | Why It Hurts | Fix |
|---------|-------------|-----|
| Too many custom properties | Clutters UI, slows page load | Create custom objects for complex domains |
| Not setting re-enrollment limits | Workflow loops, infinite enrollments | Always set max re-enrollment = 1 unless needed |
| No property validation | Inconsistent data (Manila / manila / PH-MNL) | Use dropdowns + data quality format rules |
| Over-segmenting lists | Thousands of near-empty list entries | Use active lists with property filters instead |
| API key exposure in code | Security risk | Use OAuth 2.0 or Private App tokens |
| Marketing too many contacts | High costs | Set non-marketing for support/transactional contacts |
| Skipping sandbox | Breaking production on CMS changes | Use content staging (Pro+) or sandbox (Enterprise) |
| Not monitoring rate limits | Integrations break silently | Log rate limit headers, implement backoff |
| Merging without review | Lost data | Check both records carefully before merge |
| Buying all Hubs Day 1 | Wasted budget on unused features | Start small, add Hubs when process is ready |
| Ignoring Breeze AI features | Missing efficiency gains | Explore Breeze Copilot — it's included in most paid plans