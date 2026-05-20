# 5. CMS Hub (Content Hub)

## What It Does
HubSpot CMS Hub (now called Content Hub in latest branding) is a content management system for building websites, blogs, landing pages, and managing content at scale. It combines drag-and-drop editing for marketers with full developer flexibility (HubL templating, custom modules, serverless functions).

## Key Features

### Website Builder
- **Drag-and-drop editor**: build pages with pre-built modules
- **Responsive design**: mobile-optimized by default
- **Theme system**: Marketplace themes or custom themes
- **Page types**: landing pages, website pages, blog posts, listing pages, system pages
- **Global content**: headers, footers, theme settings (change once, apply everywhere)
- **Smart content**: show different content based on contact properties, device, language, list membership
- **Multi-language**: full internationalization support (URL structure per language)
- **Domain management**: multiple custom domains, SSL auto-provisioning
- **Password-protected pages**: member-only content
- **A/B testing**: test page variants (Content Hub Pro+)
- **SEO recommendations**: page-level analysis, meta tag management, canonical URLs
- **Content staging**: draft pages, schedule publish, rollback
- **Branches**: content branching (Enterprise — clone entire site for redesign)

### HubL Templating
- **HubL**: HubSpot's templating language (Jinja2-inspired)
- **Template types**: `base.html`, `page.html`, `blog.html`, `email.html`, `search_results.html`
- **Variables**: pull dynamic data from CRM, query params, HubSpot objects
- **Macros**: reusable code snippets
- **CPT (Content Partials)**: reusable page sections
- **HubL functions**: `{{ content.absolute_url }}`, `{{ request_contact.firstname }}`, `{{ blog_recent_posts() }}`
- **Conditional rendering**: `{% if request_contact.is_logged_in %}`
- **Loop over CRM data**: `{% for contact in crm_objects("contacts") %}`
- **Custom modules**: reusable UI components with parameters
- **Serverless functions**: run Node.js on HubSpot edge (Enterprise)

### Custom Modules
- **Module builder**: build reusable components with field definitions
- **Field types**: text, image, video, rich text, CTA, logo, icon, form, button, space, social follow, etc.
- **CSS/JS in modules**: module-scoped styling
- **Module parameters**: allow editors to configure content without touching code
- **Theme modules**: import modules from themes
- **Module marketplace**: publish and sell modules
- **Global modules**: update once, reflect everywhere
- **Module export**: download as ZIP for sharing

### Blogging
- **Blog editor**: rich text with drag-and-drop modules
- **Topic clusters**: pillar pages + related cluster content
- **Topic suggestions**: AI-powered content ideas based on search data
- **SEO recommendations**: real-time readability, keyword density, meta data
- **Internal linking**: auto-suggestions for linking related posts
- **Blog listing design**: customizable listing page (grid, list, featured)
- **Blog tags**: categorize with hierarchical tags
- **Multi-author**: author profiles with bios and images
- **RSS feeds**: auto-generated for each topic/language
- **Content calendar**: plan, schedule, and track blog posts
- **Content remix**: repurpose blog posts into social posts, emails, or landing pages (Content Hub)
- **AI content assistant**: generate blog drafts, rephrase, expand sections (Content Hub)

### SEO & Analytics
- **Content strategy**: topic planning based on search volume and competition
- **Keyword tracking**: positions, estimated traffic, search volume
- **Recommendations**: page-level and site-level SEO issues (meta tags, headings, internal links, page speed)
- **Traffic analytics**: organic, paid, social, email, direct
- **Conversion analytics**: page views → submissions → customers
- **Site search**: track what visitors search on your site
- **Page performance**: load time, core web vitals, mobile usability
- **Content performance**: views, clicks, CTA clicks, form submissions per page
- **Attribution**: see which content influenced conversions (first interaction, last interaction, linear)

