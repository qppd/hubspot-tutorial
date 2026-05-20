# 8. Custom Objects, APIs & Developer Platform

## What It Does
HubSpot's developer platform extends the CRM beyond standard objects (Contacts, Companies, Deals, Tickets) with custom objects — letting you model your business domain directly in HubSpot. Combined with the HubSpot API (REST + GraphQL), webhooks, and app marketplace, you can build anything on top of HubSpot.

## Key Features

### Custom Objects
- **Custom object creation**: define new object types (e.g., "Courses", "Vehicles", "Properties", "Projects")
- **Fields/properties**: all standard property types (text, number, dropdown, date, etc.) — up to 10,000 per object
- **Associations**: link custom objects to contacts, companies, deals, tickets, and other custom objects
- **Association labels**: label each direction of association (e.g., Student → Course "enrolled in", Course → Student "has student")
- **Pipelines**: custom objects can have pipelines (Enterprise)
- **Records**: create, update, delete, search custom object records via API
- **Websites**: build dynamic pages backed by custom objects (Content Hub Enterprise)
- **Reporting**: custom objects in custom report builder and datasets
- **Import/export**: bulk import/export custom object records
- **Automation**: custom objects in workflows (triggers and actions)
- **Data sync**: sync custom objects between HubSpot and connected apps (Enterprise)
- **Limits**: 10 custom objects (Pro), 200 (Enterprise) / Record limits: 100k (Starter), 1M (Pro), 10M+ (Enterprise)

### HubSpot REST API
- **Base URL**: `https://api.hubapi.com`
- **Authentication**: API Key (legacy) or OAuth 2.0 (recommended) or Private App Access Token
- **API Categories**:
  - **CRM**: Contacts, Companies, Deals, Tickets, Custom Objects, Associations, Pipelines, Properties
  - **Marketing**: Email, Events, Forms, Landing Pages, Blog, Social Media, Campaigns
  - **Sales**: Quotes, Documents, Sequences, Meetings, Calling
  - **CMS**: Pages, Blog Posts, Templates, HubDB, Domains, Files
  - **Automation**: Workflows, Webhooks
  - **Commerce**: Payments, Invoices, Subscriptions, Products, Line Items
- **Pagination**: cursor-based (after/before)
- **Search**: POST /crm/v3/objects/{object}/search with filters, sorts, property selection
- **Batch operations**: batch create, read, update, upsert
- **Rate limits**: 100 requests per 10 seconds (varies by plan and endpoint)
- **Daily limits**: varies — 250k/day (Free), 500k/day (Starter), 1M+/day (Enterprise)

### Private Apps
- **Private App tokens**: create scoped API tokens for internal integrations
- **Scopes**: granular permissions per API category (e.g., `crm.objects.contacts.read`, `crm.objects.deals.write`)
- **Token rotation**: regenerate tokens without downtime
- **Rate limits**: separate from public app limits
- **App management**: Dashboard showing usage, scopes, last used

### Webhooks
- **Event types**: contact creation, property changes, deal stage changes, form submissions, and more
- **Delivery**: HTTP POST to your endpoint
- **Security**: signature verification with HMAC-SHA256
- **Retry**: exponential backoff for failed deliveries
- **Batching**: events delivered in batch (up to 100 events per batch)
- **Management**: create, enable/disable, test subscriptions via API or UI
- **Best for**: real-time sync, external notification, event-driven workflows

### GraphQL API
- **Endpoint**: `https://api.hubapi.com/api/graphql`
- **Use**: query multiple CRM objects and associations in one request
- **Reduce roundtrips**: fetch contact + its deals + company in one query
- **Query structure**: follow association paths to navigate related objects
- **Limitations**: read-only (no mutations), max 5 objects per query

### SDKs & Client Libraries
- **Official SDKs**:
  - Node.js: `@hubspot/api-client`
  - Python: `hubspot-api-client`
  - Ruby: `hubspot-api-client`
- **Community**: PHP, Go, .NET
- **SDK features**: auto-pagination, retry, rate limit handling, type definitions

