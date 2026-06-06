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

---

## API Integration Tutorials

### Tutorial 1: Building a Data Import Script (Python)

**Goal**: Import 10,000 contacts from an external system into HubSpot using the batch API for efficiency.

```python
import hubspot
from hubspot.crm.contacts import BatchInputSimplePublicObjectInput
import csv
import time

client = HubSpot(access_token="YOUR_PRIVATE_APP_TOKEN")

def batch_import_contacts(csv_path, batch_size=100):
    """Import contacts from CSV using batch API."""
    
    # Read contacts from CSV
    contacts = []
    with open(csv_path, 'r') as f:
        reader = csv.DictReader(f)
        for row in reader:
            contacts.append({
                "email": row["email"],
                "firstname": row["first_name"],
                "lastname": row["last_name"],
                "phone": row["phone"],
                "company": row["company"],
                "jobtitle": row["job_title"],
                "website": row["website"]
            })
    
    print(f"Read {len(contacts)} contacts from CSV")
    
    # Process in batches of 100
    successful = 0
    errors = 0
    
    for i in range(0, len(contacts), batch_size):
        batch = contacts[i:i + batch_size]
        
        try:
            batch_input = BatchInputSimplePublicObjectInput(
                inputs=[{
                    "properties": contact
                } for contact in batch]
            )
            
            response = client.crm.contacts.batch_api.create(
                batch_input_simple_public_object_input=batch_input
            )
            
            successful += len(response.results)
            print(f"Batch {i//batch_size + 1}: Created {len(response.results)} contacts")
            
        except Exception as e:
            errors += len(batch)
            print(f"Batch {i//batch_size + 1} failed: {e}")
        
        # Rate limiting: wait if needed
        if (i // batch_size) % 5 == 0:
            time.sleep(1)  # Stay within 100 req/10s limit
    
    print(f"\nImport complete: {successful} created, {errors} errors")
    return successful, errors

# Usage
batch_import_contacts("contacts_to_import.csv")
```

### Tutorial 2: Building a Webhook Receiver (Flask)

**Goal**: Receive HubSpot webhooks, verify signatures, and process events.

```python
from flask import Flask, request, jsonify
import hmac
import hashlib
import json
from datetime import datetime

app = Flask(__name__)
WEBHOOK_SECRET = "your-hubspot-webhook-secret"

def verify_signature(payload_body, timestamp, signature):
    """Verify HMAC-SHA256 signature from HubSpot."""
    source = payload_body + timestamp
    expected = hmac.new(
        WEBHOOK_SECRET.encode('utf-8'),
        source.encode('utf-8'),
        hashlib.sha256
    ).hexdigest()
    return hmac.compare_digest(signature, expected)

def check_timestamp(timestamp):
    """Prevent replay attacks by checking timestamp freshness."""
    now = int(datetime.utcnow().timestamp())
    event_time = int(timestamp)
    return abs(now - event_time) < 300  # 5 minute window

def process_contact_creation(event):
    """Handle new contact created."""
    contact_id = event['objectId']
    print(f"New contact created: {contact_id}")
    # Your logic here: enrich, sync, notify, etc.

def process_deal_stage_change(event):
    """Handle deal stage change."""
    deal_id = event['objectId']
    new_stage = event['propertyValue']
    print(f"Deal {deal_id} moved to stage: {new_stage}")
    # Your logic here: trigger external workflow, notify, etc.

@app.route("/webhooks/hubspot", methods=["POST"])
def hubspot_webhook():
    """Main webhook endpoint."""
    
    # Extract headers
    signature = request.headers.get("X-HubSpot-Signature-v3")
    timestamp = request.headers.get("X-HubSpot-Request-Timestamp")
    body = request.data.decode("utf-8")
    
    # Verify
    if not signature or not timestamp:
        return jsonify({"error": "Missing headers"}), 401
    
    if not verify_signature(body, timestamp, signature):
        return jsonify({"error": "Invalid signature"}), 401
    
    if not check_timestamp(timestamp):
        return jsonify({"error": "Stale timestamp"}), 401
    
    # Process events (HubSpot delivers batches)
    events = request.json
    if not isinstance(events, list):
        events = [events]
    
    for event in events:
        event_type = event.get("subscriptionType")
        try:
            if event_type == "contact.creation":
                process_contact_creation(event)
            elif event_type == "deal.stageChange":
                process_deal_stage_change(event)
            elif event_type == "ticket.creation":
                process_ticket_creation(event)
            # Add more event types as needed
        except Exception as e:
            print(f"Error processing {event_type}: {e}")
            # Log but don't fail the whole batch
    
    # Always return 200 to acknowledge receipt
    return jsonify({"status": "ok"}), 200

@app.route("/health", methods=["GET"])
def health_check():
    """Health check endpoint for monitoring."""
    return jsonify({"status": "healthy"})

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=8080, ssl_context="adhoc")
```

