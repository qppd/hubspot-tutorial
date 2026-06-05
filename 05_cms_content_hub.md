# 5. CMS Hub (Content Hub)

## What It Does
HubSpot CMS Hub (now called **Content Hub** in current branding) is a content management system for building websites, blogs, landing pages, and managing content at scale. It combines drag-and-drop editing for marketers with full developer flexibility (HubL templating, custom modules, serverless functions, the HubSpot CLI, and Git integration).

## Key Features

### Website Builder
- **Drag-and-drop editor**: build pages with pre-built modules — marketers can assemble pages without code
- **Responsive design**: mobile-optimized by default across all templates
- **Theme system**: Marketplace themes (free and paid), custom themes, or start from scratch
- **Page types**: landing pages, website pages, blog posts, listing pages, system pages (404, search results, etc.)
- **Global content**: headers, footers, theme settings (change once, apply everywhere)
- **Smart content**: show different content based on contact properties, device type, language, or list membership
- **Multi-language**: full internationalization support with URL structure per language (/en/, /es/, /fr/)
- **Domain management**: multiple custom domains, auto-SSL provisioning via Let's Encrypt
- **Password-protected pages**: member-only content with built-in authentication
- **A/B testing**: test page variants (Content Hub Pro+)
- **SEO recommendations**: page-level analysis, meta tag management, canonical URLs, structured data
- **Content staging**: draft pages, schedule publish, rollback to previous versions
- **Branches**: content branching (Enterprise) — clone entire site for redesign, merge back when ready

### HubL Templating
- **HubL**: HubSpot's templating language (Jinja2-inspired syntax)
- **Template types**: `base.html` (base layout), `page.html`, `blog.html`, `email.html`, `search_results.html`, `landing-page.html`
- **Variables**: pull dynamic data from CRM, query parameters, HubSpot objects (`{{ content.absolute_url }}`, `{{ request_contact.firstname }}`)
- **HubL functions**:
  - `{{ blog_recent_posts() }}` — fetch recent blog posts
  - `{{ crm_objects("contacts") }}` — query CRM objects
  - `{{ get_asset_url() }}` — reference uploaded files
  - `{{ hubdb_table_rows() }}` — query HubDB tables
- **Conditional rendering**: `{% if request_contact.is_logged_in %}`, `{% if widget.bg_color %}`
- **Loop over data**: `{% for item in module.items %}`
- **Macros**: reusable code snippets with parameters (`{% macro render_card(title, body) %}`)
- **CPT (Content Partials)**: reusable page sections — header, footer, navigation, sidebar
- **HubL playground**: test HubL snippets live in the browser at app.hubspot.com

### Custom Modules
- **Module builder**: build reusable UI components with field definitions
- **Field types**: text, image, video, rich text, CTA, logo, icon, form, button, spacer, social follow, embed, and 20+ more
- **CSS/JS in modules**: module-scoped styling — styles and scripts only apply to that module instance
- **Module parameters**: allow content editors to configure content and layout without touching code
- **Theme modules**: import and override modules from purchased themes
- **Module marketplace**: publish and sell modules on the HubSpot Marketplace
- **Global modules**: update once, reflect everywhere the module is used
- **Module export**: download as ZIP for sharing across portals

### Blogging
- **Blog editor**: rich text with drag-and-drop modules
- **Topic clusters**: pillar pages + related cluster content for SEO
- **Topic suggestions**: AI-powered content ideas based on search data (Content Hub)
- **SEO recommendations**: real-time readability, keyword density, meta data checks
- **Internal linking**: auto-suggestions for linking related posts based on topic cluster membership
- **Blog listing design**: customizable listing page (grid, list, featured post, category-based)
- **Blog tags**: categorize with hierarchical tags and nested categories
- **Multi-author**: author profiles with bios, images, and social links
- **RSS feeds**: auto-generated for each topic, author, and language
- **Content calendar**: plan, schedule, and track blog posts (Content Hub)
- **Content remix**: repurpose blog posts into social posts, emails, or landing pages with one click (Content Hub)
- **Breeze AI content assistant**: generate blog drafts, rephrase tone, expand sections, and translate content