### Content Hub Features (Content Hub plan)
- **AI Assistant**: generate, rewrite, summarize, and translate content
- **Content Remix**: one piece of content → blog post, social post, email, landing page, podcast
- **Content Calendar**: drag-and-drop calendar for all content types
- **Campaign Management**: group assets by campaign (Content Hub + Marketing Hub)
- **Brand Voice**: set tone and style guidelines for AI content generation
- **Generative AI**: image generation, headline suggestions, body copy
- **Audio/podcast**: create audio versions of blog posts
- **Content attribution**: which pieces of content drive pipeline and revenue
- **Video hosting**: upload, embed, and analyze video content
- **Content analytics**: per-piece performance data across channels

### Developer Tools
- **Local development**: HubSpot CLI for local dev with hot reload
- **Git integration**: sync your repo with design manager (Enterprise)
- **Webpack/ESBuild**: bundling and transpilation
- **CMS API**: programmatic content management (pages, blog posts, templates)
- **Custom objects in CMS**: build dynamic pages backed by custom CRM objects
- **Site search API**: customize and extend site search
- **Webhooks**: triggers on content publish, update, delete
- **Asset pipeline**: minification, image optimization, CDN delivery
- **Edge cache**: Cloudflare-powered global CDN

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
   - Show language-specific content based on browser
6. Set SEO: Page title, meta description, URL slug, canonical URL
7. Set password protection (optional)
8. Preview (desktop, tablet, mobile)
9. Publish or schedule for later

## Step-by-Step: Adding a Custom Module (Developer)

1. In Design Tools (or local via CLI), create a module:
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

## Limits That Matter

- Website pages: Free (25), Starter (100), Pro (unlimited), Enterprise (unlimited)
- Blog posts: Free (250), Starter (2,500), Pro (unlimited)
- Custom domains: Free (1), Starter (5), Pro (15), Enterprise (unlimited)
- Bandwidth: 10GB (Free), 100GB (Starter), 300GB (Pro), 2TB+ (Enterprise)
- Storage: 1GB (Free), 10GB (Starter), 25GB (Pro), 100GB+ (Enterprise)
- Custom modules: Free (50), Starter (100), Pro (unlimited), Enterprise (unlimited)
- Serverless functions: Enterprise only (varies by tier)
- Content branches: Enterprise only
- A/B tests: Pro (5 concurrent), Enterprise (10 concurrent)
- Smart content rules: Pro (100), Enterprise (1,000)
- Users with edit access: Free (2), Starter (5), Pro (50), Enterprise (unlimited)
- Site search: on all pages, but indexing limited to your domain
- API calls: varies by plan (Free: 50/day, paid: unlimited with throttling)

## Step-by-Step: Setting Up Local Dev with HubSpot CLI

1. Install: `npm install -g @hubspot/cli`
2. Authenticate: `hs init` → paste API key or personal access key
3. Fetch existing files: `hs fetch --overwrite`
4. Watch for changes: `hs watch --remove`
5. Upload: `hs upload src/ target/`
6. Git integration: `hs sync --mode=git` (Enterprise — sync GitHub → Design Manager)

## Use Cases

- Build a full marketing website with blog, landing pages, and resource center
- Create multi-language sites for global audiences
- Personalize content per visitor (smart content)
- Build custom reusable modules without writing HTML every time
- Run A/B tests on landing pages to improve conversion rates
- Manage content calendar and repurpose content across channels (Content Hub)
- Developer-led sites with full control over HTML/CSS/JS via custom themes

## Common Gotchas

- Custom modules must be uploaded via Design Tools or CLI — no in-browser editor for code
- HubL caching can cause stale templates (publish or clear cache to see changes)
- Smart content only works for logged-in contacts or those with HubSpot tracking cookie
- Content staging doesn't include custom modules — must deploy separately
- Blog post URLs cannot be changed after publish (set up 301 redirects in modules)
- Free tier CMS pages show HubSpot branding in footer (removable on paid plans)
- Local dev requires `hs watch` to sync — changes made directly in HubSpot can be overwritten
- Serverless functions (Node.js) have cold start and 10-second timeout limits
- SSL is auto-provisioned but can take up to 24 hours for custom domains