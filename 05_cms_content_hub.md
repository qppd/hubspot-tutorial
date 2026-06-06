# 5. Content Hub (CMS) — Complete Tutorial

## Table of Contents
1. [Introduction to Content Hub](#introduction-to-content-hub)
2. [Website Builder — Complete Guide](#website-builder--complete-guide)
3. [HubL Templating Language](#hubL-templating-language)
4. [Custom Modules — Complete Guide](#custom-modules--complete-guide)
5. [Blogging — Complete Guide](#blogging--complete-guide)
6. [Content AI — Complete Guide](#content-ai--complete-guide)
7. [Local Development — Complete Guide](#local-development--complete-guide)
8. [Serverless Functions — Complete Guide](#serverless-functions--complete-guide)
9. [HubDB — Complete Guide](#hubdb--complete-guide)
10. [Multi-Language Content — Complete Guide](#multi-language-content--complete-guide)
11. [Membership & Gated Content — Complete Guide](#membership--gated-content--complete-guide)
12. [Adaptive Testing — Complete Guide](#adaptive-testing--complete-guide)
13. [Limits That Matter](#limits-that-matter)
14. [Common Gotchas](#common-gotchas)
15. [Use Cases](#use-cases)

---

## Introduction to Content Hub

Content Hub (formerly CMS Hub) is HubSpot's content management system. It powers websites, blogs, landing pages, and dynamic content — all integrated with your CRM data. Unlike standalone CMS platforms (WordPress, Contentful, Webflow), Content Hub has direct access to your contacts, companies, deals, and custom objects.

### What You Get by Tier

| Feature | Free | Starter | Pro | Enterprise |
|---------|------|---------|-----|------------|
| Website pages | 25 | 100 | Unlimited | Unlimited |
| Blog posts | 250 | 2,500 | Unlimited | Unlimited |
| Custom domains | 1 | 5 | 15 | Unlimited |
| SSL certificate | ✓ | ✓ | ✓ | ✓ |
| Content AI | Limited | Limited | ✓ | ✓ |
| Custom modules | ✗ | ✗ | ✓ | ✓ |
| HubL templating | ✓ | ✓ | ✓ | ✓ |
| HubDB | ✗ | ✗ | ✓ | ✓ |
| Serverless functions | ✗ | ✗ | 10 | 100 |
| Local dev (CLI) | ✓ | ✓ | ✓ | ✓ |
| Git integration | ✗ | ✗ | ✗ | ✓ |
| Multi-language | ✗ | ✗ | 5 languages | Unlimited |
| Membership/gating | ✓ | ✓ | ✓ | ✓ |
| Adaptive testing | ✗ | ✗ | 10 tests | Unlimited |
| CDN | ✓ | ✓ | ✓ | ✓ |

### Navigation

- **Marketing** > **Website** — Pages editor, themes, menus
- **Marketing** > **Blog** — Blog posts, content calendar
- **Design Tools** (Settings > Tools > Design Tools) — HubL, CSS, JS, modules
- **Settings** > **Content** — Domains, membership, SEO defaults

---

## Website Builder — Complete Guide

### Themes

Themes are the foundation of your Content Hub website.

**Marketplace themes**:
1. **Marketing** > **Website** > **Themes**
2. Browse the theme marketplace (free and paid themes)
3. Preview themes on sample content
4. Install with one click
5. Themes include: homepage, about page, contact page, blog templates, 404 page, search results

**Custom themes**:
Built by developers using HubL, CSS, and JavaScript. A theme package includes:
- Template files (`.html`)
- CSS files
- JavaScript files
- Module definitions (`.module/`)
- Theme configuration (`theme.json`)
- Field schemas

**Theme settings** (available in the UI after installing a theme):
- Global colors (primary, secondary, accent, background, text)
- Font stacks (headings, body, navigation)
- Logo upload
- Social media links
- Footer content
- GDPR cookie banner

### Drag-and-Drop Page Editor

1. **Marketing** > **Website** > **Website Pages** > Create
2. Choose template from your theme
3. **Drag-and-drop editor** interface:
   - **Left panel**: Available modules (text, image, form, CTA, video, testimonial, logo cloud, pricing table, rich text, custom modules)
   - **Center**: Live preview (Desktop/Mobile/Tablet toggles)
   - **Right panel** (click a module): Content tab, Style tab, Advanced tab

**Module types available in drag-and-drop**:
| Module | What It Does |
|--------|-------------|
| Text | Rich text with formatting |
| Image | Single image with alt text and link |
| Button | CTA button with style options |
| Form | HubSpot form embed |
| CTA | Call-to-action button with tracking |
| Video | Embed YouTube, Vimeo, or HubSpot video |
| Testimonial | Quote with author photo |
| Logo Cloud | Grid of partner/client logos |
| Pricing Table | Feature comparison table |
| Divider | Horizontal line |
| Spacer | Vertical space |
| Social Follow | Social media icons |
| Rich Text | Advanced formatted content |
| Menu | Navigation menu |
| Header/Footer | Global content blocks |
| Blog Subscription | Email signup form |
| Custom Module | Any module from your theme |

### Global Content

Global content blocks appear on every page and update everywhere when changed:

**Header**:
- Logo, navigation menu, CTA button (e.g., "Get Started")
- Login/account links
- Language switcher (for multi-language sites)
- Search bar

**Footer**:
- Copyright text
- Navigation links
- Social media icons
- Privacy policy and terms links
- Cookie settings link
- Unsubscribe link (for GDPR compliance)

**Global modules**:
- Any module can be set as "Global" — changes apply site-wide
- Useful for: Promo banners, announcement bars, site-wide CTAs

### SEO Settings per Page

Each page has SEO settings accessible from the settings panel:

**SEO fields**:
- **Page title**: Displayed in browser tab and search results (50-60 chars recommended)
- **Meta description**: Displayed in search results (150-160 chars recommended)
- **URL slug**: The page URL (e.g., `/about-us`)
- **Featured image**: Social sharing preview image (Open Graph + Twitter Cards)
- **Canonical URL**: If content is syndicated elsewhere
- **NOINDEX**: Hide from search engines
- **NOFOLLOW**: Don't follow links on this page
- **Structured data**: Schema.org markup (auto-generated for blog, article, product)

**Sitemap**: HubSpot auto-generates your sitemap.xml

### Forms on Pages

Embed forms on website pages:
1. Add the "Form" module to any page
2. Select existing form or create new one in the module
3. Style: Inline label, stacked label, or placeholder
4. Set thank-you behavior: Inline message or redirect URL

---

## HubL Templating Language

HubL (HubSpot Markup Language) is HubSpot's templating language, similar to Jinja2, Liquid, or Django templates. It's used to create dynamic templates and modules.

### HubL Syntax

```hubL
{# This is a comment #}

{{ variable }}          {# Output a value #}
{% tag %}               {# Execute a tag (for, if, block) #}
{{ "text"|filter }}     {# Apply a filter to a value #}
```

### Variables

```hubL
{{ content.name }}              {# Page name #}
{{ content.absolute_url }}      {# Page URL #}
{{ content.body }}              {# Main content #}
{{ content.meta.title }}        {# Meta title #}
{{ content.meta.description }}  {# Meta description #}
{{ content.featured_image }}    {# Featured image #}

{{ request }}                   {# Current request info #}
{{ request.contact }}           {# Current contact (if logged in) #}
{{ request.user }}              {# Current user (if logged in) #}

{{ blog_author }}               {# Blog author (on author page) #}
{{ blog_post }}                 {# Current blog post (on post page) #}
{{ topic }}                     {# Current topic (on topic page) #}

{{ current_page }}              {# For paginated blog listings #}

{% module "my_module" path="@hubspot/text" %}  {# Include a module #}
```

### Filters

```hubL
{{ "hello"|capitalize }}        {# Output: "Hello" #}
{{ "hello world"|title }}       {# Output: "Hello World" #}
{{ "HELLO"|lower }}             {# Output: "hello" #}
{{ name|default("Guest") }}     {# Default value if empty #}
{{ content.body|striptags }}    {# Remove HTML tags #}
{{ content.body|truncate(100) }} {# Truncate to 100 chars #}
{{ content.body|safe }}         {# Don't escape HTML #}
{{ [1, 2, 3]|first }}          {# Output: 1 #}
{{ [1, 2, 3]|last }}           {# Output: 3 #}
{{ [1, 2, 3]|join(", ") }}     {# Output: "1, 2, 3" #}
{{ content.updated|datetimeformat('%B %e, %Y') }}  {# Format date #}
{{ content.publish_date|format_date('long') }}      {# Pre-set date format #}
{{ list|length }}               {# Number of items #}
{{ list|sort(False, False) }}   {# Sort list #}
{{ list|batch(3) }}             {# Split into groups of 3 #}
```

### Control Flow

```hubL
{% if request.contact.is_logged_in %}
  Welcome back, {{ request.contact.firstname }}!
{% elif request.contact %}
  {{ request.contact.firstname }}, complete your profile!
{% else %}
  Welcome, guest!
{% endif %}

{% for item in items %}
  <div class="item">{{ item.name }}</div>
{% else %}
  <p>No items found.</p>
{% endfor %}
```

### For Loop Variables

```hubL
{% for item in items %}
  {{ loop.index }}     {# Current iteration (1-indexed) #}
  {{ loop.index0 }}    {# Current iteration (0-indexed) #}
  {{ loop.first }}     {# True if first item #}
  {{ loop.last }}      {# True if last item #}
  {{ loop.length }}    {# Total number of items #}
{% endfor %}
```

### Macros (Reusable Template Fragments)

```hubL
{% macro card(title, body, image) %}
<div class="card">
  <img src="{{ image }}" alt="{{ title }}">
  <h3>{{ title }}</h3>
  <p>{{ body }}</p>
</div>
{% endmacro %}

{# Usage #}
{{ card("Product A", "Description here", "image.jpg") }}
{{ card("Product B", "Another description", "image2.jpg") }}
```

### HubL Functions

```hubL
{# Query HubDB tables #}
{% set rows = hubdb_table_rows(1234567) %}
{% set rows = hubdb_table_rows(1234567, "orderBy=-created_at") %}
{% set row = hubdb_table_row(1234567, "row-id") %}

{# Query blog posts #}
{% set posts = blog_recent_posts('default', 5) %}
{% set posts = blog_recent_tag_posts('default', 'news', 5) %}
{% set post = blog_recent_topic_posts('default', 'topic-slug', 5) %}

{# File and asset URLs #}
{% set image_url = get_asset_url('/images/logo.png') %}
{% set image_url = resize_image_url(original_url, 0, 0, 300) %}

{# Content IDs #}
{{ content.id }}              {# Page/blog ID #}
{{ group.id }}                {# Blog ID #}
{% set group = blog_by_id('default') %}  {# Blog group #}

{# Custom module fields #}
{{ module.field_name }}       {# Access module field value #}
```

### Extending Templates

```hubL
{# base.html - Parent template #}
<!DOCTYPE html>
<html>
<head>
  <title>{% block title %}Default Title{% endblock %}</title>
</head>
<body>
  <header><!-- Global header --></header>
  <main>
    {% block content %}{% endblock %}
  </main>
  <footer><!-- Global footer --></footer>
</body>
</html>

{# about.html - Child template #}
{% extends "templates/base.html" %}

{% block title %}About Us{% endblock %}

{% block content %}
<h1>About Our Company</h1>
<p>Content specific to the About page.</p>
{% endblock %}
```

---

## Custom Modules — Complete Guide

Custom modules are reusable content blocks that you can use in the drag-and-drop editor.

### Creating a Custom Module

1. Navigate to **Design Tools** (Settings > Tools > Design Tools)
2. Click "File" > "New file" > "Module"
3. **Field schema** (fields.json): Define what fields the module accepts:

```json
[
  {
    "type": "text",
    "name": "title",
    "label": "Title",
    "default": "Default Title"
  },
  {
    "type": "richtext",
    "name": "body",
    "label": "Body Content",
    "default": "<p>Default content</p>"
  },
  {
    "type": "image",
    "name": "featured_image",
    "label": "Featured Image",
    "default": {
      "src": "",
      "alt": "Featured image"
    }
  },
  {
    "type": "boolean",
    "name": "show_cta",
    "label": "Show CTA Button",
    "default": true
  },
  {
    "type": "url",
    "name": "cta_link",
    "label": "CTA Link",
    "default": { "href": "", "type": "EXTERNAL" }
  },
  {
    "type": "color",
    "name": "background_color",
    "label": "Background Color",
    "default": { "color": "#ffffff", "opacity": 100 }
  }
]
```

4. **Module template** (module.html): The HubL output:

```hubL
<div class="custom-hero" style="background-color: {{ module.background_color.color }}">
  <h2>{{ module.title }}</h2>
  <div class="hero-body">{{ module.body }}</div>
  
  {% if module.featured_image.src %}
    <img src="{{ module.featured_image.src }}" alt="{{ module.featured_image.alt }}">
  {% endif %}
  
  {% if module.show_cta %}
    <a href="{{ module.cta_link.href }}" class="btn btn-primary">
      Learn More
    </a>
  {% endif %}
</div>
```

5. **CSS** (module.css):
```css
.custom-hero {
  padding: 60px 20px;
  text-align: center;
}
.custom-hero h2 {
  font-size: 48px;
  margin-bottom: 20px;
}
```

6. **JS** (module.js):
```javascript
(function() {
  // Module-specific JavaScript
  console.log('Hero module initialized');
})();
```

7. Save the module — it appears in your drag-and-drop editor under "Custom modules"

### Module Field Types

| Field Type | UI Element | Use Case |
|------------|-----------|----------|
| text | Single-line input | Titles, names, short text |
| textarea | Multi-line input | Longer text, descriptions |
| number | Number input | Quantities |
| boolean | Checkbox | Show/hide toggle |
| color | Color picker | Background, text colors |
| image | Image picker | Photos, graphics |
| icon | Icon picker | FontAwesome icons |
| rich_text | WYSIWYG editor | Formatted content |
| url | URL input | Links |
| link | URL + label | Linked text |
| choice | Dropdown | Single select |
| checkbox | Checkbox group | Multi-select |
| file | File upload | Documents, downloads |
| video | Video embed | YouTube/Vimeo |
| font | Font picker | Custom fonts |
| group | Field group | Nested fields |

### Module Categories

Organize modules in the drag-and-drop editor:
- **Header modules**: Hero banners, navigation
- **Content modules**: Text, image, video, testimonials
- **Conversion modules**: Forms, CTAs, pricing tables
- **Footer modules**: Footer content, social links
- **Blog modules**: Post listing, subscription

---

## Blogging — Complete Guide

### Blog Setup

1. **Settings** > **Marketing** > **Blog** > **Blog dashboard**
2. Configure:
   - **Blog home**: URL prefix (`/blog`, `/resources`, `/insights`)
   - **Post URL**: `/{slug}` (simple) or `/{year}/{month}/{slug}` (date-based)
   - **RSS feed**: Enable, customize description
   - **Comments**: Enable, moderate, require login
   - **Author pages**: Enable author bios
   - **Social sharing**: Auto-format for networks
   - **Subscription**: Enable blog email subscription

### Content Calendar

1. **Marketing** > **Blog** > **Content Calendar**
2. Calendar view shows:
   - Published posts
   - Scheduled posts
   - Drafts with due dates
   - Editorial tasks (assigned to team members)
3. Drag and drop to reschedule
4. Filter by author, blog, topic

### Blog Post Editor

- **Rich text editor** with drag-and-drop modules
- **Sidebar settings**:
  - Post body
  - Excerpt (listing preview)
  - Featured image
  - Author (from your blog team)
  - Topics/tags (for SEO and categorization)
  - Publish date (past or future)
  - Password (member-only)
  - Custom meta description
  - Custom URL slug
- **Blog module types**: Text, image, CTA, social share, subscription, author bio, related posts, comments

### Multi-Language Blogging

Structure for international blogs:
- `/en/blog/post-title`
- `/es/blog/titulo-del-articulo`
- `/fr/blog/titre-de-larticle`

1. Create post in primary language
2. Click "Add language" → choose language
3. Translate content
4. Language switcher on blog displays appropriate version

---

## Content AI — Complete Guide

### AI Blog Generation

1. In blog editor, click the Breeze AI icon (sparkle)
2. Select "Generate blog post"
3. Describe what you want:
   - **Topic**: "How to choose a CRM for small business"
   - **Tone**: Professional, Casual, Technical, Persuasive
   - **Audience**: Small business owners, Marketing managers, Developers
   - **Key points**: "budget considerations, must-have features, implementation timeline"
   - **Length**: Short (300-500), Medium (500-1000), Long (1000+)
   - **CTA**: "Start your free trial"
4. Click "Generate"
5. AI creates: Title, introduction, body sections (with H2 headings), conclusion, CTA
6. Review and edit
7. Generate accompanying image with AI Image Generator

### AI Image Generation

1. In any content editor, add image module → "Generate with AI"
2. **Prompt**: "Modern office with collaborative team, natural lighting, plants, diverse group"
3. **Style**: Photorealistic, Illustration, Flat design, 3D render, Watercolor, Abstract
4. **Aspect ratio**: 16:9 (blog), 1:1 (social), 4:3 (email), 9:16 (stories)
5. Generate → choose from 4 options → edit or regenerate

### AI Translation

1. In the blog/page settings, click language dropdown → "Add language"
2. Select target language (20+ supported)
3. AI translates all content, preserving formatting, links, and images
4. Review and publish translated version

### Brand Voice

Define brand voice for all AI-generated content:
1. **Settings** > **Content** > **Brand Voice**
2. Create profile:
   - **Brand description**: "Innovative B2B SaaS helping businesses automate workflows"
   - **Tone**: Professional yet approachable
   - **Vocabulary**: Use "empower", "streamline", "transform"; avoid "cheap", "easy button"
   - **Formatting**: Short paragraphs, use bullet points, minimal jargon
3. AI will follow these guidelines when generating content

---

## Local Development — Complete Guide

### HubSpot CLI Setup

```bash
# Install globally
npm install -g @hubspot/cli

# Authenticate with your portal
hs init

# Choose authentication method:
# 1. Personal access key (recommended for local dev)
# 2. OAuth (for apps)
```

### Useful CLI Commands

```bash
# Upload a file to HubSpot
hs upload src/index.html my-theme/templates/index.html

# Download files from HubSpot
hs fetch my-theme/templates src/

# Watch for local changes and auto-upload
hs watch src my-theme

# Create a new theme scaffold
hs create theme my-theme-name

# Create a new template
hs create template my-template

# Create a new module
hs create module my-module-name

# List uploaded assets
hs list my-theme

# Remove a file
hs remove my-theme/templates/old-page.html

# Open Design Tools in browser
hs open

# See current portal info
hs info
```

### Project Structure

A typical local development project:
```
my-theme/
├── theme.json                    # Theme configuration
├── templates/
│   ├── home.html                 # Homepage template
│   ├── about.html                # About page template
│   ├── contact.html              # Contact template
│   └── blog_post.html            # Blog post template
├── modules/
│   ├── hero-banner.module/
│   │   ├── module.html           # HubL template
│   │   ├── fields.json           # Field schema
│   │   ├── module.css            # Module styles
│   │   └── module.js             # Module scripts
│   └── pricing-table.module/
│       ├── module.html
│       └── fields.json
├── css/
│   ├── main.css                  # Global styles
│   └── _variables.css            # CSS variables
├── js/
│   └── main.js                   # Global scripts
└── images/
    ├── logo.svg
    └── hero-bg.jpg
```

### Git Integration (Enterprise)

Connect GitHub/Bitbucket/GitLab repos:
1. **Settings** > **Content** > **Connected apps** > **Git**
2. Connect repository
3. Configure branch: `main` → production, `develop` → staging/QA
4. Auto-deploy on push to connected branch
5. Deploy previews for PRs

---

## Serverless Functions — Complete Guide

Serverless functions run Node.js code on HubSpot's edge network.

### Creating a Function

1. In Design Tools, create new file → **Serverless function**
2. Write your function:

```javascript
// Example: Form submission handler
exports.main = async (context, sendResponse) => {
  const { body } = context;
  
  // Access HubSpot API
  const response = await fetch(
    `https://api.hubapi.com/crm/v3/objects/contacts/${body.contactId}`,
    {
      headers: {
        'Authorization': `Bearer ${context.authorization}`,
        'Content-Type': 'application/json'
      }
    }
  );
  
  const contactData = await response.json();
  
  sendResponse({
    statusCode: 200,
    body: {
      message: 'Contact retrieved successfully',
      contact: contactData
    }
  });
};
```

### Function Configuration

**Secrets and environment variables**:
1. Design Tools → Functions → Secrets
2. Add secrets: API keys, database connection strings
3. Access in code: `process.env.MY_SECRET`

**Timeout**: 20 seconds maximum execution time

**Triggers**: Call functions via:
- Webhook endpoints (external systems can POST to your function URL)
- Custom-coded workflow actions
- Custom-coded cards
- Form submission handlers

---

## HubDB — Complete Guide

HubDB is a database for structured content within Content Hub.

### Creating a HubDB Table

1. **Design Tools** → **HubDB** → Create table
2. **Table name**: "Products" or "Team Members"
3. **Columns**: Add columns with types:
   - Text, Number, Date, DateTime, Boolean
   - File, Image, Video
   - URL, Email, Phone
   - Rich text (limited)
   - Select (dropdown)
   - Multi-select (checkboxes)
4. **Foreign key**: Link to another HubDB table
5. **Add rows**: Enter data manually or import CSV (up to 10,000 rows)

### Querying HubDB in HubL

```hubL
{# Get all rows #}
{% set products = hubdb_table_rows(1234567) %}
{% set products = hubdb_table_rows("Products") %}

{# With filters #}
{% set active_products = hubdb_table_rows(1234567, "active=true") %}

{# With sorting and limit #}
{% set top_products = hubdb_table_rows(1234567, "orderBy=-price&limit=10") %}

{# Get a single row #}
{% set product = hubdb_table_row(1234567, "row-id-here") %}

{# Display rows #}
{% for product in products %}
  <div class="product">
    <h3>{{ product.name }}</h3>
    <p>{{ product.description }}</p>
    <span>${{ product.price }}</span>
  </div>
{% endfor %}
```

### Dynamic Pages from HubDB

Create pages that automatically generate from HubDB rows:

1. Create a **dynamic template** that queries a HubDB table
2. Set the table as the data source for the template
3. Each row generates a URL: `/products/product-name`
4. Template displays the row's data
5. New rows → new pages (published automatically)

### HubDB Use Cases

- Product catalogues with individual product pages
- Team member directory with profile pages
- FAQ sections with expandable answers
- Event schedules with speaker details
- Location/office directories

---

## Multi-Language Content — Complete Guide

### Setting Up Multi-Language

1. **Settings** > **Content** > **Languages**
2. Set primary language (default)
3. Add supported languages (up to 5 on Pro, unlimited on Enterprise)
4. URL structure: Choose `/{lang}/` prefix or subdomain (`es.yourcompany.com`)

### Creating Translated Content

**For pages/blog posts**:
1. Create content in primary language
2. In settings, click "Add language" → choose language
3. Translation is created as a linked copy
4. HubSpot manages the connection between language versions
5. Language switcher automatically shows only available translations

### Language Switcher

1. Add the "Language Switcher" module to header or footer
2. It auto-detects the user's browser language
3. Shows available language options
4. Redirects to appropriate language version

### Multi-Language SEO

- `hreflang` tags auto-added to pages
- Each language version has independent SEO settings
- URL structure: `/en/blog/post` and `/es/blog/articulo`
- Sitemap includes all language versions

---

## Membership & Gated Content — Complete Guide

### Password Protection

1. In page settings, check "Password protect this page"
2. Set a password
3. Visitors must enter password to view content
4. Best for: Internal documents, client portals, preview links

### Registration-Required Pages

1. In page settings, check "Require registration"
2. HubSpot form collects name and email
3. Visitor submits form → contact created in CRM → page loads
4. Track who views gated content on the contact timeline

### Membership Tiers (Content Hub Enterprise)

Create gated content with tiered access:
1. **Settings** > **Content** > **Membership**
2. Create membership tiers: Free, Premium, Enterprise
3. Assign contacts to tiers based on CRM data (deal size, plan type)
4. Pages can require specific membership tier
5. URL-level access control

---

## Adaptive Testing — Complete Guide

A/B and multivariate testing for website pages:

1. Open a page → Click "Create test"
2. Choose test type:
   - **A/B test**: Test two versions of the page
   - **Adaptive test**: Test multiple variations
3. Create variants: Copy page and make changes
4. Set traffic split: 50/50 for A/B, even for adaptive
5. Choose goal metric: Click-through rate, Form submission rate, Time on page
6. Set minimum sample size
7. Launch test → HubSpot shows winner to more visitors over time

---

## Limits That Matter

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Website pages | 25 | 100 | Unlimited | Unlimited |
| Blog posts | 250 | 2,500 | Unlimited | Unlimited |
| Custom domains | 1 | 5 | 15 | Unlimited |
| Custom modules | 0 | 0 | Unlimited | Unlimited |
| Serverless functions | 0 | 0 | 10 | 100 |
| HubDB tables | 0 | 0 | 25 | 100 |
| HubDB rows per table | 0 | 0 | 10,000 | 10,000 |
| Hosting bandwidth | 10GB/mo | 50GB/mo | 100GB/mo | 250GB/mo |
| CDN | ✓ | ✓ | ✓ | ✓ |
| Multi-language | ✓ (1 lang) | ✓ (1 lang) | 5 languages | Unlimited |
| Adaptive tests | 0 | 0 | 10 | Unlimited |
| Content AI | Limited | Limited | ✓ | ✓ |

---

## Common Gotchas

### 1. HubL Debugging
HubL errors don't show in the browser by default. Use `{% debug %}` to output all available variables. Check the browser console for errors.

### 2. Template Caching
HubSpot caches templates aggressively. After making changes, use "Clear cache" in page settings or wait 5-10 minutes for changes to appear.

### 3. HubDB Performance
Large HubDB tables (>5,000 rows) can slow down page load. Use pagination and limit queries. Consider adding search/filter to the page rather than displaying all rows.

### 4. Serverless Function Timeouts
Functions have a 20-second hard timeout. Long-running operations (API calls to slow endpoints, large file processing) will fail. Use async patterns or break work into smaller functions.

### 5. Custom Module Fields
Adding or removing fields from a custom module after it's been used on pages can cause errors. Existing pages that used the module may lose data or show broken modules.

### 6. Asset URLs
After uploading a file, HubSpot gives it a hashed URL. Moving or renaming the file breaks all links. Use the asset URL from Design Tools rather than the file name.

### 7. Git Integration Limitations
The Git integration (Enterprise) only syncs code files, not content. Blog posts, landing pages, and form settings are not in the Git repo.

### 8. Multi-Language URL Structure
Changing the URL structure after publishing will break existing links. Plan your URL structure (`/lang/` prefix vs subdomain) before publishing translated content.