# 2. Marketing Hub — Complete Tutorial

## Table of Contents
1. [Introduction to Marketing Hub](#introduction-to-marketing-hub)
2. [Breeze AI Content Assistant](#breeze-ai-content-assistant)
3. [Email Marketing — Complete Guide](#email-marketing--complete-guide)
4. [Forms — Complete Guide](#forms--complete-guide)
5. [Landing Pages — Complete Guide](#landing-pages--complete-guide)
6. [SEO & Blogging — Complete Guide](#seo--blogging--complete-guide)
7. [Social Media — Complete Guide](#social-media--complete-guide)
8. [Ads — Complete Guide](#ads--complete-guide)
9. [Campaigns — Complete Guide](#campaigns--complete-guide)
10. [Marketing Automation (Workflows) — Complete Guide](#marketing-automation-workflows--complete-guide)
11. [Lead Scoring — Complete Guide](#lead-scoring--complete-guide)
12. [Analytics & Reporting — Complete Guide](#analytics--reporting--complete-guide)
13. [Limits That Matter](#limits-that-matter)
14. [Common Gotchas](#common-gotchas)
15. [Use Cases](#use-cases)

---

## Introduction to Marketing Hub

Marketing Hub is HubSpot's inbound marketing suite. It provides everything you need to attract visitors, convert leads, nurture prospects, and measure campaign ROI — all within the same CRM where your sales and service teams work.

### What Marketing Hub Includes

| Feature | Free | Starter | Pro | Enterprise |
|---------|------|---------|-----|------------|
| Email marketing | 2,000 sends/mo | 10× contacts/mo | 10× contacts/mo | 12× contacts/mo |
| Forms | 1,000 forms | 5,000 forms | 50,000 forms | Unlimited |
| Landing pages | 20 pages | 70 pages | Unlimited | Unlimited |
| Blogging | 250 posts | 2,500 posts | Unlimited | Unlimited |
| Social media | 5 accounts | 10 accounts | Unlimited | Unlimited |
| Workflows | 5 active | 20 active | 500 active | 1,000+ active |
| Lead scoring | ✗ | ✗ | ✓ | ✓ |
| A/B testing | ✗ | ✗ | ✓ | ✓ |
| Smart content | ✗ | ✗ | ✓ | ✓ |
| Multi-touch attribution | ✗ | ✗ | ✓ | ✓ |

### Navigation

The Marketing Hub navigation is in the top menu bar under **Marketing**. Sub-sections:

- **Marketing** > **Email** — Email campaigns, templates, analytics
- **Marketing** > **Forms** — Form builder, embedded forms, pop-up forms
- **Marketing** > **Landing Pages** — Page builder, templates, performance
- **Marketing** > **Blog** — Blog posts, content calendar, SEO
- **Marketing** > **Social** — Social publishing, monitoring, analytics
- **Marketing** > **Ads** — Ad tracking, audiences, analytics
- **Marketing** > **Campaigns** — Campaign management, asset grouping, attribution
- **Marketing** > **Lead Scoring** — Score criteria, scoring models
- **Automation** > **Workflows** — Marketing automation workflows
- **Reports** > **Marketing** — Traffic, conversion, email, social, SEO dashboards

---

## Breeze AI Content Assistant

Breeze AI is built into Marketing Hub to accelerate content creation and optimization.

### AI Content Generation

The AI Content Assistant can generate:

**Blog posts**: Give it a topic, target audience, key points, and tone. It generates a complete blog post with headings, body, and a call-to-action.

**Email campaigns**: Provide a goal (welcome, promotion, newsletter, re-engagement). The AI generates subject lines, body copy, CTAs, and even images.

**Landing page copy**: Describe your offer (ebook, webinar, trial). The AI writes headline, subheadline, bullet points, and CTA text.

**Social media posts**: Extend blog content to social posts for multiple platforms (LinkedIn, Twitter/X, Facebook, Instagram).

### How to Use AI Content Assistant

1. Open any content editor (blog, email, landing page)
2. Click the Breeze AI icon (sparkle) in the editor toolbar
3. Choose what you want to create: "Generate blog post", "Rewrite paragraph", "Shorten text", "Translate", "Change tone"
4. For generation: Enter a prompt describing what you need
5. Click "Generate"
6. Review the output — you can regenerate, edit, or accept
7. Modify as needed (AI is a starting point, not a final draft)

### Brand Voice Settings

Define your brand's voice so AI-generated content stays consistent:

1. **Settings** > **Marketing** > **Brand Voice**
2. Click "Create brand voice profile"
3. Fill in:
   - Brand description: "A modern B2B SaaS company helping small businesses manage finances"
   - Tone: Casual, Professional, Playful, Formal, Authoritative, Friendly
   - Words to use: Industry-specific terminology
   - Words to avoid: Competitor names, outdated terms
   - Style preferences: Contractions (yes/no), humor level, sentence length
4. Save — AI will use this voice profile when generating content

### AI Image Generation

Generate custom images for blog posts, landing pages, emails, and social:

1. In any content editor, click the image module
2. Select "Generate with AI"
3. Describe the image you want: "A modern office with plants and natural lighting, diverse team collaborating"
4. Choose style: Photorealistic, Illustration, Flat design, 3D render, Watercolor
5. Set dimensions (16:9 for blog, 1:1 for social, 4:3 for email)
6. Click "Generate"
7. Choose from 4 generated options
8. Add, edit, or regenerate

### AI Translation

Translate any content into supported languages with one click:

1. Open blog post, landing page, or email
2. Click the language dropdown in the settings panel
3. Select "Add language"
4. Choose target language from 20+ options
5. AI generates the translation maintaining formatting and links
6. Review and publish

Supported languages include: Spanish, French, German, Italian, Portuguese, Dutch, Japanese, Chinese (Simplified), Chinese (Traditional), Korean, Arabic, Russian, Swedish, Norwegian, Danish, Finnish, Polish, Turkish, Thai, Vietnamese, Indonesian

---

## Email Marketing — Complete Guide

### Email Editor Walkthrough

The drag-and-drop email editor is the heart of Marketing Hub's email capabilities.

**Creating an email**:
1. **Marketing** > **Email** > Create email
2. Choose from:
   - **Regular email**: Standard marketing email
   - **Automated email**: Trigger-based (e.g., abandoned cart)
   - **Blog/RSS email**: Auto-send new blog posts to subscribers
   - **Transactional email**: Operational emails (order confirmations, password resets)
3. Select a template:
   - **Blank template**: Start from scratch
   - **Pre-built templates**: HubSpot's library of responsive templates
   - **Saved templates**: Your team's previously saved templates
   - **Drag-and-drop templates**: Fully customizable

### The Email Editor Interface

The editor has three main areas:

**Left sidebar — Modules**:
- Text, Image, Button, Divider, Spacer, Social Follow, Video, CTA, Header, Footer, Logo
- Drag modules into the email body
- Each module has customizable settings (padding, background color, borders, visibility on mobile)

**Center — Preview canvas**:
- WYSIWYG view of your email
- Toggle between Desktop and Mobile views (critical for responsive testing)
- Click any module to edit its content and settings

**Right panel — Settings** (click a module to see):
- **Content tab**: Text, links, images for the selected module
- **Style tab**: Font, color, size, padding, alignment
- **Advanced tab**: CSS classes, conditional visibility

### Personalization Tokens

Insert dynamic content from the contact's CRM record:

| Token | What It Shows | Example Output |
|-------|--------------|----------------|
| `{{ contact.firstname }}` | Contact's first name | "Hi Jane!" |
| `{{ contact.lastname }}` | Contact's last name | "Doe" |
| `{{ contact.email }}` | Email address | "jane@example.com" |
| `{{ contact.company }}` | Company name | "Acme Corp" |
| `{{ contact.jobtitle }}` | Job title | "Marketing Manager" |
| `{{ contact.phone }}` | Phone number | "+1 (555) 123-4567" |
| `{{ contact.city }}` | City | "San Francisco" |
| `{{ contact.country }}` | Country | "United States" |
| `{{ owner.firstname }}` | Contact owner's first name | "Sarah" |
| `{{ custom.property_name }}` | Custom property | Any custom value |
| `{{ subscription.bulk }}` | Subscription confirmation | "You're receiving this because..." |

Insert tokens by clicking the `{{ }}` icon in the editor toolbar.

### Smart Content

Show different content to different contacts based on rules:

**Available conditions**:
- **Contact list membership**: Show content A to list "VIP Customers", content B to everyone else
- **Lifecycle stage**: Show different CTAs to Leads vs Customers
- **Device type**: Mobile-optimized vs desktop content
- **Language**: Show translated content blocks based on contact's language property
- **Contact properties**: Any property value (e.g., industry, job role)
- **Personalization tokens within smart content**: Combine both approaches

**Setting up smart content**:
1. Add a module to your email
2. Click the module → **Smart Content** tab
3. Enable "Make this module smart"
4. Choose condition type (e.g., "Contact list membership")
5. Create default content (seen by non-matching contacts)
6. Add variation: Choose a specific list, set the content for that audience
7. Add more variations as needed
8. Preview each variation to verify

**Example**: A fitness company sends the same newsletter to all subscribers, but uses smart content to show:
- Runners: "New running shoes!" image and CTA
- Yoga practitioners: "Yoga mats on sale!" image and CTA
- Everyone else: "Browse our collection" generic CTA

### A/B Testing

Test up to 5 variations to find the winner:

**What you can test**:
- **Subject line**: Test different subject lines (most common)
- **Content**: Test different body copy, images, CTAs
- **Send time**: Test different send days/times
- **From name**: Test sender name variations

**Setting up an A/B test**:
1. In email editor, click "Enable A/B test" in settings
2. Choose what to test: Subject line, Content, Send time, From name
3. Create variants:
   - **A**: Control (your original)
   - **B, C, D, E**: Variations
4. Set sample size: What percentage of the list gets the test? (Recommended: 20-50%)
5. Winner determination:
   - **Manual**: You pick the winner after reviewing results
   - **Automatic**: HubSpot picks the winner based on open rate, click rate, or reply rate
6. Winning criteria: Open rate (subject line tests) vs Click rate (content tests)
7. Minimum sample: HubSpot needs enough data to determine a statistically significant winner
8. Winner sends to remaining list automatically

### Send Time Optimization

Send emails when each recipient is most likely to open:

1. In email send settings, enable "Send time optimization"
2. HubSpot analyzes each contact's past open behavior
3. The send window opens at your set time
4. Over the next 24 hours, each contact receives the email at their optimal time
5. Works best with lists of 1,000+ contacts for sufficient data

**Pro tip**: Send time optimization works better for broadcast marketing emails than time-sensitive content (event reminders, flash sales).

### Transactional Emails

Transactional emails are not marketing emails — they're operational:

**Use cases**:
- Order confirmations
- Password resets
- Account verification
- Payment receipts
- Shipping notifications

**Differences from marketing emails**:
- Not subject to marketing send limits
- Bypass unsubscribe (though you should still provide preference center links)
- Do not count against marketing contact metrics
- Use separate templates with different design considerations

**Setting up transactional emails**:
1. **Settings** > **Marketing** > **Email** > **Transactional email**
2. Create a transactional email template
3. Use personalization tokens for order details
4. Trigger via workflow, API, or connected app (Shopify, Stripe, etc.)

### Subscription Management

Manage how contacts receive your emails:

**Subscription types**:
- **Bulk/Newsletter**: Marketing emails (default)
- **One-to-one**: Sales sequences
- **Transactional**: Operational emails (auto-approved)

**Preference center**:
- HubSpot-hosted page where contacts manage their subscriptions
- URL format: `https://[portal].hubspotpreferences-ns.com/page/[id]`
- Include in email footer via the subscription management module
- Shows contact's current subscriptions, allows opt-in/opt-out

**Double opt-in** (optional):
1. Settings > Marketing > Email > Double opt-in
2. When enabled, contacts must click a confirmation link in an initial email
3. Only confirmed contacts are added as marketing contacts
4. Reduces spam signups, improves deliverability

### Email Analytics

After sending, analyze performance:

**Key metrics**:
- **Delivered**: Successfully reached inbox
- **Opens**: Unique and total open count, open rate
- **Clicks**: Unique and total click count, click rate (CTR)
- **Click-to-open rate**: Clicks/Opens (CTOR)
- **Bounces**: Soft (temporary) vs Hard (permanent) bounces
- **Unsubscribes**: By type, by campaign
- **Spam complaints**: Complaints as % of delivered
- **Forwarded**: Recipients who forwarded the email
- **Device breakdown**: Opens and clicks by device type
- **Click map**: Visual heatmap of where contacts clicked in the email
- **Location breakdown**: Opens by country, city
- **Browser/email client**: Which email clients were used to open

**Per-contact analytics**: Open the contact record → See their email engagement on the timeline. Shows which emails they opened, clicked, and when.

---

## Forms — Complete Guide

### Form Types

HubSpot offers 5 form types. Each serves a different purpose:

**1. Embedded Form**:
- Placed directly on your website pages via iframe or HubSpot tracking code
- Stays within the page flow
- Best for: Long forms, multi-field forms, inline sign-ups
- Pro: Fully customizable, all field types available
- Con: Requires the visitor to be on the page

**2. Pop-Up Form**:
- Overlays the page in a modal window
- Best for: Lead capture from exit intent, timed triggers
- Triggers: Time on page, scroll percentage, exit intent, page specific, CTA click

**3. Slide-In Form**:
- Slides in from the bottom or side of the screen
- Less intrusive than pop-ups, more visible than embedded
- Best for: Gentle lead capture, blog sidebar offers
- Triggers: Same as pop-ups

**4. Inline Form**:
- Appears inline within a blog post or page content
- Best for: Contextual CTAs within content (e.g., "Subscribe to this blog" mid-article)
- Uses HubSpot's tracking code for placement

**5. Floating Footer Form**:
- Stays fixed at the bottom of the screen
- Best for: Persistent lead capture on long pages, newsletters
- Minimally intrusive, always visible

### Creating a Form — Step-by-Step

1. **Marketing** > **Forms** > Create form
2. Choose form type: Embedded, Pop-up, Slide-in, Inline, Floating footer
3. **Form name**: Internal name for your reference
4. **Form options**:
   - **Style**: Customize colors, fonts, layout (single column, multi-column)
   - **Theme**: Use brand colors, custom CSS
   - **Position**: For pop-ups and slide-ins — top, center, bottom; left, right
5. **Add fields**:
   - Drag fields from the left panel into the form
   - Available field types: Single-line text, Multi-line text, Number, Date, Dropdown, Multiple checkboxes, Radio select, File upload, Phone, Email, Domain, GDPR consent
   - Mark required fields
   - Set placeholder text
6. **Progressive profiling** (Pro+):
   - Enable in the field settings
   - Returning visitors see different fields than new visitors
   - Configure how many new fields to show per submission
   - Identity fields (usually email) identify returning visitors
7. **Smart fields**: If a field's value is already known (e.g., first name from a previous form), auto-hide it
8. **Behavior settings**:
   - **Thank-you message**: Inline or redirect to a landing page
   - **Follow-up email**: Send an automated email after submission
   - **Workflow enrollment**: Enroll in a workflow automatically
9. **Lead assignment**: Assign the new lead to a specific user, owner, or team
10. **Captcha**: Google reCAPTCHA v2 (checkbox) or v3 (invisible)
11. **GDPR consent**: Add consent checkboxes with custom text
12. Click "Publish" → Get embed code or set trigger rules

### Progressive Profiling Deep Dive

Progressive profiling shows new fields over time so you never overwhelm visitors:

**How it works**:
1. First visit: First name, Last name, Email (3 fields)
2. Second visit: Phone number (1 new field)
3. Third visit: Company name, Job title (2 new fields)
4. By the 5th visit, you've collected 10 fields from 5 form submissions

**Setup**:
1. Add ALL the fields you want to eventually collect to the form
2. For each field after the identity fields, check "Use progressive profiling"
3. Set "Fields to show per submission": Default is 1 (show one new field each time)
4. Prioritize fields by dragging them — more important fields appear sooner
5. Identity field (email) is always shown and is not progressive

**Best practices**:
- Collect 3-4 fields on first submission
- Show 1-2 new fields on subsequent submissions
- Prioritize fields: start with essential info, get deeper data later
- Don't make all fields visible at once (defeats the purpose)

### Form Field Types Explained

| Field Type | When to Use |
|------------|------------|
| Single-line text | Short answers, any data up to 255 chars |
| Multi-line text | Longer answers, comments, messages |
| Number | Quantities, scores, ages |
| Date | Birthdays, preferred dates |
| Dropdown | Single choice from long list (industry, country) |
| Radio select | Single choice from short list (yes/no/maybe) |
| Checkboxes | Multiple selections (interests, preferences) |
| File upload | Submit documents, images, resumes |
| Phone | Contact number (with formatting) |
| Email | Primary identifier (with validation) |
| Domain | Website URL |
| GDPR consent | Legal consent checkboxes |

---

## Landing Pages — Complete Guide

Landing pages are standalone web pages designed for a specific marketing goal (form fill, ebook download, webinar registration, trial signup).

### Creating a Landing Page — Step-by-Step

1. **Marketing** > **Landing Pages** > Create landing page
2. Choose template:
   - **Blank**: Start from scratch
   - **HubSpot templates**: Dozens of pre-built, responsive templates
   - **Your templates**: Previously saved custom templates
   - **From URL**: Clone from an existing page
3. **Template categories**:
   - Ebook download
   - Webinar registration
   - Free consultation
   - Demo request
   - Newsletter signup
   - Multi-step (wizard-style)
4. **Editor**:
   - **Left panel**: Drag-and-drop modules (text, image, form, CTA button, video, testimonial, logo cloud, pricing table, divider, spacer, rich text)
   - **Center**: WYSIWYG preview (Desktop/Mobile toggle)
   - **Right panel**: Selected module settings

5. **Settings panel** (gear icon):
   - **Page title**: Browser tab title
   - **Page URL**: e.g., `/free-ebook-download`
   - **Meta description**: For search results
   - **Featured image**: Social sharing preview
   - **Custom domain**: `resources.yourcompany.com/ebook`
   - **Language**: For multi-language pages
   - **Password**: Protect the page (membership/gating)
   - **A/B test**: Enable to test variants
   - **Smart content**: Personalize per visitor

6. **SEO settings**:
   - Page title tag
   - Meta description
   - URL slug
   - Canonical URL (if syndicated elsewhere)
   - NOINDEX option (for landing pages you don't want in search)

7. **Publish**: Click "Publish" to make live

### Smart Content on Landing Pages

Same concept as email smart content, but for web pages:

**Available conditions**:
- **Contact list membership**: Show different CTAs to different segments
- **Lifecycle stage**: Adapt messaging for leads vs customers
- **Device type**: Mobile vs desktop layout variations
- **Language**: Show content in visitor's language
- **Referral source**: Customize for organic vs paid vs social traffic
- **Contact properties**: Any CRM field

**Example**: A SaaS company's homepage shows:
- First-time visitors: "Start your free trial"
- Existing leads: "Schedule a demo" (with personalized text)
- Current customers: "Upgrade your plan" or "Access knowledge base"

### Domain Setup for Landing Pages

1. **Settings** > **Marketing** > **Domains & URLs** > **Connected domains**
2. Click "Connect a domain"
3. Enter your subdomain (e.g., `resources.yourcompany.com` or `go.yourcompany.com`)
4. HubSpot provides CNAME and TXT records
5. Add these to your DNS provider (GoDaddy, Cloudflare, AWS Route53, etc.)
6. SSL certificate is auto-provisioned
7. Verification takes 5-30 minutes (DNS propagation)
8. Once verified, you can select this domain for landing pages

**Domain recommendations**:
- Use `go.yourcompany.com` for campaign landing pages
- Use `resources.yourcompany.com` for content offers
- DON'T use your primary domain for landing pages if you're sending high-volume marketing traffic

---

## SEO & Blogging — Complete Guide

### Blog Editor

1. **Marketing** > **Blog** > Create blog post
2. **Rich text editor** with drag-and-drop modules:
   - Text blocks
   - Images (upload, from URL, or AI-generated)
   - CTAs and buttons
   - Video embeds (YouTube, Wistia, HubSpot Video)
   - Tables
   - Code blocks
   - Social sharing buttons
   - Blog subscription form
   - Topic/tag links
3. **Sidebar settings**:
   - **Post body**: Main content
   - **Excerpt**: Blog listing summary (for RSS and tags)
   - **Featured image**: Shown on blog listing
   - **Author**: From your blog team
   - **Topics/Tags**: For filtering and SEO clustering
   - **Publish date**: Schedule for future
   - **Password**: Member-only content

### Topic Clusters

HubSpot's content strategy is built around **topic clusters** — a modern SEO approach:

**Structure**:
```
Pillar Page (Broad Topic)
├── Cluster Content 1 (Specific subtopic)
├── Cluster Content 2 (Specific subtopic)
├── Cluster Content 3 (Specific subtopic)
└── Each cluster page links BACK to the pillar page
```

**Why it works**:
- Google sees the pillar page as authoritative on the broad topic
- Internal linking structure boosts SEO for all pages in the cluster
- Content is organized, not scattered

**Setting up topic clusters**:
1. **Marketing** > **Content Strategy** > **Strategy tool**
2. **Add a topic**: Enter a broad topic (e.g., "Email Marketing")
3. HubSpot suggests related subtopics:
   - "Email deliverability best practices"
   - "How to write email subject lines"
   - "Email automation workflows"
   - "A/B testing for emails"
4. For each subtopic, HubSpot provides:
   - Monthly search volume
   - Keyword difficulty
   - Current ranking (if any)
5. Create content for each subtopic
6. Link from each cluster page back to the pillar page
7. HubSpot's tool tracks internal links and cluster completeness

### SEO Recommendations

When editing a blog post or page, HubSpot provides real-time SEO analysis:

**Page-level analysis**:
- **Title tag**: Is it the right length (50-60 characters)? Does it include the target keyword?
- **Meta description**: Is it compelling and the right length (150-160 characters)?
- **URL slug**: Is it clean and keyword-rich?
- **Headings**: Is H1 used? Are H2/H3s structured?
- **Image alt text**: Are images described for accessibility and SEO?
- **Keyword usage**: Is the target keyword used appropriately (not stuffed)
- **Readability score**: Flesch reading ease, grade level
- **Internal linking**: Are there enough internal links? Links to the pillar page?
- **External links**: Are citations authoritative?
- **Content length**: Is the post long enough to be comprehensive?

### Content Strategy Tool

1. **Marketing** > **Content Strategy**
2. **Topics tab**: Add your core topics
3. **Competitors tab**: Add competitors' domains — see which topics they rank for
4. **Content gaps**: HubSpot shows topics your competitors rank for but you don't
5. **Opportunity score**: Prioritizes topics by search volume + ranking difficulty
6. **Track keywords**: Monitor your rankings over time (Pro+)

### Blog Settings

1. **Settings** > **Marketing** > **Blog**:
   - **Blog homepage**: URL structure (`/blog`, `/resources`, `/insights`)
   - **Post URL structure**: `/blog/post-title` or `/blog/category/post-title`
   - **RSS feed**: Enable, customize
   - **Comments**: Enable/disable, moderate
   - **Author pages**: Display author bios
   - **Social sharing**: Auto-format posts for social platforms
   - **Subscription**: Blog subscription module, frequency
   - **Content calendar**: Visual calendar view of published and scheduled posts

---

## Social Media — Complete Guide

### Publishing

1. **Marketing** > **Social** > **Create post**
2. **Single post**:
   - Choose network: Facebook, LinkedIn, Twitter/X, Instagram
   - Write content — different lengths for each network
   - Add image, link, or video
   - Set publish time: Now or schedule
3. **Bulk scheduling**:
   - Upload CSV of posts with content, dates, networks
   - Useful for monthly content planning

**Approval workflows** (Pro+):
1. Settings > Marketing > Social > Approval workflows
2. Require approval before posts go live
3. Draft → Submit for review → Approve/Reject → Schedule/Publish

### Social Analytics

**Per-network analytics**:
- Impressions
- Clicks
- Engagement rate
- Follower growth over time
- Best posting times
- Top-performing content

**Social listening** (Enterprise):
- Monitor brand mentions across social platforms
- Track competitor mentions
- Identify trending topics in your industry
- Sentiment analysis on mentions

### Connected Networks Setup

1. **Settings** > **Marketing** > **Social** > **Connect new account**
2. Authenticate with each network:
   - Facebook: Page access required
   - LinkedIn: Company page or personal profile
   - Twitter/X: Profile access
   - Instagram: Professional account connected to Facebook
3. Limits: Free (5 accounts), Starter (10), Pro (unlimited)

---

## Ads — Complete Guide

HubSpot Ads lets you track ad performance and sync lead data from ad platforms.

### Connected Ad Networks

| Network | What Syncs |
|---------|-----------|
| Google Ads | Clicks, impressions, cost, conversions, keywords |
| Facebook Ads | Clicks, impressions, cost, conversions, lead ads |
| LinkedIn Ads | Clicks, impressions, cost, conversions, lead gen forms |
| Instagram | Via Facebook Ads connection |

### Setting Up Ad Tracking

1. **Marketing** > **Ads** > Connect accounts
2. Authenticate your ad platform (Google, Facebook, LinkedIn)
3. **Auto-tagging**: Enable to track UTM parameters
4. **Conversion tracking**: HubSpot tracking code on your thank-you pages
5. **Revenue attribution**: Connect ad clicks to closed deals

### Retargeting Audiences

Create retargeting audiences from HubSpot contact lists:

1. **Marketing** > **Ads** > **Create audience**
2. Choose ad platform: Google, Facebook, LinkedIn
3. Select a HubSpot list as the audience source
4. Set parameters:
   - **Include**: Contacts from the list (e.g., "Visited pricing page but didn't convert")
   - **Exclude**: Contacts from another list (e.g., "Already customers")
5. HubSpot syncs the audience to the ad platform
6. Create your ad campaign targeting that audience in the platform

### Lead Ad Sync

Facebook/Instagram/LinkedIn lead ads automatically create HubSpot contacts:

1. Connect your Facebook/LinkedIn Ads account
2. Enable lead ad sync
3. When someone submits a lead ad, HubSpot creates a contact with the form data
4. The contact's source is "Facebook Lead Ad" or "LinkedIn Lead Ad"
5. Automatically enroll in workflows for immediate follow-up

---

## Campaigns — Complete Guide

Campaigns group related marketing assets to track combined performance.

### Creating a Campaign

1. **Marketing** > **Campaigns** > Create campaign
2. Fill in:
   - **Name**: "Q3 Ebook Launch"
   - **Goal**: Leads, Revenue, Brand awareness, Engagement
   - **Budget**: Marketing spend for this campaign
   - **Start/End dates**: Campaign duration
   - **Associated assets**: Emails, landing pages, forms, ads, social posts, CTAs, workflows, lists

### Adding Assets to Campaign

**From campaign**:
1. Open campaign
2. Click "Add asset"
3. Search for existing email, landing page, form, ad, social post, CTA, workflow, or list
4. Add it to the campaign

**From asset creation**: When creating a new email, landing page, or form, set the "Campaign" field to associate it automatically.

### Multi-Touch Attribution

HubSpot supports 6 attribution models:

| Model | How It Works | Best For |
|-------|-------------|----------|
| **First interaction** | First touchpoint gets 100% credit | Brand awareness campaigns |
| **Last interaction** | Last touchpoint gets 100% credit | Bottom-of-funnel campaigns |
| **Linear** | Equal credit to all touchpoints | Multi-channel campaigns |
| **U-shaped** | 40% first, 40% last, 20% middle | Balanced view |
| **W-shaped** | 30% first, 30% deal creation, 30% close, 10% middle | Complex B2B sales |
| **Time decay** | More credit to recent interactions | Long sales cycles |

**Setting attribution**:
1. **Settings** > **Tracking & Analytics** > **Attribution**
2. Select default attribution model
3. Customize attribution windows:
   - Lookback window: How far back to consider touchpoints (default: 90 days)
   - Close window: How long after close to include touchpoints (default: 0 days)

---

## Marketing Automation (Workflows) — Complete Guide

### Workflow Types

**Contact-based**: Most common. Triggered by contact properties, form submissions, page views, list membership, email engagement, dates. Actions affect the contact.

**Company-based**: Triggered by company property changes. Actions affect the company record. Less common.

**Deal-based**: Triggered by deal stage changes, property values. Actions affect deals. Used for sales handoffs.

**Ticket-based**: Triggered by ticket creation, status changes. Used for service automation.

**Custom object-based**: Triggered by custom object events.

### Enrollment Triggers in Detail

**Property-based**:
- When property value is: `Lifecycle stage` → `becomes` → `MQL`
- When property value changes: Any property → `has changed`
- Schedule-based: `Property value` → `(date property)` → `is in the past`

**Activity-based**:
- Form submission: `Has submitted a form` → specific form or any form
- Email engagement: `Has opened a marketing email` → specific email or any
- Page visit: `Has visited a page` → URL contains `/pricing`
- Meeting booked: `Meeting booked` by contact
- Call logged: `Call logged` with outcome

**List-based**:
- List membership: `Added to list` → specific list

**Combined triggers**:
Use AND/OR logic for multiple conditions. Example: "When contact's lifecycle becomes MQL AND has submitted the demo form" is narrower than "When lifecycle becomes MQL OR has submitted the demo form."

### Workflow Actions — Complete List

| Action Category | Specific Actions |
|----------------|-----------------|
| **Email** | Send marketing email, send transactional email, send automated email |
| **CRM** | Create record (contact, deal, ticket, custom object), delete record, associate records, disassociate records |
| **Property** | Set property value, clear property value, copy property value |
| **List** | Add to static list, remove from static list |
| **Communication** | Create task, enroll in sequence (Sales Hub), log a call, log an email |
| **Goal** | Set goal (wait until condition met), expire goal after |
| **Delay** | Wait for duration, wait until date, wait for specific day/time |
| **Branch** | If/then branch based on property value, list membership, has associated deal, etc. |
| **Internal** | Trigger webhook, rotate lead to user/team, create deal, create ticket |
| **Actions from connected apps** | Salesforce, Slack, Jira, etc. (via integrations) |

### Goal-Based Workflows

A workflow that enrolls contacts and keeps them in until a goal is met:

**Example**: "Nurture until demo booked"
1. Enrollment: New MQL created
2. Actions: Send nurture email series
3. Goal: Meeting booked with sales team
4. Expiration: 30 days without meeting → notify manager
5. If goal met → exit workflow, enroll in "thank you" workflow
6. If expired → move to "re-engagement" workflow

### Workflow Example: Complete Lead Nurture

**Trigger**: Form submission (download "Ultimate Guide")

**Branch 1**: If lifecycle stage is "Lead" → continue. Otherwise, skip.

**Action Sequence**:
1. Set property: Lead Source = "Ebook Download: Ultimate Guide"
2. Add to list: "Ebook Downloaders"
3. Send email: "Download link + recommended next resource" (immediate)
4. Delay: 2 days
5. Send email: "Related content based on download" (nurture)
6. Delay: 3 days
7. Branch: If lead score > 50 AND lifecycle = "MQL"
   - Yes: Create task "Hot lead — call within 24 hours" assigned to owner
   - No: Continue nurture
8. Set property: Marketing status = "Being nurtured"
9. Goal: Contact becomes "Opportunity"
10. If goal met → Exit, add to "Closed-loop" workflow
11. If 30 days expire → Send re-engagement email, create task "Re-engage cold lead"

---

## Lead Scoring — Complete Guide

### How Lead Scoring Works

Lead scoring assigns points to contacts based on their profile and behavior.

**Score types**:
1. **Positive attributes**: Add points for desirable characteristics
2. **Negative attributes**: Subtract points for undesirable characteristics
3. **Fit scoring**: Demographic match to your ideal customer profile
4. **Behavior scoring**: Engagement level with your brand

### Setting Up Lead Scoring

1. **Marketing** > **Lead Scoring** > Create scoring model
2. **Name**: "B2B SaaS Standard" or similar

**Positive attributes** (% of max points):

**Demographic fit** (up to 50 points total):
| Criteria | Points | Reasoning |
|----------|--------|-----------|
| Job title contains "VP", "Director", "Manager" | +10 | Decision-making role |
| Industry is "Technology" | +10 | Our ICP |
| Company size > 200 employees | +10 | Enterprise target |
| Revenue > $50M | +10 | Budget availability |
| Country is US, UK, Canada, Australia | +10 | Our serviceable markets |

**Behavioral fit** (up to 50 points total):
| Criteria | Points | Reasoning |
|----------|--------|-----------|
| Visited pricing page | +15 | High purchase intent |
| Downloaded 3+ resources | +10 | Engaged with content |
| Opened 3+ marketing emails | +10 | Active engagement |
| Attended webinar | +15 | In-depth interest |
| Clicked CTA in email | +10 | Action-oriented |

**Negative attributes** (up to -50 points total):
| Criteria | Points | Reasoning |
|----------|--------|-----------|
| Job title contains "Student" | -20 | Not in our ICP |
| Unsubscribed from marketing | -50 | No marketing permission |
| Company is non-profit | -10 | Typically no budget |
| No activity in 90 days | -20 | Cold lead |

**Score ranges and lifecycle mapping**:
| Score Range | Lifecycle Stage | Action |
|-------------|----------------|--------|
| 0-19 | Lead | Continue nurture |
| 20-49 | MQL | Assign to SDR |
| 50-79 | SQL | Assign to AE for demo |
| 80-100 | Opportunity | Prioritize for close |

3. Click "Save and turn on"

### Predictive Lead Scoring (Pro+/Enterprise)

ML-based scoring that learns from your historical data:

1. **Marketing** > **Lead Scoring** > **Predictive scoring** tab
2. HubSpot analyzes your past won/lost deals
3. Model identifies patterns: which properties and behaviors correlate with conversion
4. Model outputs a "conversion probability" score (0-100%)
5. Updates as new data comes in
6. More accurate over time as the model trains on more data

---

## Analytics & Reporting — Complete Guide

### Traffic Analytics

1. **Reports** > **Analytics** > **Traffic**
2. **Sources breakdown**:
   - **Organic**: Search engine traffic
   - **Paid**: Ad traffic (Google Ads, Facebook, LinkedIn)
   - **Social**: Social media traffic
   - **Email**: Email campaign traffic
   - **Referral**: Other websites linking to you
   - **Direct**: Typed URL or bookmarked
   - **Other campaigns**: UTM-tagged custom sources
3. **Pages**: Top pages by visits, time on page, bounce rate
4. **Devices**: Desktop vs mobile vs tablet
5. **Locations**: Top countries, cities
6. **New vs returning**: First-time vs repeat visitors

### Contact Analytics

1. **Reports** > **Analytics** > **Contacts**
2. **Contacts created**: Over time, by source
3. **Lifecycle progression**: Subscriber → Lead → MQL → SQL → Opportunity → Customer
4. **Conversion rates**: Visitor → Contact → Lead → Customer
5. **Source performance**: Which channels create the most contacts? Most customers?

### ROI Reporting

1. **Reports** > **Dashboards** → **Marketing ROI**
2. Shows:
   - Revenue attributed to marketing
   - Cost per lead (CPL)
   - Customer acquisition cost (CAC)
   - Marketing-attributed revenue
   - ROI per campaign
   - ROI per channel
3. **Setup**: Go to settings and enter campaign costs (ad spend, content production, tools) for accurate ROI

### Custom Dashboards

1. **Reports** > **Dashboards** > Create dashboard
2. Name: "Weekly Marketing Review"
3. Add reports:
   - New contacts this week (single number)
   - Traffic by source (pie chart)
   - Email performance (table)
   - Pipeline from marketing sources (bar chart)
   - Campaign ROI (single number)
   - Blog top posts (table)
   - Social followers (line chart)
4. Schedule email: Send snapshot every Monday
5. Share with team: Set viewing permissions

---

## Limits That Matter

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Marketing contacts | 0 | 1,000 | 2,000 base | 10,000 base |
| Monthly email sends | 2,000 | 10× contacts | 10× contacts | 12× contacts |
| Email send per day | 5× contacts | 5× contacts | 5× contacts | Unlimited |
| Forms | 1,000 | 5,000 | 50,000 | Unlimited |
| Form fields per form | 100 | 100 | 100 | 100 |
| Landing pages | 20 | 70 | Unlimited | Unlimited |
| Blog posts | 250 | 2,500 | Unlimited | Unlimited |
| Social accounts | 5 | 10 | Unlimited | Unlimited |
| Workflows (active) | 5 | 20 | 500 | 1,000+ |
| A/B test variants | — | — | 5 | 5 |
| Lead scoring | — | — | 3 models | Unlimited |
| Campaigns | 5 | 20 | Unlimited | Unlimited |
| Custom attribution models | — | — | 1 | 3 |

### Marketing Contacts vs Non-Marketing Contacts

This is the most important distinction in Marketing Hub pricing:

- **Marketing contacts**: Contacts you send marketing emails to. You're billed per marketing contact.
- **Non-marketing contacts**: Everyone else. Unlimited at no extra cost.

**Setting a contact as non-marketing**:
1. Open contact record
2. Under "Marketing contact status": Toggle OFF
3. They still appear in CRM, support teams can work with them
4. They don't receive marketing emails but still get transactional emails
5. Workflows targeting them can still run (just no marketing emails)

**Strategy**: Set contacts who don't need nurturing (existing customers, support-only contacts) to non-marketing.

---

## Common Gotchas

### 1. Marketing Contacts Count
If you go over your marketing contact limit, you'll get an overage warning. You're not charged immediately, but you must reduce contacts or upgrade before the next billing period.

### 2. Email Deliverability
HubSpot manages sending reputation, but you must warm up new domains. Start with small lists and increase gradually. Bounce rate > 5% can damage your sending reputation.

### 3. Progressive Profiling Limitations
Progressive profiling requires your contact to have a cookie from HubSpot tracking code. If they clear cookies or use a different device, they may see all fields again.

### 4. Workflow Retroactive Enrollment
Workflows only enroll contacts who meet criteria AFTER the workflow is turned on. They don't retroactively enroll existing contacts. To enroll existing contacts, use manual enrollment or re-enrollment settings.

### 5. Workflow Actions Are Not Undone
If a workflow sends an email, you can't "unsend" it. If a workflow moves a contact to "Customer" lifecycle stage, reversing it requires a separate workflow.

### 6. A/B Testing Sample Size
If your list is too small (<500 contacts), A/B tests won't have enough data for significant results. HubSpot warns you but still sends.

### 7. Blog URL Changes
Once published, changing a blog post URL requires a redirect. HubSpot auto-redirects old URLs, but it's best practice to decide URLs before publishing.

### 8. Form Embedding Without Tracking Code
Embedded forms (iframe method) work without HubSpot tracking code on the page, but you lose page view tracking. Forms placed via HubSpot tracking code module work fully.

### 9. Social Post Scheduling
Social posts scheduled in HubSpot might have slight UI differences vs native posting. LinkedIn carousels and Instagram Stories have limited support.

### 10. Ad Tracking Accuracy
UTM parameters are the most reliable tracking method. Auto-tagging from ad platforms works but can miss some interactions. Combine UTM + HubSpot tracking for best results.

---

## Marketing Hub Tutorials

### Tutorial 1: Building a Complete Email Campaign

**Goal**: Plan, create, launch, and analyze a marketing email campaign from start to finish.

**Step 1: Define Campaign Goals**
1. Navigate to **Marketing** > **Campaigns** > Create campaign
2. Name: "Q3 Product Launch — Email Series"
3. Goal: Generate 100 demo requests from existing leads
4. Budget: $2,000 (content creation, no paid ads)
5. Timeline: 4 weeks (1 email per week)
6. Target audience: Existing leads who haven't requested a demo yet

**Step 2: Create Your Audience List**
1. **Contacts** > **Lists** > Create active list
2. Name: "Q3 Launch — Target Audience"
3. Criteria:
   - Lifecycle stage is "Lead" OR "MQL"
   - Has not submitted "Demo Request" form
   - Email subscription status is "Subscribed"
   - Created in last 90 days
4. Save — list auto-populates with matching contacts

**Step 3: Design Email Series (4 emails)**

**Email 1 — Teaser (Day 0)**
- Subject: "Something big is coming, {{ contact.firstname }}"
- Preview text: "You won't want to miss this announcement"
- Body: Build anticipation, hint at new features, include countdown
- CTA: "Get notified" (link to interest page)
- Personalization: `{{ contact.firstname }}`, `{{ contact.company }}`

**Email 2 — Launch (Day 7)**
- Subject: "Introducing [Product Name] — available now"
- Preview text: "See what's new and how it helps your team"
- Body: Feature highlights, benefits, customer quote
- CTA: "See it in action" (link to demo request form)
- Smart content: Show different features based on contact's industry

**Email 3 — Social Proof (Day 14)**
- Subject: "How [Customer Name] achieved 3× results with [Product Name]"
- Preview text: "Real results from real customers"
- Body: Case study summary, key metrics, testimonial
- CTA: "Read full case study" + "Request demo"
- Personalization: Include company name in case study context

**Email 4 — Final Push + Offer (Day 21)**
- Subject: "Last chance: Your exclusive early adopter offer"
- Preview text: "20% off for the first 50 customers"
- Body: Recap of features, urgency ("limited time"), offer details
- CTA: "Claim your discount" (link to payment/checkout)
- A/B test: Test subject line A ("Last chance...") vs B ("Exclusive offer ends soon")

**Step 4: Set Up Email Automation in Editor**
1. **Marketing** > **Email** > Create automated email
2. Choose: Automated email (trigger-based, not broadcast)
3. Enable A/B testing on Email 4:
   - Variant A: "Last chance: Your exclusive early adopter offer"
   - Variant B: "Exclusive offer ends soon: 20% off [Product Name]"
   - Test size: 30% of list
   - Winner based on: Click rate
4. Set send time optimization: Enable (send when each contact is most likely to open)

**Step 5: Create Campaign Workflow**
1. **Automation** > **Workflows** > Create workflow
2. Trigger: Contact added to "Q3 Launch — Target Audience" list
3. Sequence:
   - Day 0: Send Email 1 (teaser)
   - Delay: 7 days
   - Branch: If form submitted "Demo Request" → exit workflow (goal met)
   - Day 7: Send Email 2 (launch)
   - Delay: 7 days
   - Branch: If demo requested → exit
   - Day 14: Send Email 3 (case study)
   - Delay: 7 days
   - Day 21: Send Email 4 (offer) — with A/B test
   - After 14 more days: If no demo request → add to "Long-term nurture" list
4. Goals: Contact submits "Demo Request" form → exit workflow
5. Turn on workflow

**Step 6: Launch and Monitor**
1. Review all 4 emails for rendering on desktop and mobile
2. Send test emails to yourself
3. Check all links work correctly
4. Review campaign analytics daily for the first week:
   - Open rates (target: 25%+)
   - Click rates (target: 3%+)
   - Unsubscribe rate (alert if > 0.5%)
   - Bounce rate (alert if > 3%)
5. A/B test winner declared after 24 hours → winning variant sent to remaining list

**Step 7: Post-Campaign Analysis**
1. **Marketing** > **Campaigns** > Open "Q3 Product Launch"
2. Review KPIs:
   - Total emails sent, delivered, opened, clicked
   - Unsubscribes and bounces
   - Conversions: How many demo requests from the campaign?
   - Revenue: How many deals created from campaign leads?
   - ROI: Revenue attributed ÷ campaign cost
3. Create a campaign report: Save as dashboard

### Tutorial 2: Building a Multi-Channel Lead Generation System

**Goal**: Create an automated system that captures leads from multiple channels and funnels them into a unified nurture workflow.

**Step 1: Create Lead Capture Forms**

**Form 1: Newsletter Signup (Blog)**
- Type: Slide-in form (less intrusive on blog pages)
- Fields: Email (required), First Name (required)
- Trigger: Show after 10 seconds on blog
- Follow-up: Send welcome email with latest content

**Form 2: Ebook Download (Landing Page)**
- Type: Embedded form on dedicated landing page
- Fields: Email, First Name, Last Name, Company, Job Title, Phone
- Progressive profiling: Return visitors only see 2 new fields
- Follow-up: Send download link, enroll in nurture sequence

**Form 3: Demo Request (Website)**
- Type: Pop-up form on pricing page
- Fields: Email, First Name, Company, Company Size, Phone
- Trigger: Show when visitor scrolls past pricing table
- Follow-up: Create high-priority task for SDR to call within 1 hour

**Form 4: Contact Us (Website)**
- Type: Embedded form on Contact page
- Fields: Email, First Name, Last Name, Company, Message (multi-line)
- Follow-up: Create ticket for general inquiry

**Step 2: Set Up Progressive Profiling**
1. **Marketing** > **Forms** > Edit "Ebook Download" form
2. Enable progressive profiling
3. First submission fields: Email, First Name (identity)
4. Second submission: Last Name, Company
5. Third submission: Job Title, Phone
6. Fourth submission: Company Size, Industry

**Step 3: Create Channel-Specific Workflows**

**Workflow: Blog Subscriber**
1. Trigger: Form submission (Newsletter Signup)
2. Actions:
   - Send welcome email with recent blog posts
   - Set lifecycle = "Subscriber"
   - Add to "Blog Subscribers" list
   - If email domain matches known company → associate to company

**Workflow: Content Downloader**
1. Trigger: Form submission (Ebook Download)
2. Actions:
   - Send download link email immediately
   - Set lifecycle = "Lead"
   - Set lead source = "Ebook: [Title]"
   - Add to "Content Engaged" list
   - Delay 3 days → Send follow-up email with related content
   - Delay 7 days → Enroll in "Demo Nurture" sequence

**Workflow: Demo Request (High Priority)**
1. Trigger: Form submission (Demo Request)
2. Actions:
   - Send confirmation email with meeting link
   - Set lifecycle = "MQL"
   - Set lead status = "Hot"
   - Create task for SDR: "Call {{ contact.firstname }} at {{ contact.company }} within 1 hour"
   - Send Slack notification to #new-leads
   - Enroll in "Demo Prep" sequence

**Step 4: Create Unified Nurture Sequence**
1. **Sales** > **Sequences** > Create sequence
2. Name: "Demo Nurture — 5 Step"
3. Steps:
   - Day 0: Email — "Thanks for your interest. Here's how [Product] works"
   - Day 3: Email — Case study relevant to their industry
   - Day 6: Email — "FAQ: What customers ask before booking a demo"
   - Day 10: Email — Product comparison vs competitors
   - Day 14: Email — "Ready to see it in action?" with meeting link
4. Goal: Meeting booked
5. Unenrollment: Reply, meeting booked, demo requested

**Step 5: Measure Channel Effectiveness**
1. Create report: "Lead Generation by Channel"
   - Source: Original source drill-down (Organic, Paid, Referral, Social, Email, Direct)
   - Metric: Contacts created, MQLs, SQLs, Customers
   - View: Which channels generate the most volume vs highest quality
2. Create report: "Cost Per Lead by Channel"
   - If using paid ads: Import ad spend data
   - Calculate: Total spend ÷ contacts created per channel
   - View: Which channels are most cost-efficient

### Tutorial 3: Setting Up A/B Testing for Continuous Optimization

**Goal**: Systematically test and improve email and landing page performance through A/B testing.

**Step 1: Email Subject Line Testing**

Create a test plan:
| Test | Control | Variant | Goal |
|------|---------|---------|------|
| Subject line length | "New feature announcement" (29 chars) | "Introducing [Feature]: Save 10 hours/week" (49 chars) | Higher open rate |
| Personalization | "Hi there" | "Hi {{ contact.firstname }}" | Higher open rate |
| Urgency | No urgency | "Limited time: Offer ends Friday" | Higher click rate |
| CTA placement | CTA at bottom only | CTA at top + bottom | Higher click rate |
| Imagery | Stock photo | Screenshot of product | Higher click rate |

**Setting up the test**:
1. Create email → Enable A/B testing
2. Select "Subject line" as test variable
3. Variant A: "New feature announcement"
4. Variant B: "Introducing [Feature]: Save 10 hours/week"
5. Test size: 30% of list
6. Winner based on: Open rate
7. Winning variant sends to remaining 70%

**Step 2: Landing Page Testing**

| Test | Control | Variant | Goal |
|------|---------|---------|------|
| Headline | "Download our ebook" | "Learn how top companies increased revenue by 40%" | Higher conversion |
| Form length | 5 fields | 3 fields | Higher submission rate |
| CTA text | "Submit" | "Get my free copy" | Higher click rate |
| Layout | Text on left, form on right | Form on left, text on right | Higher conversion |
| Social proof | None | Customer logos + testimonial | Higher trust |

**Setting up the test**:
1. **Marketing** > **Landing Pages** > Open page → Create test
2. Select "Adaptive test" (multiple variants)
3. Create 3 variants: Control (current), Variant A (new headline), Variant B (new headline + social proof)
4. Traffic split: 33/33/34
5. Goal metric: Form submission rate
6. Minimum sample: 500 visitors before declaring winner
7. Launch — HubSpot auto-optimizes traffic to best performer

**Step 3: Analyze and Iterate**
1. Review test results after minimum sample is reached
2. Statistical significance: HubSpot shows confidence level (95%+ recommended)
3. Apply winner: Publish the winning variant as the new default
4. Create next test: Build on learnings (e.g., if shorter forms convert better, test even shorter)

### Tutorial 4: Building an Automated Webinar Funnel

**Goal**: Drive registrations, attendance, and post-webinar conversions using HubSpot automation.

**Step 1: Create Registration Page**
1. **Marketing** > **Landing Pages** > Create
2. Use "Webinar Registration" template
3. Content: Headline, date/time, speaker bio, agenda, key takeaways
4. Form: Email, First Name, Last Name, Company, Job Title
5. CTA: "Save my spot"
6. Thank-you page: Confirmation with calendar link, webinar link, "Add to calendar" button
7. Set up tracking: UTM parameters for promotion channels

**Step 2: Build Registration Workflow**
1. Trigger: Form submitted (Webinar Registration)
2. Actions:
   - Send confirmation email with webinar link and calendar attachment
   - Add to "Webinar Registrants" list
   - Set property "Webinar Registered" = true
   - Delay 1 day: Send pre-webinar reminder email
   - Delay 3 days (if webinar is 1 week away): Send reminder with speaker highlight
   - Delay 1 day before: Send "See you tomorrow!" email with technical requirements
   - Delay 1 hour before: Send final reminder with webinar link

**Step 3: Build Attendance Tracking**
1. Create custom property: "Webinar Attended" (boolean)
2. On the webinar landing page, add tracking code that fires on page load
3. Create workflow: Triggered when webinar page is loaded
   - Set "Webinar Attended" = true
   - Set lifecycle = "MQL" (if was "Lead")
   - Add to "Webinar Attendees" list

**Step 4: Build Post-Webinar Follow-up**
1. Trigger: "Webinar Attended" becomes true
2. Actions:
   - Send thank-you email with recording link and slides
   - Send follow-up survey (CES: "How was the webinar?")
   - Enroll in "Post-Webinar Nurture" sequence:
     - Day 0: Email with recording + related resources
     - Day 3: Email with case study related to webinar topic
     - Day 7: Email with demo offer (meeting link)
     - Day 14: Email with "Did you miss this?" (key takeaways)
   - If survey score is 4-5 → Add to "Hot Lead" list
   - If survey score is 1-2 → Create task for CS: "Follow up with dissatisfied attendee"

**Step 5: Measure Webinar ROI**
1. Create report: "Webinar Performance"
   - Registrations: Total signups
   - Attendance rate: Attendees ÷ Registrants (target: 40%+)
   - Lead conversion: MQLs from webinar
   - Revenue: Deals created from webinar-attributed contacts
   - Cost: Promotion spend + content creation
   - ROI: Revenue ÷ Cost

---

## Marketing Hub Metrics — What to Track

### Email Metrics
| Metric | Target | Red Flag |
|--------|--------|---------|
| Delivery rate | > 97% | < 95% (check list quality) |
| Open rate | > 25% | < 15% |
| Click rate (CTR) | > 3% | < 1% |
| Click-to-open rate (CTOR) | > 15% | < 10% |
| Unsubscribe rate | < 0.5% | > 1% |
| Bounce rate (hard) | < 1% | > 3% |
| Spam complaint rate | < 0.1% | > 0.1% (deliverability risk) |
| Reply rate | > 0.5% | < 0.1% (no engagement) |

### Landing Page Metrics
| Metric | Target | Red Flag |
|--------|--------|---------|
| Conversion rate | > 10% | < 3% |
| Bounce rate | < 60% | > 80% |
| Average time on page | > 60s | < 20s |
| Form abandonment | < 70% | > 85% |

### Blog & SEO Metrics
| Metric | Target |
|--------|--------|
| Monthly blog traffic growth | > 10% month-over-month |
| Average time on article | > 3 minutes |
| Pages per session | > 2 |
| Organic traffic % of total | > 40% |
| Keyword rankings in top 10 | Increasing |
| Content cluster completeness | 80%+ |

### Social Media Metrics
| Metric | Target |
|--------|--------|
| Engagement rate | > 2% |
| Click-through rate | > 0.5% |
| Follower growth | > 5% monthly |
| Posts per week | 3-5 minimum |

### Automation & Workflow Metrics
| Metric | Target | Red Flag |
|--------|--------|---------|
| Workflow enrollment rate | Meets expectations | < 50% of projected |
| Email open rate in workflow | > 30% | < 20% |
| Goal completion rate | > 10% | < 3% |
| Workflow to-list conversion | > 5% | < 1% |