### App Marketplace (Public Apps)
- **Public app listing**: publish your integration on HubSpot App Marketplace
- **OAuth flow**: standard OAuth 2.0 authorization code flow
- **App types**:
  - **Connected app**: access HubSpot data with user consent
  - **Portal-level app**: installed for entire HubSpot account
- **App review**: submit for HubSpot review (quality, security, UX standards)
- **Marketplace categories**: CRM, Marketing, Sales, Service, CMS, Commerce, Operations
- **Analytics**: installs, users, API usage
- **Monetization**: free, freemium, or paid apps

### CLI & Developer Tools
- **HubSpot CLI**: `npm install -g @hubspot/cli`
  - `hs init` — authenticate
  - `hs fetch` — download files from Design Manager
  - `hs watch` — watch and upload local changes
  - `hs upload` — upload files to CMS
  - `hs create` — scaffold template, module, theme
- **Design Tools**: browser-based IDE for HubL, CSS, JS
- **Local dev**: VS Code + CLI for full local development
- **Git integration**: connect GitHub repo to Design Manager (Enterprise)
- **HubL playground**: test HubL snippets in browser

### Custom Behaviors (Enterprise)
- **Custom-coded cards**: React or plain JS cards that appear on CRM record pages
  - Display real-time data from external systems
  - Has access to HubSpot SDK for CRM actions
  - Can trigger workflows, create/update records
- **Custom-coded actions**: workflow actions written in Node.js/Python
- **Custom-coded bots**: chatbot actions with custom logic
- **Custom-coded timeline events**: show external events on CRM timeline

### Association Labels & Custom Associations
- **Association types**: one-to-one, one-to-many, many-to-many
- **Association labels**: label each direction (e.g., "Primary contact" vs "Secondary contact")
- **Custom labels**: create labels beyond the defaults
- **Unlabeled associations**: simple relationship without semantic label
- **Association limits**: 1,000 associations per label per record (10,000 total per record)
- **Search by association**: filter/search records by association to another object

## Step-by-Step: Creating a Custom Object

### Via UI
1. Settings > Data Management > Custom Objects
2. Click "Create custom object"
3. Set singular name (e.g., "Course") and plural name ("Courses")
4. Set internal name (e.g., "course" — cannot be changed later)
5. Add properties:
   - "Course Name" (single-line text, required)
   - "Duration (weeks)" (number)
   - "Level" (dropdown: Beginner, Intermediate, Advanced)
   - "Certification Available" (checkbox)
6. Set primary display property (shown in associations and search results)
7. Set required properties
8. Configure associations:
   - Contact → Course ("enrolled in" / "has student")
   - Course → Deal ("targeted in" / "targets course")
9. Create

### Via API
```bash
POST /crm/v3/schemas
{
  "name": "course",
  "labels": { "singular": "Course", "plural": "Courses" },
  "primaryDisplayProperty": "course_name",
  "requiredProperties": ["course_name"],
  "properties": [
    { "name": "course_name", "label": "Course Name", "type": "string", "fieldType": "text" },
    { "name": "duration_weeks", "label": "Duration (weeks)", "type": "number", "fieldType": "number" },
    { "name": "level", "label": "Level", "type": "enumeration",
      "fieldType": "select", "options": [
        { "label": "Beginner", "value": "beginner" },
        { "label": "Intermediate", "value": "intermediate" },
        { "label": "Advanced", "value": "advanced" }
      ]
    }
  ],
  "associatedObjects": ["contact", "deal"]
}
```

## Step-by-Step: Setting Up OAuth 2.0 (Public App)

