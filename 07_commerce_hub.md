# 7. Commerce Hub — Complete Tutorial

## Table of Contents
1. [Introduction to Commerce Hub](#introduction-to-commerce-hub)
2. [Payments — Complete Guide](#payments--complete-guide)
3. [Invoicing — Complete Guide](#invoicing--complete-guide)
4. [Subscriptions — Complete Guide](#subscriptions--complete-guide)
5. [CPQ (Configure, Price, Quote) — Complete Guide](#cpq-configure-price-quote--complete-guide)
6. [Accounting Integrations — Complete Guide](#accounting-integrations--complete-guide)
7. [Tax Management — Complete Guide](#tax-management--complete-guide)
8. [Billing Portal — Complete Guide](#billing-portal--complete-guide)
9. [Payment Reporting — Complete Guide](#payment-reporting--complete-guide)
10. [Limits That Matter](#limits-that-matter)
11. [Common Gotchas](#common-gotchas)
12. [Use Cases](#use-cases)

---

## Introduction to Commerce Hub

Commerce Hub brings payment processing, invoicing, subscriptions, and CPQ into HubSpot's CRM. It transforms HubSpot from a CRM into a revenue platform where you can manage the entire quote-to-cash lifecycle without leaving the system.

### What Commerce Hub Includes

| Feature | Starter | Professional | Enterprise |
|---------|---------|-------------|------------|
| Payment links | ✓ | ✓ | ✓ |
| Card processing | ✓ | ✓ | ✓ |
| Digital wallets | ✓ | ✓ | ✓ |
| Invoicing | ✓ | ✓ | ✓ |
| Recurring invoices | ✓ | ✓ | ✓ |
| Subscriptions | ✗ | ✓ | ✓ |
| CPQ (bundles) | ✗ | ✗ | ✓ |
| Accounting integrations | ✓ | ✓ | ✓ |
| Tax calculation | ✓ (basic) | ✓ (Avalara) | ✓ (Avalara) |

### Payment Processing

Commerce Hub's payment processing is powered by **Stripe**. HubSpot handles the Stripe integration — you don't need a separate Stripe account (though you can connect an existing one).

### Navigation

- **Commerce** > **Payments** — Payment links, transactions, disputes
- **Commerce** > **Invoices** — Invoice creation, templates, recurring
- **Commerce** > **Subscriptions** — Plans, subscribers, billing cycles
- **Commerce** > **CPQ** — Product bundles, pricing rules (Enterprise)
- **Commerce** > **Reporting** — Revenue, payment, subscription analytics

---

## Payments — Complete Guide

### Setting Up Payments

1. **Settings** > **Commerce** > **Payments** > **Connect payment processor**
2. Two options:
   - **Use HubSpot's Stripe account** (quick setup, no separate account needed)
   - **Connect your existing Stripe account** (for existing Stripe customers)
3. **Business details**: Business name, address, tax ID, support email
4. **Statement descriptor**: What appears on customer's bank statement (e.g., "ACME CORP")
5. **Accepted payment methods**:
   - Credit/debit cards (Visa, Mastercard, Amex, Discover)
   - Digital wallets (Apple Pay, Google Pay)
   - Buy now, pay later (Affirm, Afterpay — US only)
   - ACH bank transfers (US only)
6. **Currency**: Choose your primary currency (can add more later)
7. **Pricing**: Standard processing fee (2.9% + $0.30 per transaction for cards; varies by region and volume)

### Payment Links

Shareable checkout pages you can send to customers:

**Creating a payment link**:
1. **Commerce** > **Payments** > **Payment links** > Create
2. **Amount**: Fixed amount or "customer enters amount"
3. **Currency**: Default or choose specific
4. **Description**: What the payment is for (appears on checkout page)
5. **One-time or recurring**: Single payment or subscription setup
6. **Expiration**: Optional link expiration date
7. **Customize**: Add your logo, brand colors, custom thank-you message

**Sharing payment links**:
- Copy link and paste in email, chat, SMS
- Include in HubSpot quotes (with Commerce Hub enabled)
- Add to invoices as "Pay now" button
- Embed on website pages

**Checkout experience** (what the customer sees):
1. Customer clicks link → branded checkout page
2. Sees amount, description, your logo
3. Enters payment info (card details or digital wallet)
4. Completes payment → confirmation page
5. Payment logged on contact timeline
6. Invoice auto-generated
7. Workflow can trigger (e.g., "Payment received → activate subscription")

### Dispute Management

Handle chargebacks directly in HubSpot:

1. **Commerce** > **Payments** > **Disputes**
2. See disputed transactions with reason (fraud, product not received, etc.)
3. Respond with evidence: tracking info, signed contracts, communication history
4. Track dispute status: Open → Under Review → Won/Lost
5. Dispute rate monitoring (% of transactions disputed)

### Refund Processing

1. Open a payment record
2. Click "Refund"
3. Enter refund amount (full or partial)
4. Select reason: Customer request, Duplicate, Fraud, Other
5. Process refund → money returned to customer
6. Refund logged on contact timeline and payment record

---

## Invoicing — Complete Guide

### Creating an Invoice

1. **Commerce** > **Invoices** > Create invoice
2. **Customer**: Select contact (auto-fills billing info)
3. **Invoice date**: Default today
4. **Due date**: Default 30 days (customizable: 7, 15, 30, 60, or custom)
5. **Line items**: Add products, descriptions, quantity, unit price
6. **Discounts**: Per-line or overall (percentage or flat amount)
7. **Tax**: Auto-calculated with Avalara integration (or manual entry)
8. **Payment terms**: Due on receipt, Net 15, Net 30, Net 60, or custom
9. **Memo**: Optional note to customer
10. **Attachments**: Upload supporting documents (contract, PO, timesheet)
11. **Send options**:
   - Send via HubSpot email (customer receives PDF + payment link)
   - Download PDF and send manually
   - Share payment link only

### Invoice Templates

1. **Settings** > **Commerce** > **Invoices** > **Templates**
2. Create template with:
   - Logo placement
   - Brand colors
   - Header/footer text
   - Payment terms
   - Late payment reminders
   - Invoice number format (auto-incrementing or custom)

### Recurring Invoices

For regular billing cycles:

1. **Commerce** > **Invoices** > **Recurring invoices** > Create
2. Customer, line items, amounts (same as regular invoice)
3. **Frequency**: Weekly, bi-weekly, monthly, quarterly, annually
4. **Start date**: When to begin
5. **End**: Never (ongoing), after N occurrences, or on specific date
6. **Send options**: Send automatically on schedule or create draft for review
7. HubSpot auto-generates and sends invoices on schedule
8. Payment and invoice history tracked on contact timeline

### Invoice Automation

Automated workflows for invoices:

**Trigger**: Invoice becomes overdue
- Send payment reminder email (Day 1, 7, 14, 30)
- Notify sales rep
- Apply late fee (requires custom-coded action)
- Suspend service if overdue > 60 days (requires integration)

**Trigger**: Invoice paid
- Send receipt/thank-you
- Update deal stage to "Closed Won"
- Activate subscription
- Notify fulfillment team

---

## Subscriptions — Complete Guide

### Creating a Subscription Product

1. **Settings** > **Products** > **Products** > Create product
2. **Product type**: Select "Service/Subscription"
3. **Billing frequency**: Monthly, Quarterly, Semi-Annual, Annual, Custom
4. **Price**: Set price per billing period
5. **Free trial**: Offer X days free
6. **Setup fee**: One-time fee on signup
7. **Cancel anytime**: Yes/No

### Managing Subscribers

1. **Commerce** > **Subscriptions**
2. **List view**: All subscribers with plan, status, next billing date
3. **Filter by**: Plan, status (Active, Paused, Cancelled, Past Due), billing cycle
4. **Subscriber details**:
   - Contact info (linked to HubSpot contact)
   - Plan details
   - Payment history
   - Billing cycle (current period start/end)
   - Next payment date and amount
   - Lifetime value
   - Churn risk score (if Breeze Intelligence enabled)

### Subscription Lifecycle

| Status | Description | Actions |
|--------|-------------|---------|
| **Active** | Subscriber is current on payments | Normal operations |
| **Past Due** | Last payment failed, grace period | Send reminders, retry payment |
| **Cancelled** | Subscriber or admin cancelled | Retention offer, convert to free |
| **Paused** | Temporarily suspended | Resume when ready |
| **Expired** | Term ended without renewal | Win-back campaign |

### Dunning Management

Automatic retry logic for failed payments:

1. **Settings** > **Commerce** > **Subscriptions** > **Dunning**
2. **Retry schedule**: Smart retry (3, 5, 8 days) or custom
3. **Email notifications**: Send to customer on first failure
4. **Grace period**: Days before cancellation after failure
5. **Escalation**: Notify account manager after 3 failed attempts

### Plan Changes

- **Upgrade**: Prorated charge for remainder of billing period
- **Downgrade**: Credits applied to next billing period
- **Add-ons**: Add features mid-cycle with prorated pricing

---

## CPQ (Configure, Price, Quote) — Complete Guide

CPQ is an Enterprise feature for complex product configurations and pricing.

### Product Bundles

Group products into packages:

1. **Commerce** > **CPQ** > **Product Bundles** > Create
2. **Bundle name**: "Starter Suite" or "Enterprise Package"
3. **Components**: Add products, each with:
   - Quantity
   - Role: Required or Optional
   - Default selection: Yes/No
4. **Bundle pricing**:
   - Sum of components (no discount)
   - Fixed bundle price (discounted from sum)
   - Tiered (price changes based on quantity)

### Pricing Rules

Apply dynamic pricing logic:

**Volume discounts**:
```
1-10 units: $100 each
11-50 units: $90 each
51+ units: $80 each
```

**Tiered pricing**:
```
Starter: $100/mo (up to 50 contacts)
Professional: $500/mo (up to 500 contacts)
Enterprise: $2,000/mo (unlimited contacts)
```

**Contract term discounts**:
```
Monthly: List price
Annual (paid monthly): 10% discount
Annual (paid upfront): 20% discount
```

**Customer segment pricing**:
```
New business: Standard price
Existing customer: Loyalty discount of 15%
Nonprofit: 50% discount
```

### Guided Selling

Multi-step product configuration for complex sales:

**Example: IT Services Quote**
```
Step 1: How many users? → [Number input]
Step 2: What features? → [Checkboxes: Security, Analytics, API, Support]
Step 3: Support level? → [Basic, Standard, Premium]
Step 4: Contract term? → [Monthly, Annual, Multi-year]
Step 5: Review and quote
```

Each choice updates the price and available options in real-time.

### Approval Flows

Multi-level approval for complex quotes:

| Quote Value | Approver |
|-------------|----------|
| < $10,000 | Sales manager |
| $10,000 - $50,000 | VP of Sales |
| $50,000 - $250,000 | CRO |
| $250,000+ | CEO |

Approval requests show: Customer, products, total, discount %, margin %, rep notes.

---

## Accounting Integrations — Complete Guide

### Supported Integrations

| App | What Syncs | Direction |
|-----|-----------|-----------|
| **QuickBooks Online** | Customers, Invoices, Payments | Bi-directional |
| **QuickBooks Desktop** | Customers, Invoices | HubSpot → QB |
| **Xero** | Customers, Invoices, Payments | Bi-directional |
| **NetSuite** | Customers, Invoices, Payments | Bi-directional |
| **Stripe** | Charges, Refunds, Customers | HubSpot ↔ Stripe |

### Setting Up QuickBooks

1. **Settings** > **Commerce** > **Accounting** > **QuickBooks**
2. Click "Connect"
3. Log in to QuickBooks and authorize access
4. **Mapping**:
   - HubSpot Customers → QuickBooks Customers
   - HubSpot Invoices → QuickBooks Invoices
   - HubSpot Payments → QuickBooks Payments
5. **Sync frequency**: Real-time or daily
6. **Tax codes**: Map HubSpot tax settings to QuickBooks tax codes

### What Gets Synced

From HubSpot to accounting app:
- Invoice created → syncs as sales invoice
- Payment received → syncs as payment
- Customer created → syncs as customer/account
- Credit note → syncs as credit memo

From accounting app to HubSpot:
- Payment status updates
- Invoice status (paid, overdue, voided)
- Customer account status

---

## Tax Management — Complete Guide

### Manual Tax Entry

For simple tax needs:
1. In invoice creation, enable "Apply tax"
2. Set tax rate as percentage (e.g., 8.25%)
3. Tax applies to all line items
4. Displayed separately on invoice

### Avalara Integration

For automated, jurisdiction-accurate tax calculation:

1. **Settings** > **Commerce** > **Tax** > **Connect Avalara**
2. Log in to your Avalara account
3. **Tax code mapping**: Map your products to Avalara tax codes
4. **Jurisdiction support**: Auto-calculates state, county, city taxes
5. **Exempt customers**: Mark customers as tax-exempt
6. **Nexus rules**: Configure which states you have tax nexus in

**What Avalara handles**:
- US sales tax (state, county, city)
- VAT (European Union, UK)
- GST/HST (Canada, Australia, India, Singapore)
- Digital services tax (various countries)

### Tax Reporting

- **Tax collected by period**: Track total tax collected
- **Tax by jurisdiction**: Breakdown by state/country
- **Tax-exempt sales**: Value of exempt transactions
- **Tax filing reports**: Ready-to-file summaries (Avalara integration)

---

## Billing Portal — Complete Guide

The customer self-service portal for billing management.

### Setting Up the Portal

1. **Settings** > **Commerce** > **Billing Portal**
2. **Customize**:
   - Logo
   - Brand colors
   - Portal URL (yourcompany.hubspotbilling.com or custom domain)
   - Support contact information
3. **Available actions**:
   - View invoices (current and past)
   - View payment history
   - Update payment method
   - Download invoices as PDF
   - Manage subscriptions (pause, cancel, upgrade)
   - Update billing address

### Sending Portal Access

- Invoice emails include "View invoice" link
- "Manage billing" link in email footer
- Direct portal URL sent to customers

---

## Payment Reporting — Complete Guide

### Revenue Dashboard

- **Total revenue**: This month, last month, YTD
- **Revenue by source**: Invoices, payment links, subscriptions
- **Revenue by product**: Which products/services generate most revenue
- **Revenue by customer**: Top customers by revenue
- **Payment method breakdown**: Card vs digital wallet vs ACH

### Transaction Reports

- **Transactions by status**: Completed, pending, failed, refunded, disputed
- **Average transaction value**: Overall and by customer segment
- **Transaction volume**: Count and value over time
- **Failed payments**: Rate and reasons

### Subscription Analytics

- **MRR/ARR**: Monthly and Annual Recurring Revenue
- **Churn rate**: % of subscribers who cancelled
- **LTV**: Average customer lifetime value
- **Renewal rate**: % of subscribers who renew
- **Trial conversion**: % of free trials that convert to paid

### Payment Reconciliation

- Match payments to invoices
- Match refunds to original payments
- Export to accounting software
- Bank reconciliation reports

---

## Limits That Matter

| Resource | Available |
|----------|-----------|
| Transaction fee | 2.9% + $0.30 (cards); varies for other methods |
| Payout schedule | 2 business days (US); varies by region |
| Maximum transaction amount | Varies by processor (typically $10,000-$25,000) |
| Invoice line items | 50 per invoice |
| Recurring invoice frequency | Weekly, bi-weekly, monthly, quarterly, annually |
| Subscription plans | Unlimited |
| Dunning retry attempts | Configurable (default: 3) |
| Accounting integrations | 1 per portal (expandable with Operations Hub) |
| Tax jurisdictions (Avalara) | Based on Avalara plan |

---

## Common Gotchas

### 1. Payment Processing Fees
The 2.9% + $0.30 per transaction adds up. For high-volume businesses ($50k+/mo), consider negotiating custom rates with HubSpot/Stripe.

### 2. International Payments
Commerce Hub supports 135+ currencies but payout is in your primary currency. International transactions incur currency conversion fees. Not all payment methods are available in all countries.

### 3. Invoice vs Payment Link
Invoices represent a request for payment (can be overdue). Payment links are one-time checkouts (paid immediately). Use invoices for B2B Net-30 terms, payment links for immediate collection.

### 4. Subscription Tax Compliance
If you sell subscriptions internationally, you need to handle VAT/GST correctly. Avalara integration is strongly recommended for subscription businesses with international customers.

### 5. Dunning Effectiveness
Dunning emails from HubSpot improve recovery by 15-30%. Customize both the messaging and timing for best results.

### 6. CPQ Complexity
CPQ is powerful but complex. Start with simple bundles and pricing rules before attempting advanced configurations. Test thoroughly in a sandbox.