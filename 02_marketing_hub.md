# 2. Marketing Hub

## What It Does
HubSpot Marketing Hub provides tools for inbound marketing: attracting visitors, converting leads, nurturing prospects, and analyzing campaign performance. It covers email marketing, landing pages, forms, SEO/content, social media, ads, marketing automation, lead scoring, and analytics.

## Key Features

### Breeze AI Content Assistant
- **AI writing**: generate blog posts, emails, landing page copy, and social content with natural language prompts
- **AI image generation**: create custom images for blogs, landing pages, emails, and social posts using built-in AI image generator
- **AI translation**: translate content into multiple languages with one click (Pro+)
- **AI subject line generation**: automatically generate and test subject line variations for email campaigns
- **Content tone adjustment**: rewrite content for brand voice (formal, casual, professional, playful)
- **AI content repurposing**: reformat existing content for different channels (blog → social, email → landing page)
- **Brand voice settings**: define and enforce brand voice guidelines across all AI-generated content

### Email Marketing
- **Breeze AI email campaign generation**: generate full email campaigns — subject lines, body copy, CTAs, and images — with natural language prompts
- **Drag-and-drop email editor** with pre-built templates
- **Personalization tokens**: first name, company, deal info, custom properties
- **Smart content**: show different content based on list membership, lifecycle stage, device type, language, or contact properties
- **A/B testing**: test subject lines, content, send times
- **Email scheduling**: send immediately, schedule for later, or time-zone optimized send
- **Transactional emails**: order confirmations, password resets (not marketing)
- **Subscription management**: bulk email (marketing), one-to-one (sales), transactional
- **Unsubscribe management**: automated, one-click unsubscribe required
- **Reply-to routing**: replies go to shared inbox or specific email
- **Email analytics**: opens, clicks, bounces, unsubscribes, spam reports, click maps, device breakdown
- **Send time optimization**: send when each recipient is most likely to open (Pro+)
- **Email templates**: save as templates, clone, share across teams
- **Drag-and-drop builder**: modules, sections, global content
- **Domain management**: connect custom domains (up to 15 on Pro, unlimited on Enterprise)
- **SEO settings**: meta description, page title, URL slug, canonical URL
- **Smart content**: personalize landing pages per contact
- **A/B testing**: test page variants (Pro+)
- **Forms on landing pages**: embedded or pop-up, with progressive profiling
- **CTA buttons**: with click tracking
- **Password-protected pages**: member-only content
- **Responsive design**: mobile-optimized by default
- **Blog integration**: link landing pages from blog posts
- **Conversion analytics**: views → submissions, traffic sources

### Forms
- **Form types**: embedded form, pop-up form, slide-in form, inline form, floating footer
- **Field types**: text, email, phone, date, file upload, GDPR consent, checkboxes, radio, dropdown, multi-select
- **Progressive profiling**: show new fields to returning visitors (replace existing fields)
- **Smart fields**: hide fields if already known
- **Thank-you messages**: redirect to URL or show inline message
- **Lead flows**: pop-up forms triggered by exit intent, time on page, scroll percentage (Legacy)
- **Captcha**: Google reCAPTCHA v2 and v3
- **Post-submit actions**: follow-up email, workflow enrollment, lead assignment
- **HubSpot tracking code**: automatically tracks form submissions
- **Form pre-population**: populate with known contact data
- **File upload**: collect files via forms (limits apply)

### SEO / Blogging
- **Blog editor**: rich text with drag-and-drop modules
- **Topic clusters**: pillar page + cluster content model
- **SEO recommendations**: page-level analysis, suggested keywords, readability score
- **Content strategy tool**: topic suggestions based on search data
- **Keyword tracking**: rank tracking for target keywords (Pro+)
- **Internal linking recommendations**: connect related blog posts
- **Meta data editor**: title tag, meta description, URL slug
- **Structured data**: schema.org markup for blogs
- **Blog RSS**: auto-generated RSS feeds
- **Author pages**: author bios with social links
- **Multi-language blogging**: URL structure for i18n
- **Content calendar** (Content Hub)

### Social Media
- **Social publishing**: compose, schedule, and publish posts
- **Supported networks**: Facebook, LinkedIn, Twitter/X, Instagram, YouTube (limited)
- **Social listening**: monitor brand mentions (Enterprise)
- **Social analytics**: engagement, clicks, impressions, followers over time
- **Post re-engagement**: see past posts, reshare
- **Bulk scheduling**: upload CSV of posts
- **Approval workflows**: draft → review → publish (Pro+)
- **Content sharing**: share blog posts and landing pages to social

### Ads
- **Ad tracking**: track ad interactions for Google Ads, Facebook Ads, LinkedIn Ads, Instagram
- **Ad conversion attribution**: see which ads generate leads/customers
- **Ad audiences**: create retargeting audiences from HubSpot contact lists
- **Budget management**: view spend, impressions, clicks (read-only, manage in ad platform)
- **Lead ad sync**: sync Facebook/Instagram/LinkedIn lead ads to HubSpot
- **UTM parameter tracking**: auto-tagging and tracking

### Campaigns
- **Campaign creation**: name, goal, budget, start/end dates
- **Asset grouping**: associate emails, landing pages, ads, social posts, CTAs, workflows, lists
- **Campaign analytics**: ROI, influence, contacts created, revenue attributed
- **Multi-touch attribution**: first interaction, last interaction, linear, U-shaped, W-shaped, time decay
- **Campaign reporting**: dashboard of all assets' performance