1. Go to App Marketplace > Manage Apps > Create app
2. Get **Client ID** and **Client Secret**
3. Set redirect URLs (your app's callback URLs)
4. Set scopes (required API permissions)
5. Build OAuth flow:
   ```
   GET https://app.hubspot.com/oauth/authorize?client_id=YOUR_CLIENT_ID&scope=contacts%20deals&redirect_uri=YOUR_REDIRECT_URI
   ```
6. User authorizes → redirect with `code` query param
7. Exchange code for tokens:
   ```
   POST https://api.hubapi.com/oauth/v1/token
   grant_type=authorization_code&client_id=...&client_secret=...&redirect_uri=...&code=...
   ```
8. Use `access_token` in API calls: `Authorization: Bearer {token}`
9. Refresh token when expired: `grant_type=refresh_token`

## Step-by-Step: Creating a Webhook Subscription

1. Settings > Integrations > Webhooks
2. Click "Create webhook subscription"
3. Choose event type: Contact property change, Deal stage change, Form submission, etc.
4. Set target URL: `https://your-server.com/hubspot-webhook`
5. Set secret: used for HMAC signature verification
6. Active webhook → HubSpot POSTs to your URL with JSON payload
7. Verify signature:
   ```javascript
   const crypto = require('crypto');
   const sig = req.headers['x-hubspot-signature-v3'];
   const expected = crypto.createHmac('sha256', secret)
     .update(JSON.stringify(req.body) + req.headers['x-hubspot-request-timestamp'])
     .digest('hex');
   if (sig === expected) { /* valid */ }
   ```

## API Example: Search Deals with Filters

```bash
POST https://api.hubapi.com/crm/v3/objects/deals/search
{
  "filterGroups": [{
    "filters": [
      { "propertyName": "amount", "operator": "GT", "value": "10000" },
      { "propertyName": "dealstage", "operator": "EQ", "value": "closedwon" }
    ]
  }],
  "sorts": [{ "propertyName": "createdate", "direction": "DESCENDING" }],
  "properties": ["dealname", "amount", "dealstage", "closedate"],
  "limit": 50
}
```

## Limits That Matter

- Custom objects: 10 (Pro), 200 (Enterprise)
- Custom object records: 100k (Starter), 1M (Pro), 10M (Enterprise)
- Properties per custom object: 1,000 (Pro), 10,000 (Enterprise)
- Associations per record: 10,000 max (1,000 per label)
- Association labels per object pair: 10 (Pro), 100 (Enterprise)
- Pipelines per custom object: Enterprise only, 50 max
- API rate: 100 requests per 10 seconds per app
- API daily: Free (250k), Starter (500k), Pro (1M), Enterprise (varies)
- Webhook timeout: 5 seconds
- Webhook retries: 3 attempts (exponential backoff)
- Batch API size: 100 records per batch (most endpoints)
- Search results per page: 200 max
- SDK supported: Node.js, Python, Ruby (official); community libraries for other languages
- Custom-coded cards: Enterprise only
- Custom-coded workflows: Operations Hub Pro/Enterprise

## Use Cases

- Model complex domains (fleet management, property listings, course platforms)
- Build internal tools (custom dashboards, admin portals)
- Create dynamic websites from custom CRM data
- Sync custom data between HubSpot and external systems
- Build and sell integrations on the App Marketplace
- Automate complex business logic with custom-coded workflow actions
- Display live external data on CRM records with custom cards
- Build real-time event-driven integrations with webhooks

## Common Gotchas

- Custom object internal name cannot be changed after creation (also applies to properties)
- Deleting a custom object with records requires deleting all records first or using the recycle bin
- Custom objects cannot be added to sequences or email marketing directly (but can via workflows/deals)
- Custom object pipelines are Enterprise only
- Association labels are one-way — label a→b must be created separately from label b→a
- Webhook payloads are not guaranteed in order — process them idempotently
- OAuth refresh tokens expire after 6 months of inactivity (use refresh flow before expiry)
- API rate limits are per app, not per user — shared apps can hit limits faster
- Search API has a 5-second timeout — queries over large datasets may need pagination
- HubSpot does not support raw SQL against CRM data (use datasets in Operations Hub for SQL access)
- Custom-coded cards require React knowledge and deployment as a HubSpot app
- SDK auto-retry may not cover all error types — implement your own retry logic for production