### Tutorial 3: Complete OAuth 2.0 Implementation (Node.js)

**Goal**: Full OAuth flow for a public HubSpot app with token refresh.

```javascript
const express = require('express');
const hubspot = require('@hubspot/api-client');
const axios = require('axios');

const app = express();
const CLIENT_ID = 'YOUR_CLIENT_ID';
const CLIENT_SECRET = 'YOUR_CLIENT_SECRET';
const REDIRECT_URI = 'https://your-app.com/oauth/callback';
const SCOPES = ['crm.objects.contacts.read', 'crm.objects.contacts.write'];

// In-memory token store (use database in production)
const tokenStore = {};

// Step 1: Redirect user to HubSpot authorization page
app.get('/oauth/authorize', (req, res) => {
    const authUrl = 'https://app.hubspot.com/oauth/authorize' +
        `?client_id=${CLIENT_ID}` +
        `&redirect_uri=${REDIRECT_URI}` +
        `&scope=${SCOPES.join(' ')}` +
        `&state=${generateRandomState()}`; // CSRF protection
    
    res.redirect(authUrl);
});

// Step 2: Handle OAuth callback
app.get('/oauth/callback', async (req, res) => {
    const { code, state } = req.query;
    
    // Verify state to prevent CSRF
    if (!verifyState(state)) {
        return res.status(401).send('Invalid state parameter');
    }
    
    try {
        // Exchange code for tokens
        const response = await axios.post(
            'https://api.hubapi.com/oauth/v1/token',
            new URLSearchParams({
                grant_type: 'authorization_code',
                client_id: CLIENT_ID,
                client_secret: CLIENT_SECRET,
                redirect_uri: REDIRECT_URI,
                code: code
            }),
            { headers: { 'Content-Type': 'application/x-www-form-urlencoded' } }
        );
        
        const { access_token, refresh_token, expires_in } = response.data;
        
        // Store tokens securely
        const userId = extractUserId(state);
        tokenStore[userId] = {
            accessToken: access_token,
            refreshToken: refresh_token,
            expiresAt: Date.now() + (expires_in * 1000)
        };
        
        // Create HubSpot client with the access token
        const hubspotClient = new hubspot.Client({
            accessToken: access_token
        });
        
        // Fetch user's portal info
        const portalInfo = await hubspotClient.apiRequest({
            method: 'GET',
            path: '/account-info/v3/details'
        });
        
        res.json({
            message: 'Authorization successful',
            portal: portalInfo.portalId
        });
        
    } catch (error) {
        console.error('OAuth error:', error.response?.data || error.message);
        res.status(500).send('Authorization failed');
    }
});

// Step 3: Refresh token middleware
async function getValidToken(userId) {
    const token = tokenStore[userId];
    if (!token) throw new Error('No token found');
    
    // Check if token is expired (with 5 minute buffer)
    if (Date.now() > token.expiresAt - 300000) {
        try {
            const response = await axios.post(
                'https://api.hubapi.com/oauth/v1/token',
                new URLSearchParams({
                    grant_type: 'refresh_token',
                    client_id: CLIENT_ID,
                    client_secret: CLIENT_SECRET,
                    refresh_token: token.refreshToken
                }),
                { headers: { 'Content-Type': 'application/x-www-form-urlencoded' } }
            );
            
            const { access_token, refresh_token, expires_in } = response.data;
            
            // Update stored tokens
            token.accessToken = access_token;
            token.refreshToken = refresh_token;
            token.expiresAt = Date.now() + (expires_in * 1000);
            
        } catch (error) {
            console.error('Token refresh failed:', error.message);
            throw new Error('Token refresh failed');
        }
    }
    
    return token.accessToken;
}

// Helper: API route using HubSpot client
app.get('/api/contacts', async (req, res) => {
    try {
        const userId = req.query.userId; // Get from session/auth
        const token = await getValidToken(userId);
        
        const hubspotClient = new hubspot.Client({ accessToken: token });
        
        const contacts = await hubspotClient.crm.contacts.basicApi.getPage(
            50, undefined, ['email', 'firstname', 'lastname']
        );
        
        res.json(contacts.results);
        
    } catch (error) {
        res.status(500).json({ error: error.message });
    }
});

app.listen(3000, () => {
    console.log('OAuth app running on port 3000');
});
```