### Marketing Automation (Workflows)
- **Trigger types**: contact-based (form submission, list membership, property change, date-based), company-based, deal-based, ticket-based
- **Actions**: send email, add to list, remove from list, create task, set property value, enroll in sequence, create deal, trigger webhook, branch (if/then), delay, goal, rotate lead
- **Enrollment criteria**: AND/OR logic with property conditions, list membership, form submissions, page views
- **Goal-based workflows**: enroll until goal met (e.g., "contact becomes customer")
- **Re-enrollment**: configure re-enrollment triggers
- **Workflow history**: visual audit trail of contacts through workflow
- **Error handling**: logs for enrollment failures, action failures
- **Versioning**: save workflow versions, rollback

### Lead Scoring
- **Positive attributes**: +X points for property values, page views, form submissions, email clicks, behaviors
- **Negative attributes**: -X points for unsubscribes, bounces, inactivity
- **Scoring tiers**: set score ranges that map to lifecycle stages
- **Fit scoring**: demographic fit (industry, job title, company size, location)
- **Behavior scoring**: engagement level
- **Predictive lead scoring** (Content Hub Enterprise, Sales/Service Enterprise): ML-based scoring
- **Workflow integration**: trigger workflows when score changes

### Analytics
- **Traffic analytics**: sources (organic, paid, direct, social, email, referrals), pages, devices, locations
- **Contact analytics**: contacts created, engaged, converted by source
- **Conversion analytics**: from visitor → contact → customer
- **ROI reporting**: revenue generated vs. cost spent
- **Custom report builder**: drag-and-drop report creation
- **Dashboard creation**: shareable, filterable, scheduled emails
- **Attribution reporting**: multi-touch attribution models

## Step-by-Step: Creating an Email Campaign
1. Marketing > Email > Create email
2. Choose template (blank, pre-built, or saved template)
3. Name your email in the settings panel
4. Set sender details: From name, From address, Reply-to address
5. Personalize subject line: use {{ contact.firstname }} tokens
6. Build content: drag modules (text, image, CTA, video, social follow, etc.)
7. Add smart content rules (Pro+): Device type, Contact list membership, Lifecycle stage, Language
8. Set send settings: send to list, send at specific time, time-zone optimized, A/B test variant
9. Preview and test: send test to your own email, test rendering in different clients
10. Review compliance: verify unsubscribe link, physical address, permission basis
11. Review > Send or Schedule

## Step-by-Step: Creating a Marketing Automation Workflow
1. Automation > Workflows > Create workflow
2. Choose type: Contact-based, Company-based, Deal-based, Ticket-based, Custom object-based
3. Set enrollment triggers (can be blank for manual enrollment)
4. Add branches: Set up if/then logic (e.g., if contact has role "Manager")
5. Add actions in sequence:
   - Send email (choose from existing marketing emails)
   - Add to/remove from static list
   - Set property value (e.g., set Lifecycle Stage to "Customer")
   - Create task (e.g., "Call this lead")
   - Enroll in sequence (Sales Hub)
   - Delay (specific time, X days, or until day of week/time)
   - Goal (wait until condition met, e.g., "deal created")
6. Configure re-enrollment: When should contacts re-enter?
7. Turn on workflow

## Step-by-Step: Progressive Profiling on Forms
1. Settings > Marketing > Forms
2. Create new form or edit existing
3. Add all fields you want to collect over time
4. Click on a field → "Progressive Profiling" tab
5. Check "Use progressive profiling" (form must have at least 4 extra fields beyond contact identity)
6. Set how many fields to show per submission (default: 1 new field)
7. Order fields by priority (drag to reorder)
8. Configure identity fields (email is default identifier)
9. Save

## Limits That Matter
- Marketing contacts: Free (0), Starter (1,000), Pro (2,000 base + $250/1,000), Enterprise (10,000 base + $225/1,000)
- Emails per month: Free (2,000 send limit), Pro (10x marketing contacts count), Enterprise (12x)
- Email send frequency: no hard limit but deliverability declines >1 per day per contact
- Landing pages: Free (20), Starter (70), Pro (100), Enterprise (unlimited)
- Forms: Free (1,000), Starter (5,000), Pro (50,000), Enterprise (unlimited)
- Workflows: Free (5), Starter (20), Pro (500), Enterprise (1,000+)
- Blog posts: Free (250), Starter (2,500), Pro (unlimited)
- Social accounts: Free (5), Starter (10), Pro/Enterprise (unlimited on some plans)
- A/B test variants: up to 5 per test
- Form fields per form: 100
- File upload size via forms: 5MB per file
- Recipients per email send: up to 100 per email on Free tier (Starter+) unlimited per send

## Use Cases
- Nurture leads through automated email drip sequences
- Generate conversions with targeted landing pages and forms
- Improve organic search ranking through topic clusters
- Score leads based on behavior and demographic fit
- Attribute revenue to specific marketing campaigns
- Manage multi-channel campaigns (email, social, ads)

## Common Gotchas
- Marketing contacts vs non-marketing contacts: you pay for marketing contacts who are sent marketing emails; contacts can be set as "non-marketing" to save cost
- Sending too many marketing emails hurts deliverability — HubSpot enforces bounce/reputation management
- Progressive profiling won't work on all form styles (best with multi-step or embedded forms)
- Workflow enrollment is evaluated on trigger — if contact doesn't meet criteria at trigger time, they won't enroll retroactively
- Removing someone from a workflow does NOT undo actions already taken (emails already sent)
- A/B testing in email requires minimum sample size (usually 20-50% of list before winner determined)
- Landing page domains must have SSL configured (auto-provided but custom domains need DNS config)
- Blog post URLs cannot be changed once published (redirect recommended)
- Topic cluster pillar page auto-detection requires internal links from cluster pages back to pillar
