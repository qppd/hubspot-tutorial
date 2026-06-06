# 8. Custom Objects, APIs & Developer Platform — Complete Tutorial

## Table of Contents
1. [Introduction to the Developer Platform](#introduction-to-the-developer-platform)
2. [Custom Objects — Complete Guide](#custom-objects--complete-guide)
3. [HubSpot REST API — Complete Guide](#hubspot-rest-api--complete-guide)
4. [GraphQL API — Complete Guide](#graphql-api--complete-guide)
5. [Webhooks — Complete Guide](#webhooks--complete-guide)
6. [Private Apps — Complete Guide](#private-apps--complete-guide)
7. [Public Apps & Marketplace — Complete Guide](#public-apps--marketplace--complete-guide)
8. [SDKs & Client Libraries — Complete Guide](#sdks--client-libraries--complete-guide)
9. [Custom Behaviors — Complete Guide](#custom-behaviors--complete-guide)
10. [HubSpot CLI — Complete Guide](#hubspot-cli--complete-guide)
11. [Limits That Matter](#limits-that-matter)
12. [Common Gotchas](#common-gotchas)
13. [Use Cases](#use-cases)

---

## Introduction to the Developer Platform

HubSpot's developer platform lets you extend the CRM beyond its built-in capabilities. You can create custom data models, integrate external systems, build custom UIs on CRM records, and publish apps to the HubSpot Marketplace.

### What You Can Build

- **Custom objects**: Model your business domain in HubSpot
- **API integrations**: Connect HubSpot to any external system
- **Private apps**: Internal integrations for your organization
- **Public apps**: Marketplace apps for all HubSpot users
- **Custom behaviors**: UI cards, workflow actions, chatbots, timeline events
- **Serverless functions**: Code that runs on HubSpot's edge network

### Developer Tools Overview

| Tool | Purpose | Access |
|------|---------|--------|
| **REST API** | CRUD operations on CRM objects | Any HubSpot account |
| **GraphQL API** | Query multiple objects in one request | Any HubSpot account |
| **Webhooks** | Receive real-time event notifications | Any HubSpot account |
| **Private Apps** | Internal API tokens with scoped permissions | Any HubSpot account |
| **Public Apps** | OAuth-based apps for marketplace | Developer account |
| **CLI** | Local development for Content Hub | npm install |
| **SDKs** | Client libraries (Python, Node.js, Ruby) | npm/pip/gem |
| **Design Tools** | Browser-based IDE for HubL, CSS, JS | Settings > Tools |
| **Custom Behaviors** | Cards, actions, bots (Enterprise) | Enterprise only |

---

## Custom Objects — Complete Guide

### What Are Custom Objects?

Custom objects extend HubSpot's data model beyond the 7 standard objects (Contact, Company, Deal, Ticket, Product, Line Item, Quote). If your business deals with entities that aren't directly supported — courses, vehicles, properties, projects, policies, events — you can create a custom object to represent them.

### Limits by Tier

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Custom objects | 10 | 10 | 10 | 200 |
| Records per custom object | 10,000 | 100,000 | 1,000,000 | Unlimited |
| Properties per custom object | 1,000 | 1,000 | 1,000 | 10,000 |
| Pipelines per custom object | — | — | — | 50 |

### Creating a Custom Object — Step-by-Step

**Via UI**:
1. **Settings** > **Data Management** > **Custom Objects**
2. Click "Create custom object"
3. **Name**: Singular (e.g., "Course") and Plural (e.g., "Courses")
4. **Internal name**: Auto-generated from singular (e.g., "course"). **Cannot be changed later.**
5. **Properties**: Add fields:
   - Name (single-line text, can be primary display)
   - Duration (number)
   - Level (dropdown: Beginner, Intermediate, Advanced)
   - Certificate Available (checkbox)
   - Price (number)
   - Description (multi-line text)
6. **Primary display property**: Which field shows in associations and search results
7. **Required properties**: Fields that must have a value
8. **Associations**: Link to other objects:
   - Contact → Course: "Enrolled in" / "Has student"
   - Course → Deal: "Targeted in" / "Targets course"
9. **Pipelines** (Enterprise): Enable pipeline tracking for this object
10. **Create**

**Via API**:
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

### Working with Custom Object Records

**Via API**:
```python
# Create record
client.crm.objects.basic_api.create(
  object_type="course",  # Internal name
  properties={
    "course_name": "Intro to Marketing",
    "duration_weeks": 8,
    "level": "beginner",
    "price": 499.00
  }
)

# Search records
client.crm.objects.search_api.do_search(
  object_type="course",
  filters=[{
    "property_name": "level",
    "operator": "EQ",
    "value": "advanced"
  }]
)

# Associate to contact
client.crm.associations.basic_api.create(
  from_object_type="contact",
  to_object_type="course",
  from_object_id=12345,
  to_object_id=67890,
  association_spec=[{ "association_category": "USER_DEFINED", "association_type_id": 36 }]
)
```

### Association Type IDs

When creating associations via API, you need the type ID:

| Association | Type ID |
|-------------|---------|
| Contact to Company | 1, 2 |
| Contact to Deal | 3, 4 |
| Contact to Ticket | 15, 16 |
| Company to Deal | 6, 7 |
| Deal to Line Item | 19, 20 |
| Custom Object to Contact | 36 (varies by label) |

Use `GET /crm/v3/associations/{objectType}/{objectType}/labels` to fetch type IDs.

### Custom Object Use Cases

| Industry | Custom Object | Records |
|----------|--------------|---------|
| Education | Course, Enrollment, Certificate | Students, classes |
| Real Estate | Property, Listing, Inspection | Buildings, tours |
| Healthcare | Patient, Appointment, Procedure | Visits, treatments |
| Manufacturing | Asset, Work Order, Part | Equipment, repairs |
| Nonprofit | Donation, Grant, Volunteer | Campaigns, hours |
| SaaS | Feature, Ticket, Environment | Releases, issues |

---

## HubSpot REST API — Complete Guide

### API Base URL

```
https://api.hubapi.com
```

### Authentication

**Option 1: Private App Token** (recommended for internal integrations)
```
Authorization: Bearer YOUR_PRIVATE_APP_TOKEN
```

**Option 2: OAuth 2.0** (for public apps)
```
Authorization: Bearer ACCESS_TOKEN
```

**Option 3: API Key** (legacy, being deprecated, not recommended for new apps)

### API Categories

| Category | Key Endpoints |
|----------|--------------|
| **CRM** | `/crm/v3/objects/contacts`, `/crm/v3/objects/companies`, `/crm/v3/objects/deals`, `/crm/v3/objects/tickets` |
| **CRM Search** | `/crm/v3/objects/{object}/search` (POST with filter groups) |
| **Associations** | `/crm/v3/associations/{from}/{to}/batch` |
| **Properties** | `/crm/v3/properties/{object}` |
| **Pipelines** | `/crm/v3/pipelines/{object}` |
| **Marketing** | `/marketing/v3/emails`, `/marketing/v3/forms` |
| **CMS** | `/cms/v3/pages`, `/cms/v3/url-redirects` |
| **Automation** | `/automation/v3/workflows` |
| **Webhooks** | `/webhooks/v3/subscriptions` |
| **Files** | `/files/v3/files` |
| **Engagements** | `/crm/v3/objects/notes`, `/crm/v3/objects/tasks`, `/crm/v3/objects/meetings`, `/crm/v3/objects/calls`, `/crm/v3/objects/emails` |
| **Commerce** | `/crm/v3/objects/invoices`, `/crm/v3/objects/payments`, `/crm/v3/objects/subscriptions` |

### CRM Search API (POST)

The search API is the most powerful way to retrieve CRM data:

```bash
POST /crm/v3/objects/contacts/search
{
  "filterGroups": [
    {
      "filters": [
        { "propertyName": "lifecyclestage", "operator": "EQ", "value": "customer" },
        { "propertyName": "firstname", "operator": "NEQ", "value": "" }
      ]
    },
    {
      "filters": [
        { "propertyName": "hs_lead_status", "operator": "EQ", "value": "WARM" }
      ]
    }
  ],
  "sorts": [
    { "propertyName": "createdate", "direction": "DESCENDING" }
  ],
  "properties": ["email", "firstname", "lastname", "company"],
  "limit": 50,
  "after": "next-page-cursor"
}
```

**Filter operators**:
| Operator | Description | Example |
|----------|-------------|---------|
| EQ | Equals | country EQ "US" |
| NEQ | Not equal | status NEQ "unsubscribed" |
| LT | Less than | amount LT 1000 |
| LTE | Less than or equal | score LTE 50 |
| GT | Greater than | createdate GT "2025-01-01" |
| GTE | Greater than or equal | amount GTE 50000 |
| BETWEEN | Between | amount BETWEEN 10000 50000 |
| IN | In list | stage IN "closedwon" "closedlost" |
| NOT_IN | Not in list | status NOT_IN "deleted" "spam" |
| HAS_PROPERTY | Has property value | HAS_PROPERTY email |
| NOT_HAS_PROPERTY | Property empty | NOT_HAS_PROPERTY phone |
| CONTAINS_TOKEN | Text contains | company CONTAINS_TOKEN "Acme" |
| NOT_CONTAINS_TOKEN | Text not contains | NOT_CONTAINS_TOKEN "test" |

### Batch Operations

Process up to 100 records in a single call:

```bash
# Batch create
POST /crm/v3/objects/contacts/batch/create
{
  "inputs": [
    { "properties": { "email": "alice@acme.com", "firstname": "Alice" } },
    { "properties": { "email": "bob@acme.com", "firstname": "Bob" } }
  ]
}

# Batch read
POST /crm/v3/objects/contacts/batch/read
{
  "inputs": [
    { "id": "12345" },
    { "id": "67890" }
  ],
  "properties": ["email", "firstname", "lastname"]
}

# Batch update
POST /crm/v3/objects/contacts/batch/update
{
  "inputs": [
    { "id": "12345", "properties": { "phone": "555-1234" } },
    { "id": "67890", "properties": { "phone": "555-5678" } }
  ]
}

# Batch upsert (create or update by unique identifier)
POST /crm/v3/objects/contacts/batch/upsert
{
  "inputs": [
    { "idProperty": "email", "id": "alice@acme.com", "properties": { "firstname": "Alice Updated" } }
  ]
}
```

### Rate Limits

| Plan | Requests per 10 seconds | Daily limit |
|------|------------------------|-------------|
| Free / Starter | 100 per 10s | 250,000 |
| Professional | 100 per 10s | 500,000 |
| Enterprise | 150 per 10s | 1,000,000+ |

**Rate limit headers** in API response:
- `X-HubSpot-RateLimit-Interval-Milliseconds`: Reset window
- `X-HubSpot-RateLimit-Per-Second`: Limit per second
- `X-HubSpot-RateLimit-Remaining`: Remaining calls

### Error Handling

| HTTP Code | Meaning | Action |
|-----------|---------|--------|
| 200 | Success | N/A |
| 204 | Success (no content) | N/A |
| 400 | Bad request | Check request body and parameters |
| 401 | Unauthorized | Refresh token, check permissions |
| 403 | Forbidden | Token doesn't have required scope |
| 404 | Not found | Record or endpoint doesn't exist |
| 409 | Conflict | Duplicate detected, version conflict |
| 429 | Rate limited | Implement exponential backoff |
| 500 | Server error | Retry with backoff |

---

## GraphQL API — Complete Guide

### What GraphQL Does

GraphQL lets you fetch related data in a single request, reducing roundtrips:

**REST approach**: 
1. GET contact → 2. GET contact's deals → 3. GET deal's company → 3 API calls

**GraphQL approach**: 
```graphql
{
  contact(id: "12345") {
    email
    firstname
    lastname
    deals {
      results {
        id
        dealname
        amount
        company {
          name
          domain
        }
      }
    }
  }
}
```

### Endpoint

```
https://api.hubapi.com/api/graphql
```

### Query Structure

```graphql
query {
  CRM {
    contact(uniqueIdentifier: "email", identifierValue: "jane@example.com") {
      firstname
      lastname
      email
      phone
      company {
        name
        domain
        industry
        deals {
          results {
            dealname
            amount
            dealstage
          }
        }
      }
    }
  }
}
```

### Limitations

- **Read-only**: No mutations (create, update, delete)
- **Max 5 objects** per query
- **Max depth**: 3 levels of nested associations
- **Performance**: Not recommended for bulk queries; use search API for that

---

## Webhooks — Complete Guide

### What Webhooks Do

Webhooks send real-time HTTP POST requests to your server when events happen in HubSpot.

### Supported Event Types

| Event | Description |
|-------|-------------|
| `contact.creation` | Contact created |
| `contact.propertyChange` | Specific property changed |
| `contact.deletion` | Contact deleted |
| `company.creation` | Company created |
| `company.propertyChange` | Company property changed |
| `deal.creation` | Deal created |
| `deal.stageChange` | Deal moved to new stage |
| `deal.propertyChange` | Deal property changed |
| `ticket.creation` | Ticket created |
| `ticket.propertyChange` | Ticket property changed |
| `form.submission` | Form submitted |
| `conversation.creation` | New conversation |

### Setting Up a Webhook — Step-by-Step

1. **Settings** > **Integrations** > **Webhooks**
2. Click "Create webhook subscription"
3. **Event type**: Choose from the list above
4. **Target URL**: `https://your-server.com/webhooks/hubspot`
5. **Secret**: Create a strong secret for HMAC verification
6. **Active**: Enable the subscription
7. HubSpot starts POSTing to your endpoint

### Verifying Webhook Signatures

```javascript
// Node.js verification
const crypto = require('crypto');

function verifyWebhook(req) {
  const signature = req.headers['x-hubspot-signature-v3'];
  const timestamp = req.headers['x-hubspot-request-timestamp'];
  const body = JSON.stringify(req.body);
  const secret = process.env.HUBSPOT_WEBHOOK_SECRET;
  
  // Check timestamp is recent (within 5 minutes)
  const now = Math.floor(Date.now() / 1000);
  if (Math.abs(now - parseInt(timestamp)) > 300) {
    return false; // Too old, possible replay attack
  }
  
  const expectedSig = crypto
    .createHmac('sha256', secret)
    .update(body + timestamp)
    .digest('hex');
  
  return crypto.timingSafeEqual(
    Buffer.from(signature),
    Buffer.from(expectedSig)
  );
}
```

```python
# Python verification
import hmac
import hashlib
import json

def verify_webhook(request_body, headers, secret):
    signature = headers.get('x-hubspot-signature-v3')
    timestamp = headers.get('x-hubspot-request-timestamp')
    
    body = json.dumps(request_body, separators=(',', ':'))
    source = body + timestamp
    expected = hmac.new(
        secret.encode('utf-8'),
        source.encode('utf-8'),
        hashlib.sha256
    ).hexdigest()
    
    return hmac.compare_digest(signature, expected)
```

### Webhook Payload Example

```json
{
  "subscriptionId": 123456,
  "portalId": 654321,
  "occurredAt": 1749200000000,
  "subscriptionType": "contact.propertyChange",
  "attemptNumber": 0,
  "objectId": 123456789,
  "propertyName": "lifecyclestage",
  "propertyValue": "customer",
  "changeSource": "WORKFLOW"
}
```

### Retry Policy

- 3 retry attempts
- Exponential backoff (1 min, 5 min, 30 min)
- Timeout: 5 seconds
- If all retries fail, event is logged in webhook error history

---

## Private Apps — Complete Guide

### What Are Private Apps?

Private apps are internal-use integrations authenticated with scoped API tokens. No OAuth flow required — you generate a token and use it directly.

### Creating a Private App

1. **Settings** > **Integrations** > **Private Apps**
2. Click "Create private app"
3. **Name**: "Sales Data Enrichment Tool"
4. **Description**: What this app does
5. **Scopes**: Select API permissions
   - `crm.objects.contacts.read` — Read contacts
   - `crm.objects.contacts.write` — Create/update contacts
   - `crm.objects.companies.read` — Read companies
   - `crm.objects.deals.read` — Read deals
   - `crm.objects.deals.write` — Create/update deals
   - `automation.workflows.read` — Read workflows
   - `settings.users.read` — Read user info
   - And many more...
6. **Create** → Token is generated (show once, save securely)

### Scope Categories

| Scope Prefix | Resources |
|-------------|-----------|
| `crm.objects.contacts` | Contact CRUD |
| `crm.objects.companies` | Company CRUD |
| `crm.objects.deals` | Deal CRUD |
| `crm.objects.line_items` | Line items |
| `crm.objects.quotes` | Quotes |
| `crm.schemas.custom_objects` | Custom objects |
| `crm.associations` | Associations |
| `marketing.email` | Email marketing |
| `automation.workflows` | Workflows |
| `conversations` | Conversations, chat |
| `files` | File uploads |
| `oauth` | OAuth |

### Token Management

- **View**: Last used, created date, scopes
- **Rotate**: Generate new token without downtime
- **Revoke**: Immediately invalidate a token
- **Audit log**: See which actions were performed by this app

---

## SDKs & Client Libraries — Complete Guide

### Python SDK

**Installation**:
```bash
pip install hubspot-api-client
```

**Usage**:
```python
from hubspot import HubSpot
from hubspot.crm.contacts import SimplePublicObjectInput
from hubspot.crm.contacts.exceptions import ApiException

client = HubSpot(access_token="YOUR_TOKEN")

# Create a contact
try:
    contact = client.crm.contacts.basic_api.create(
        simple_public_object_input=SimplePublicObjectInput(
            properties={
                "email": "jane@example.com",
                "firstname": "Jane",
                "lastname": "Doe",
                "phone": "555-123-4567",
                "company": "Acme Corp"
            }
        )
    )
    print(f"Created contact: {contact.id}")
except ApiException as e:
    print(f"Exception: {e}")

# Search contacts
from hubspot.crm.contacts import Filter, FilterGroup, PublicObjectSearchRequest

filter_ = Filter(property_name="lifecyclestage", operator="EQ", value="customer")
filter_group = FilterGroup(filters=[filter_])
search_request = PublicObjectSearchRequest(
    filter_groups=[filter_group],
    properties=["email", "firstname", "lastname"],
    limit=50
)

results = client.crm.contacts.search_api.do_search(
    public_object_search_request=search_request
)

for contact in results.results:
    print(f"{contact.properties['firstname']} {contact.properties['lastname']} - {contact.properties['email']}")

# Update a contact
client.crm.contacts.basic_api.update(
    contact_id=12345,
    simple_public_object_input=SimplePublicObjectInput(
        properties={"phone": "555-987-6543"}
    )
)

# Delete a contact
client.crm.contacts.basic_api.archive(contact_id=12345)
```

### Node.js SDK

**Installation**:
```bash
npm install @hubspot/api-client
```

**Usage**:
```javascript
const hubspot = require('@hubspot/api-client');

const client = new hubspot.Client({
  accessToken: 'YOUR_TOKEN'
});

// Create contact
const contact = await client.crm.contacts.basicApi.create({
  properties: {
    email: 'john@example.com',
    firstname: 'John',
    lastname: 'Smith',
    company: 'Tech Corp'
  }
});

// Search
const searchResponse = await client.crm.contacts.searchApi.doSearch({
  filterGroups: [{
    filters: [{
      propertyName: 'lifecyclestage',
      operator: 'EQ',
      value: 'lead'
    }]
  }],
  properties: ['email', 'firstname', 'lastname'],
  limit: 50
});

// Batch read
const batchResponse = await client.crm.contacts.batchApi.read({
  inputs: [{ id: '12345' }, { id: '67890' }],
  properties: ['email', 'firstname']
});
```

---

## Custom Behaviors (Enterprise) — Complete Guide

### Custom-Coded Cards

React or plain JavaScript cards that appear on CRM record pages:

**Use cases**:
- Show real-time data from external systems on contact records
- Embed charts or dashboards on company records
- Display deal health scores with visual indicators
- Show customer support history from external systems

**Building a card**:
1. Design Tools → Create new → Custom behavior
2. Select "Custom-coded CRM card"
3. Choose object: Contact, Company, Deal, Ticket, or Custom Object
4. Write card UI with JavaScript (React, Preact, or vanilla JS)
5. Access HubSpot SDK for CRM actions:
   ```javascript
   // Get current object ID
   const objectId = window.hsSDK.context.objectId;
   
   // Get object data
   const properties = window.hsSDK.context.properties;
   
   // Open a record
   window.hsSDK.records.open('contact', 12345);
   
   // Navigate
   window.hsSDK.navigation.open('/contacts/12345');
   ```

### Custom-Coded Actions

Workflow actions written in Node.js or Python:
- Deployed as serverless functions
- Triggered by CRM events in workflows
- Full access to HubSpot API

### Custom-Coded Bots

Chatbot actions with custom logic:
- Process user input
- Query external systems
- Make decisions based on CRM data
- Create tickets, update records, send messages

### Custom-Coded Timeline Events

Display external events on CRM timelines:
- Show deployment events from CI/CD
- Log product usage milestones
- Track email opens from external ESP
- Show shipping status updates

---

## HubSpot CLI — Complete Guide

### Installation

```bash
npm install -g @hubspot/cli
```

### Authentication

```bash
hs init
# → Follow prompts to authenticate with your portal
```

### Key Commands

```bash
# Upload file(s)
hs upload local/path remote/path

# Download file(s)
hs fetch remote/path local/path

# Watch for changes and auto-upload
hs watch local/path remote/path

# Create scaffolds
hs create theme my-theme-name
hs create template my-template
hs create module my-module
hs create react-app my-app

# List assets
hs list remote/path

# Remove file
hs remove remote/path/file.html

# Open Design Tools in browser
hs open

# Get portal info
hs info

# See available commands
hs help
```

---

## Limits That Matter

| Resource | Free | Starter | Pro | Enterprise |
|----------|------|---------|-----|------------|
| Custom objects | 10 | 10 | 10 | 200 |
| Custom object records | 10k/obj | 100k/obj | 1M/obj | Unlimited |
| Properties per object | 1,000 | 1,000 | 1,000 | 10,000 |
| Custom object pipelines | — | — | — | 50 |
| API rate limit | 100/10s | 100/10s | 100/10s | 150/10s |
| Daily API calls | 250k | 500k | 1M | Varies |
| Batch API size | 100 | 100 | 100 | 100 |
| Webhook timeout | 5s | 5s | 5s | 5s |
| Webhook retries | 3 | 3 | 3 | 3 |
| Custom-coded cards | — | — | — | Unlimited |
| Serverless functions | — | — | 10 | 100 |

---

## Common Gotchas

### 1. Property Internal Names
Once created, a property's internal name is **permanent**. You cannot rename it. Always use descriptive, lowercase, underscore-separated names: `preferred_contact_time` not `prefTime` or `Preferred Time`.

### 2. Custom Object Deletion
To delete a custom object with records, you must first delete or reassign all records. HubSpot provides a recycle bin, but permanently deleting a custom object schema is irreversible.

### 3. API Rate Limits
Rate limits are per-app, not per-user. If a public app makes requests on behalf of multiple users, they all share the same rate limit. Implement client-side throttling.

### 4. Search API Timeout
Search queries have a 5-second timeout. For large datasets (>1M records), use specific filters to narrow results. Avoid `HAS_PROPERTY` or `NOT_HAS_PROPERTY` on large sets.

### 5. OAuth Token Expiry
Refresh tokens expire after 6 months of inactivity. Implementation should include a refresh flow that runs periodically, not only on expiry.

### 6. Webhook Ordering
Events are NOT guaranteed to arrive in order. A later event may arrive before an earlier one. Process webhooks idempotently using the `occurredAt` timestamp for ordering if needed.

### 7. SDK Error Handling
The SDK's auto-retry doesn't cover all error scenarios. For production, implement your own retry logic with exponential backoff, especially for 429 (rate limit) errors.

### 8. Custom Object in Workflows
Custom objects can be used in workflows (triggers and actions), but NOT directly in sequences or email marketing. You must associate the custom object through a deal or contact to use those features.