### Tutorial 4: Search API — Advanced Query Examples

**Use Case 1: Find contacts who opened a specific email AND visited pricing page**

```python
import hubspot
from hubspot.crm.contacts import ApiException, PublicObjectSearchRequest, Filter, FilterGroup

client = HubSpot(access_token="YOUR_TOKEN")

# Build search request
search_request = PublicObjectSearchRequest(
    filter_groups=[
        FilterGroup(filters=[
            Filter(property_name="hs_email_click", operator="GT", value="0"),
            Filter(property_name="hs_analytics_last_visit_timestamp", operator="GT", 
                   value="2025-01-01")
        ]),
        # Second group (OR condition)
        FilterGroup(filters=[
            Filter(property_name="lifecyclestage", operator="EQ", value="opportunity")
        ])
    ],
    properties=["email", "firstname", "lastname", "company", "hs_email_click"],
    sorts=[{"property_name": "hs_email_click", "direction": "DESCENDING"}],
    limit=100
)

results = client.crm.contacts.search_api.do_search(
    public_object_search_request=search_request
)

print(f"Found {results.total} matching contacts")
```

**Use Case 2: Find companies with no recent activity**

```python
search_request = PublicObjectSearchRequest(
    filter_groups=[FilterGroup(filters=[
        Filter(property_name="hs_last_activity_date", operator="LT",
               value=datetime.now() - timedelta(days=90)),
        Filter(property_name="lifecyclestage", operator="NEQ", value="customer"),
        Filter(property_name="hs_num_open_deals", operator="EQ", value="0")
    ])],
    properties=["name", "domain", "hs_last_activity_date"],
    limit=200
)
```

**Use Case 3: Complex deal pipeline analysis**

```python
# Deals created in specific pipeline, with amounts over threshold, 
# NOT in closed stages, sorted by amount descending
search_request = PublicObjectSearchRequest(
    filter_groups=[FilterGroup(filters=[
        Filter(property_name="pipeline", operator="EQ", value="default"),
        Filter(property_name="amount", operator="GTE", value="10000"),
        Filter(property_name="dealstage", operator="NOT_IN", 
               value=["closedwon", "closedlost"]),
        Filter(property_name="createdate", operator="GTE", 
               value="2025-06-01")
    ])],
    properties=["dealname", "amount", "dealstage", "closedate", "hubspot_owner_id"],
    sorts=[{"property_name": "amount", "direction": "DESCENDING"}],
    limit=50
)
```

### Advanced Search with Associated Objects
Search across multiple objects and return associated data:

```python
# Find contacts with deals > $50k that were created this quarter
search_request = PublicObjectSearchRequest(
    filter_groups=[FilterGroup(filters=[
        Filter(property_name="createdate", operator="GTE", 
               value="2025-07-01"),
        Filter(property_name="associated_deals.dealstage", 
               operator="NOT_IN", value=["closedlost"]),
    ])],
    # Include associations in the response
    properties=["email", "firstname", "lastname", "associated_deals"],
    limit=100
)
```

### Search Performance Tips
1. **Use specific filters first**: Narrow results before applying complex conditions
2. **Limit returned properties**: Only request properties you need — reduces response time
3. **Bulk search**: For >10K results, paginate with `after` parameter
4. **Avoid `NOT_HAS_PROPERTY`**: This is slow — use `HAS_PROPERTY` with positive logic instead
5. **Combine `AND` groups**: Multiple filter groups = OR logic, filters within a group = AND
6. **Date ranges**: Use GTE/LTE with dates rather than BETWEEN for better performance

---

## Tutorial: Building a Custom Object-Based Application