### HubDB (Dynamic Database Tables)
- **HubDB**: a database-table system within the CMS for structured content
- **Use cases**: pricing tables, product catalogs, team directories, location listings, event schedules
- **Data types per column**: text, number, URL, image, file, boolean, datetime, email, phone, rich text
- **HubL integration**: query HubDB tables via `{{ hubdb_table_rows() }}` in templates
- **Dynamic pages**: create one template that renders a different page for each HubDB row
- **API access**: CRUD operations on HubDB tables via REST API
- **Import/export**: CSV import and export for bulk management
- **Limits**: Free (5 tables, 100 rows each), Starter (20 tables, 5k rows), Pro (100 tables, 10k rows), Enterprise (500 tables, 50k rows)

### SEO & Analytics
- **Content strategy**: topic planning based on search volume and competition data
- **Keyword tracking**: positions, estimated traffic, search volume over time
- **SEO recommendations**: page-level and site-level issues (meta tags, headings, internal links, page speed, mobile usability, Core Web Vitals)
- **Traffic analytics**: organic, paid, social, email, direct, referral
- **Conversion analytics**: page views → submissions → customers
- **Site search**: track what visitors search on your site — identify content gaps
- **Page performance**: load time, Core Web Vitals, mobile usability score
- **Content performance**: views, clicks, CTA clicks, form submissions per page
- **Attribution**: see which content influenced conversions (first interaction, last interaction, linear, W-shaped)

### Content Hub Features (Content Hub plan)
- **Breeze AI Assistant**: generate, rewrite, summarize, translate, and adapt tone of content
- **Content Remix**: turn one piece of content into blog post, social posts, email, landing page, podcast audio
- **Content Calendar**: drag-and-drop calendar for all content types (blog, landing pages, social, emails)
- **Campaign Management**: group assets by campaign (Content Hub + Marketing Hub)
- **Brand Voice**: set tone and style guidelines enforced across all Breeze AI content generation
- **Generative AI**: image generation (DALL-E powered), headline suggestions, body copy expansion
- **Audio/podcast**: create audio versions of blog posts — embed as podcast
- **Content attribution**: which pieces of content drive pipeline and revenue
- **Video hosting**: upload, embed, and analyze video content with engagement metrics
- **Content analytics**: per-piece performance data across all channels

### Developer Tools
- **HubSpot CLI**: `npm install -g @hubspot/cli`
  - `hs init` — authenticate
  - `hs fetch` — download files from Design Manager
  - `hs watch` — watch for local changes and auto-upload
  - `hs upload` — upload files to CMS
  - `hs create` — scaffold template, module, theme
  - `hs lint` — validate HubL syntax
- **Local development**: VS Code + CLI for full local dev workflow with hot reload
- **Git integration**: connect GitHub repo to Design Manager (Enterprise) — auto-deploy on push
- **Design Tools**: browser-based IDE for HubL, CSS, JS (at app.hubspot.com/design-manager)
- **Webpack/ESBuild**: bundling and transpilation for JS assets
- **CMS API**: programmatic content management (pages, blog posts, templates, HubDB)
- **Custom objects in CMS**: build dynamic pages backed by custom CRM objects (Enterprise)
- **HubDB API**: CRUD on database tables via REST
- **Site search API**: customize and extend site search results
- **Webhooks**: triggers on content publish, update, delete
- **Asset pipeline**: minification, image optimization, CDN delivery
- **Edge cache**: Cloudflare-powered global CDN with cache purging from the UI
- **Serverless functions**: run Node.js on HubSpot edge (Enterprise) — cold start ~1s, 10s timeout

## Step-by-Step: Creating a Website Page

1. Marketing (or Content) > Website > Website Pages > Create
2. Choose template (blank or pre-built)
3. Drag modules onto the page:
   - Header (logo, navigation, CTA)
   - Hero (image, headline, subtext, button)
   - Text/rich text
   - Form
   - CTA button
   - Image gallery
   - Testimonial slider
   - Pricing table
   - Footer (global content)
4. Customize each module's content and design
5. Add smart content rules:
   - Show different hero image for returning vs new visitors
   - Show language-specific content based on browser/language preference
6. Set SEO: Page title, meta description, URL slug, canonical URL
7. Set password protection (optional)
8. Preview (desktop, tablet, mobile)
9. Publish or schedule for later