**Goal**: Build a complete "Project Management" module in HubSpot using custom objects, associations, workflows, and dashboards.

**Step 1: Design the Data Model**

Objects and relationships:
```
Company 1──M Project M──M Contact
                 │
                 M
                 │
              Task (custom object)
```

**Custom Object 1: Project**
- Properties:
  - `project_name` (single-line text) — Project name
  - `project_status` (dropdown: Planning, Active, On Hold, Completed, Cancelled)
  - `start_date` (date) — Project start
  - `deadline` (date) — Project deadline
  - `budget` (number) — Project budget
  - `description` (multi-line text) — Project description
  - `priority` (dropdown: Low, Medium, High, Critical)
  - `completion_percentage` (number 0-100) — Progress indicator

**Custom Object 2: Task**
- Properties:
  - `task_name` (single-line text) — Task title
  - `task_status` (dropdown: Not Started, In Progress, In Review, Done)
  - `due_date` (date) — Task due date
  - `assigned_to` (single-line text) — Person responsible
  - `estimated_hours` (number) — Time estimate
  - `actual_hours` (number) — Actual time spent
  - `notes` (multi-line text) — Task notes

**Associations:**
- Project → Company (many-to-one): "Project for company" / "Has project"
- Project → Contact (many-to-many): "Project member" / "Member of"
- Project → Task (one-to-many): "Project task" / "Parent project"

**Step 2: Create Custom Objects in HubSpot**
1. **Settings** > **Data Management** > **Custom Objects** > Create custom object
2. Create "Project" object with all properties above
3. Create "Task" object with all properties above
4. Set up associations between Project, Company, Contact, and Task