## Step-by-Step: Adding a Custom Module (Developer)

1. In Design Tools (or locally via CLI), create a module:
2. Folder: `custom-modules/my-module/`
3. Files needed:
   - `module.html` — HubL template
   - `meta.json` — field definitions
   - `fields.json` — (optional, can be in meta.json)
4. Example `meta.json`:
   ```json
   {
     "label": "Testimonial Card",
     "categories": ["text"],
     "fields": [
       { "name": "quote", "label": "Quote Text", "type": "richtext" },
       { "name": "author", "label": "Author Name", "type": "text" },
       { "name": "avatar", "label": "Avatar Image", "type": "image" },
       { "name": "rating", "label": "Star Rating", "type": "number", "default": 5 }
     ]
   }
   ```
5. Example `module.html`:
   ```hubL
   <div class="testimonial">
     <div class="stars">{% for i in range(module.rating) %}★{% endfor %}</div>
     <blockquote>{{ module.quote }}</blockquote>
     <div class="author">
       <img src="{{ module.avatar.src }}" alt="{{ module.author }}" />
       <cite>{{ module.author }}</cite>
     </div>
   </div>
   ```
6. Upload via CLI: `hs upload my-module custom-modules/my-module`

## Step-by-Step: Setting Up Local Dev with HubSpot CLI

1. Install: `npm install -g @hubspot/cli`
2. Authenticate: `hs init` → paste personal access key
3. Fetch existing files: `hs fetch --overwrite`
4. Watch for changes: `hs watch --remove`
5. Upload: `hs upload src/ target/`
6. Git integration: `hs sync --mode=git` (Enterprise — sync GitHub → Design Manager)

## Limits That Matter

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Website pages | 25 | 100 | Unlimited | Unlimited |
| Blog posts | 250 | 2,500 | Unlimited | Unlimited |
| Landing pages | 20 | 70 | 100 | Unlimited |
| Custom domains | 1 | 5 | 15 | Unlimited |
| Bandwidth | 10GB | 100GB | 300GB | 2TB+ |
| Storage | 1GB | 10GB | 25GB | 100GB+ |
| Custom modules | 50 | 100 | Unlimited | Unlimited |
| HubDB tables | 5 | 20 | 100 | 500 |
| HubDB rows/table | 100 | 5k | 10k | 50k |
| Serverless functions | — | — | — | ✓ (varies) |
| Content branches | — | — | — | ✓ |
| A/B tests (concurrent) | — | — | 5 | 10 |
| Smart content rules | — | — | 100 | 1,000 |
| Users with edit access | 2 | 5 | 50 | Unlimited |
| API calls | 50/day | Unlimited* | Unlimited* | Unlimited* |
| Content staging | — | — | ✓ | ✓ |
| SSL auto-provisioning | ✓ | ✓ | ✓ | ✓ |

*API rate limits still apply per plan.

## Use Cases

- Build a full marketing website with blog, landing pages, and resource center
- Create multi-language sites for global audiences
- Personalize content per visitor (smart content rules)
- Build custom reusable modules without writing HTML every time
- Run A/B tests on landing pages to improve conversion rates
- Manage content calendar and repurpose content across channels (Content Hub)
- Developer-led sites with full control over HTML/CSS/JS via custom themes
- Build dynamic database-powered pages with HubDB (e.g., product catalog, pricing tables)

## Common Gotchas

- Custom modules must be uploaded via Design Tools or CLI — no in-browser editor for module code
- HubL caching can cause stale templates (publish or clear cache to see changes)
- Smart content only works for logged-in contacts or those with HubSpot tracking cookie
- Content staging doesn't include custom modules — must deploy separately
- Blog post URLs cannot be changed after publish (set up 301 redirects in modules)
- Free tier CMS pages show HubSpot branding in footer (removable on paid plans)
- Local dev requires `hs watch` to sync — changes made directly in HubSpot can be overwritten
- Serverless functions (Node.js) have cold start and 10-second timeout limits
- SSL is auto-provisioned via Let's Encrypt but can take up to 24 hours for custom domains
- HubDB rows imported via CSV are limited to the row count per tier
- Content branches merge is one-way — test thoroughly before merging