**Step 3: Build a Project Creation Workflow**
1. Trigger: New deal closed won (deal stage = "Closed Won")
2. Actions:
   - Create Project record: Name = "Onboarding: {{ deal.name }}"
   - Associate Project to Company (from deal's associated company)
   - Associate Project to Contact (from deal's primary contact)
   - Set Project.start_date = Today
   - Set Project.deadline = Today + 30 days
   - Create Tasks for the project:
     - Task 1: "Welcome call" — Due in 2 days
     - Task 2: "System setup" — Due in 5 days
     - Task 3: "Training session" — Due in 14 days
     - Task 4: "Go-live review" — Due in 28 days
3. Send notification to project manager about new project created

**Step 4: Build Progress Tracking Dashboard**
1. **Reports** > **Dashboards** > Create "Project Portfolio Dashboard"
2. Add reports:
   - **Project Status Distribution** — Pie chart by `project_status`
   - **Active Projects by Priority** — Bar chart: count by `priority` where status = Active
   - **Projects Nearing Deadline** — Table: projects where `deadline < 7 days` and `completion_percentage < 80%`
   - **Overdue Tasks** — Table: tasks where `due_date < Today` and `task_status ≠ Done`
   - **Project Budget vs. Actual** — Calculated report comparing budget to sum of estimated hours
   - **Workload by Assignee** — Bar chart: count of tasks grouped by `assigned_to` where task_status ≠ Done

**Step 5: Build Automation for Task Management**
1. **Overdue task notification**: When task due date passes and status ≠ Done → notify assignee
2. **Project completion**: When all tasks = Done → set Project.completion_percentage = 100
3. **Project status auto-update**: When deadline passes and status = Planning/Active → prompt manager to update
4. **Weekly digest**: Every Monday → send email with this week's tasks due

---

## Tutorial: Building a Webhook Integration with Flask

**Goal**: Create a webhook endpoint in Flask that receives HubSpot notifications and processes them.

**Prerequisites**: Basic Python knowledge, Flask installed.

**Step 1: Create Flask Webhook Receiver**
```python
from flask import Flask, request, jsonify
import hashlib
import hmac
import json

app = Flask(__name__)

# HubSpot webhook secret from Settings > Integrations > Webhooks
WEBHOOK_SECRET = "your-hubspot-webhook-secret"

def verify_signature(payload, signature_header):
    """Verify HubSpot webhook signature"""
    if not signature_header:
        return False
    expected = hashlib.sha256(
        WEBHOOK_SECRET.encode() + payload.encode()
    ).hexdigest()
    return hmac.compare_digest(f"sha256={expected}", signature_header)

@app.route('/webhook/hubspot', methods=['POST'])
def hubspot_webhook():
    # Verify the request is from HubSpot
    signature = request.headers.get('X-HubSpot-Signature-v3', '')
    payload = request.data.decode('utf-8')
    
    if not verify_signature(payload, signature):
        return jsonify({"error": "Invalid signature"}), 401
    
    events = request.json
    for event in events:
        event_type = event.get('subscriptionType')
        object_id = event.get('objectId')
        
        if event_type == 'contact.creation':
            print(f"New contact created: {object_id}")
            # Process new contact
        elif event_type == 'deal.propertyChange':
            print(f"Deal {object_id} property changed")
            property_name = event.get('propertyName')
            new_value = event.get('propertyValue')
            # React to property change
            
    return jsonify({"status": "ok"}), 200

if __name__ == '__main__':
    app.run(port=5000, debug=True)
```

**Step 2: Deploy Webhook**
1. Deploy Flask app to a public URL (Heroku, Railway, VPS, or ngrok for testing)
2. **Settings** > **Integrations** > **Webhooks** > Create webhook
3. Set URL: `https://your-domain.com/webhook/hubspot`
4. Subscribe to events:
   - Contact creation, property changes
   - Deal stage changes, deal property changes
   - Ticket creation, ticket status changes
5. Copy webhook secret and add to Flask config

**Step 3: Real-World Usage — Auto Slack Notifications**
```python
import requests

SLACK_WEBHOOK = "https://hooks.slack.com/services/..."

@app.route('/webhook/hubspot', methods=['POST'])
def hubspot_webhook():
    events = request.json
    for event in events:
        if event.get('subscriptionType') == 'deal.propertyChange':
            if event.get('propertyName') == 'dealstage':
                new_stage = event.get('propertyValue')
                deal_id = event.get('objectId')
                
                # Get deal details from HubSpot API
                deal_data = get_deal(deal_id)
                
                message = {
                    "text": f"🚀 *Deal Update*\n"
                            f"*Deal*: {deal_data['dealname']}\n"
                            f"*Stage*: Changed to {new_stage}\n"
                            f"*Amount*: ${deal_data.get('amount', 'N/A')}\n"
                            f"*Owner*: {deal_data.get('hubspot_owner_id', 'Unassigned')}"
                }
                requests.post(SLACK_WEBHOOK, json=message)
    
    return jsonify({"status": "ok"}), 200
```

---

## Tutorial: Implementing OAuth 2.0 in a Node.js App

**Goal**: Build a Node.js app that authenticates with HubSpot using OAuth 2.0 and makes API calls.

**Prerequisites**: Node.js installed, HubSpot app created in Developer Portal.

**Step 1: Create HubSpot App**
1. Go to [developers.hubspot.com](https://developers.hubspot.com)
2. **Create app** → Name: "My CRM Integration"
3. Add scopes:
   - `crm.objects.contacts.read`
   - `crm.objects.contacts.write`
   - `crm.objects.deals.read`
   - `crm.schemas.custom_objects.read`
4. Set redirect URL: `http://localhost:3000/oauth/callback`
5. Copy Client ID and Client Secret

**Step 2: Express OAuth Flow**
```javascript
const express = require('express');
const axios = require('axios');
const app = express();

const CLIENT_ID = 'your-client-id';
const CLIENT_SECRET = 'your-client-secret';
const REDIRECT_URI = 'http://localhost:3000/oauth/callback';
const SCOPES = 'crm.objects.contacts.read crm.objects.contacts.write';

// Step 1: Redirect user to HubSpot authorization URL
app.get('/oauth/authorize', (req, res) => {
  const authUrl = `https://app.hubspot.com/oauth/authorize?client_id=${CLIENT_ID}&redirect_uri=${REDIRECT_URI}&scope=${SCOPES}`;
  res.redirect(authUrl);
});

// Step 2: Handle callback with authorization code
app.get('/oauth/callback', async (req, res) => {
  const { code } = req.query;
  
  try {
    // Exchange code for tokens
    const tokenResponse = await axios.post(
      'https://api.hubapi.com/oauth/v1/token',
      new URLSearchParams({
        grant_type: 'authorization_code',
        client_id: CLIENT_ID,
        client_secret: CLIENT_SECRET,
        redirect_uri: REDIRECT_URI,
        code: code
      }).toString(),
      { headers: { 'Content-Type': 'application/x-www-form-urlencoded' } }
    );

    const { access_token, refresh_token, expires_in } = tokenResponse.data;
    
    // Store tokens securely (database recommended)
    // For demo: store in memory
    global.accessToken = access_token;
    global.refreshToken = refresh_token;
    
    res.send('✅ Authorization successful! You can now use the API.');
    
    // Schedule token refresh
    setTimeout(refreshAccessToken, (expires_in - 300) * 1000);
    
  } catch (error) {
    console.error('OAuth error:', error.response?.data || error.message);
    res.status(500).send('Authorization failed');
  }
});

// Step 3: Refresh access token
async function refreshAccessToken() {
  try {
    const response = await axios.post(
      'https://api.hubapi.com/oauth/v1/token',
      new URLSearchParams({
        grant_type: 'refresh_token',
        client_id: CLIENT_ID,
        client_secret: CLIENT_SECRET,
        refresh_token: global.refreshToken
      }).toString(),
      { headers: { 'Content-Type': 'application/x-www-form-urlencoded' } }
    );
    
    global.accessToken = response.data.access_token;
    global.refreshToken = response.data.refresh_token;
    console.log('Token refreshed successfully');
    
    // Schedule next refresh
    setTimeout(refreshAccessToken, (response.data.expires_in - 300) * 1000);
    
  } catch (error) {
    console.error('Token refresh failed:', error.message);
  }
}

// Step 4: Make API calls
app.get('/api/contacts', async (req, res) => {
  try {
    const response = await axios.get(
      'https://api.hubapi.com/crm/v3/objects/contacts?limit=10',
      { headers: { 'Authorization': `Bearer ${global.accessToken}` } }
    );
    res.json(response.data);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

---

## Tutorial: Batch Import/Export with Python

**Goal**: Build a Python script that batch imports contacts and exports deal data from HubSpot.

**Step 1: Batch Import Contacts**
```python
import requests
import csv
import time
from typing import List, Dict

API_KEY = "YOUR_PRIVATE_APP_ACCESS_TOKEN"
BASE_URL = "https://api.hubapi.com"
HEADERS = {
    "Authorization": f"Bearer {API_KEY}",
    "Content-Type": "application/json"
}

def create_batch_import(filename: str) -> str:
    """Create a batch import from CSV and return import ID"""
    with open(filename, 'rb') as f:
        files = {'files': f}
        response = requests.post(
            f"{BASE_URL}/crm/v3/imports",
            headers={"Authorization": f"Bearer {API_KEY}"},
            files={'importFile': (filename, f, 'text/csv')}
        )
    
    if response.status_code != 200:
        raise Exception(f"Import failed: {response.text}")
    
    return response.json()['id']

def check_import_status(import_id: str) -> Dict:
    """Check the status of a batch import"""
    response = requests.get(
        f"{BASE_URL}/crm/v3/imports/{import_id}",
        headers=HEADERS
    )
    return response.json()

def wait_for_import(import_id: str, timeout=300):
    """Wait for import to complete"""
    start = time.time()
    while time.time() - start < timeout:
        status = check_import_status(import_id)
        state = status['state']
        if state == 'DONE':
            print(f"Import completed: {status['importResults']}")
            return status
        elif state == 'FAILED':
            raise Exception(f"Import failed: {status.get('error', 'Unknown error')}")
        print(f"Import status: {state}... waiting")
        time.sleep(5)
    raise TimeoutError("Import timed out")

# Usage
import_id = create_batch_import("contacts_batch.csv")
result = wait_for_import(import_id)
```

**Step 2: Batch Export Deals to CSV**
```python
def export_all_deals() -> List[Dict]:
    """Export all deals with pagination"""
    all_deals = []
    after = None
    
    while True:
        params = {
            "limit": 100,
            "properties": ["dealname", "amount", "dealstage", "closedate", 
                          "createdate", "hubspot_owner_id", "pipeline"]
        }
        if after:
            params['after'] = after
        
        response = requests.get(
            f"{BASE_URL}/crm/v3/objects/deals",
            headers=HEADERS,
            params=params
        )
        
        data = response.json()
        all_deals.extend(data.get('results', []))
        
        paging = data.get('paging')
        if paging and paging.get('next'):
            after = paging['next']['after']
        else:
            break
    
    return all_deals

def deals_to_csv(deals: List[Dict], filename: str):
    """Write deals to CSV file"""
    with open(filename, 'w', newline='') as f:
        writer = csv.writer(f)
        # Header
        writer.writerow(['ID', 'Name', 'Amount', 'Stage', 'Close Date', 
                        'Created Date', 'Owner ID', 'Pipeline'])
        
        for deal in deals:
            props = deal.get('properties', {})
            writer.writerow([
                deal['id'],
                props.get('dealname', ''),
                props.get('amount', ''),
                props.get('dealstage', ''),
                props.get('closedate', ''),
                props.get('createdate', ''),
                props.get('hubspot_owner_id', ''),
                props.get('pipeline', '')
            ])

# Usage
deals = export_all_deals()
deals_to_csv(deals, "all_deals_export.csv")
print(f"Exported {len(deals)} deals to all_deals_export.csv")
```

---

## API Best Practices

### 1. Rate Limiting
HubSpot API has tier-based rate limits:
| Plan | Daily Calls | Burst Limit |
|------|------------|-------------|
| Free | 250,000 | 100 requests/10 seconds |
| Starter | 500,000 | 120 requests/10 seconds |
| Professional | 1,000,000 | 150 requests/10 seconds |
| Enterprise | 1,500,000+ | 200 requests/10 seconds |

**Handle rate limits in code:**
```python
import time

def api_call_with_retry(url, headers, max_retries=3):
    for attempt in range(max_retries):
        response = requests.get(url, headers=headers)
        
        if response.status_code == 429:
            retry_after = int(response.headers.get('Retry-After', 10))
            print(f"Rate limited. Waiting {retry_after} seconds...")
            time.sleep(retry_after)
            continue
        
        return response
    
    raise Exception("API call failed after retries")
```

### 2. Batched API Operations
Use batch endpoints for efficiency:
```python
# Create multiple contacts in one call
response = requests.post(
    f"{BASE_URL}/crm/v3/objects/contacts/batch/create",
    headers=HEADERS,
    json={
        "inputs": [
            {"properties": {"email": "user1@example.com", "firstname": "User 1"}},
            {"properties": {"email": "user2@example.com", "firstname": "User 2"}},
            {"properties": {"email": "user3@example.com", "firstname": "User 3"}},
        ]
    }
)
```

### 3. Error Handling Patterns
| HTTP Status | Meaning | Action |
|------------|---------|--------|
| 200 | Success | Parse response |
| 400 | Bad request | Check request body and parameters |
| 401 | Unauthorized | Token expired — refresh OAuth token |
| 403 | Forbidden | Check API scope permissions |
| 404 | Not found | Object ID doesn't exist |
| 409 | Conflict | Duplicate record — handle merge |
| 429 | Rate limited | Implement backoff and retry |
| 500+ | Server error | Retry with exponential backoff |

### 4. Field Selection
Always specify which properties you need — don't request everything:
```python
# BAD — fetches all properties (slow, heavy response)
response = requests.get(f"{BASE_URL}/crm/v3/objects/contacts", headers=HEADERS)

# GOOD — only fetches what you need
response = requests.get(
    f"{BASE_URL}/crm/v3/objects/contacts?properties=email,firstname,lastname,phone",
    headers=HEADERS
)

# For many contacts, use POST search instead
response = requests.post(
    f"{BASE_URL}/crm/v3/objects/contacts/search",
    headers=HEADERS,
    json={"properties": ["email", "firstname", "lastname"], "limit": 100}
)
```

### 5. Webhook Reliability
- Expect at-least-once delivery (may receive duplicates — deduplicate by event ID)
- Respond with 200 OK quickly — HubSpot has a 5-second timeout
- Use idempotent processing: same event processed twice should produce same result
- Store event IDs to detect duplicates
- Set up retry logic: HubSpot retries failed webhooks for 24 hours

### 6. Sandbox Testing (Enterprise)
Always test API changes in a sandbox:
1. **Settings** > **Account Management** > **Sandboxes** > Create sandbox
2. Sandbox copies your production data and settings
3. Make API calls to your sandbox portal URL
4. Test webhooks, data imports, and automation
5. Promote tested configurations to production