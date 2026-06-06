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

---

## Payment Methods — Detailed Reference

### Credit/Debit Cards

| Card Type | Supported | Regions |
|-----------|-----------|---------|
| Visa | ✓ | Worldwide |
| Mastercard | ✓ | Worldwide |
| American Express | ✓ | Worldwide (higher processing fee) |
| Discover | ✓ | US, Canada |
| Diners Club | ✓ | US, select international |
| JCB | ✓ | Japan, select international |
| UnionPay | ✓ | China, select international |

**Processing details**: Cards are processed through Stripe's gateway. HubSpot handles PCI DSS Level 1 compliance — you never handle raw card numbers. Card entry happens on Stripe's secure iframe or via Stripe Elements.

### Digital Wallets

| Wallet | Setup Required | User Experience |
|--------|---------------|-----------------|
| **Apple Pay** | Domain verification with Apple | One-touch payment with Face ID/Touch ID on Safari |
| **Google Pay** | Link with Google Merchant account | One-touch on Chrome/Android |
| **Shopify Pay** | Shopify integration | For Shopify-connected stores |

**How digital wallets work in HubSpot**: When enabled, the checkout page shows Apple Pay/Google Pay buttons alongside the card form. If the customer's browser supports it, they can pay with biometric authentication. The payment is processed through Stripe's existing integration.

### Buy Now, Pay Later (BNPL)

| Provider | Installment Options | Merchant Fee |
|----------|-------------------|--------------|
| **Affirm** | 3, 6, 12 months | 4-6% of transaction |
| **Afterpay** | 4 bi-weekly payments | 4-6% of transaction |

**How BNPL works**: Customer selects BNPL at checkout. They're redirected to the BNPL provider's approval flow. If approved, HubSpot receives the full payment upfront (minus BNPL fee). Customer pays the BNPL provider in installments. If customer defaults, BNPL provider bears the risk.

### ACH Bank Transfers (US Only)

| Feature | Details |
|---------|---------|
| Fee | 0.8% + $5.00 cap per transaction |
| Settlement time | 3-5 business days |
| Max transaction | $25,000 per transfer |
| Refund window | 60 days to initiate refund |
| Failed payment fee | $5.00 per failed ACH |

**Use case**: B2B companies with large invoice amounts ($5,000+) prefer ACH over credit cards to avoid 2.9% fees.

---

## Payouts & Settlement — Complete Guide

### Payout Schedule

| Region | Payout Speed | Notes |
|--------|-------------|-------|
| United States | 2 business days | Daily automatic payouts |
| Canada | 3 business days | Daily automatic payouts |
| United Kingdom | 3 business days | Daily automatic payouts |
| EU (SEPA) | 3 business days | Settled in EUR |
| Australia | 3 business days | Settled in AUD |
| Other regions | 5-7 business days | Varies by local banking |

**Minimum payout**: No minimum threshold — any positive balance is automatically paid out (US). Some regions have minimums ($1-10 equivalent).

### Payout Components

Each payout statement includes:
- **Gross volume**: Total amount of all transactions
- **Fees**: Processing fees deducted per transaction
- **Refunds**: Amount refunded during this period
- **Chargebacks**: Disputed amounts deducted
- **Adjustments**: Any corrections from Stripe
- **Net payout**: Gross - fees - refunds - chargebacks

### Payout Reporting

1. **Commerce** > **Reporting** > **Payouts**
2. View payout history by date range
3. Download payout reports as CSV
4. Reconcile with bank deposits
5. Export to accounting software via integration

### Reserve & Rolling Reserve

For businesses with higher chargeback risk, HubSpot/Stripe may place a reserve:
- **Rolling reserve**: Percentage of each transaction held for a period (e.g., 5% held for 90 days)
- **Fixed reserve**: Set amount held
- **Reserve release**: Released after reserve period if no chargebacks occur

---

## End-to-End Tutorial: Setting Up a Subscription Business in Commerce Hub

This walkthrough covers the complete setup of a subscription-based SaaS business in Commerce Hub.

### Step 1: Initial Configuration

1. **Settings** > **Commerce** > **Payments** > **Connect payment processor**
2. Select "Use HubSpot's Stripe account" or "Connect existing Stripe account"
3. Enter business details:
   - Legal business name: "Acme SaaS Inc."
   - Support email: "support@acmessaas.com"
   - Statement descriptor: "ACME SAAS"
   - Customer support phone: +1-555-123-4567
4. Enable payment methods: Visa, Mastercard, Amex, Apple Pay, Google Pay
5. Click "Complete setup"

### Step 2: Create Subscription Products

1. **Settings** > **Products** > **Products** > **Create product**
2. **Product A — Basic Plan**
   - Name: "Basic Plan"
   - Type: Service/Subscription
   - Billing: Monthly at $29.00
   - Description: "Up to 100 contacts, basic features"
   - SKU: SUB-BASIC-MONTHLY
3. **Product B — Pro Plan**
   - Name: "Pro Plan"
   - Type: Service/Subscription
   - Billing: Monthly at $99.00
   - Description: "Up to 1,000 contacts, all features"
   - SKU: SUB-PRO-MONTHLY
4. **Product C — Pro Annual**
   - Name: "Pro Plan Annual"
   - Type: Service/Subscription
   - Billing: Annually at $999.00 (save 16%)
   - SKU: SUB-PRO-ANNUAL
5. **Product D — Setup Fee**
   - Name: "Onboarding Fee"
   - Type: One-time
   - Price: $500.00
   - SKU: ONBOARDING-FEE

### Step 3: Create Product Bundles (CPQ Enterprise)

1. **Commerce** > **CPQ** > **Product Bundles** > **Create**
2. **Bundle: "Startup Package"**
   - Basic Plan (required): 1
   - Onboarding Fee (optional, default yes): 1
   - Bundle price: $29 first month (includes onboarding), $29/mo thereafter
3. **Bundle: "Growth Package"**
   - Pro Plan (required): 1
   - Onboarding Fee (optional, default yes): 1
   - Priority Support (optional): $50/mo
   - Bundle price: Sum of components minus 5%

### Step 4: Set Up Subscription Checkout

1. **Commerce** > **Payments** > **Payment Links** > **Create**
2. Name: "Subscribe — Pro Plan"
3. Amount: Customer enters amount (or link to subscription product)
4. Select the subscription product (Pro Plan)
5. Check "Recurring payment"
6. Customize checkout page:
   - Logo: Upload company logo
   - Brand color: Primary brand color
   - Thank-you page: "Welcome! Check your email for access instructions."
7. Add to website as "Subscribe" button, or send link in sales emails

### Step 5: Configure Dunning

1. **Settings** > **Commerce** > **Subscriptions** > **Dunning**
2. Enable dunning management
3. Retry schedule:
   - Attempt 1: 3 days after failure (email notification)
   - Attempt 2: 5 days after failure (email + SMS notification)
   - Attempt 3: 8 days after failure (final notice)
4. Grace period before cancellation: 15 days
5. Cancellation action: Move subscription to "Cancelled" status, notify account manager

### Step 6: Automate Subscription Workflows

**Workflow 1: New Subscriber Onboarding**
1. Trigger: Subscription created
2. Actions:
   - Send welcome email with login credentials
   - Create contact property "Subscription Tier" = current plan
   - Enroll in "New Customer Onboarding" sequence
   - Create ticket for CS team: "New subscriber onboarding"
   - If annual plan: Set lifecycle = "VIP Customer"
   - If monthly plan: Set lifecycle = "Customer"

**Workflow 2: Failed Payment Alert**
1. Trigger: Subscription payment failed
2. Actions:
   - Send "Payment failed" email with update payment link
   - After 3 retries: Notify account manager via Slack
   - After 7 days: Create high-priority task "Retention call needed"
   - After 15 days: Send "We miss you" email with retention offer

**Workflow 3: Subscription Upgrade**
1. Trigger: Subscription plan changed (upgrade)
2. Actions:
   - Send thank-you email with new features overview
   - Update contact property "Subscription Tier"
   - Create task for CS: "Onboard customer to new features"
   - Add to "Power Users" segment for upsell opportunities

**Workflow 4: Subscription Cancellation**
1. Trigger: Subscription cancelled
2. Actions:
   - Send cancellation confirmation
   - Send feedback survey (CES: "What could we have done better?")
   - Create retention task for account manager
   - After 30 days: Move to win-back sequence
   - After 90 days: Archive from active lists

### Step 7: Reporting Dashboard

Create a subscription analytics dashboard:
1. **Reports** > **Dashboards** > **Create dashboard**
2. Name: "Subscription Business Overview"
3. Add reports:
   - MRR (Monthly Recurring Revenue) — single number
   - ARR (Annual Recurring Revenue) — single number
   - Subscribers by plan — donut chart
   - Churn rate (monthly) — line chart trending down
   - New subscriptions vs cancellations — bar chart
   - Failed payments rate — gauge chart
   - Revenue forecast — line chart with projections
   - Customer lifetime value by plan — table

---

## End-to-End Tutorial: Setting Up CPQ for a Hardware Manufacturer

For companies selling configurable physical products, CPQ is essential.

### Product Configuration

**Product: Industrial Printer**

| Component | Type | Options | Base Price |
|-----------|------|---------|-----------|
| Base model | Required | Standard, Pro, Enterprise | $5,000 / $8,000 / $12,000 |
| Print speed | Required | Standard, High-speed | Included / +$2,000 |
| Paper size | Required | Letter, Legal, Tabloid, Custom | Included / +$500 / +$1,000 / +$2,000 |
| Connectivity | Optional | WiFi, Ethernet, Bluetooth, All three | $200 / $100 / $150 / $350 |
| Extended warranty | Optional | 1yr, 2yr, 3yr | $500 / $800 / $1,000 |
| Training | Optional | On-site, Virtual, Both | $2,000 / $500 / $2,200 |
| Installation | Optional | Standard, Premium | $500 / $1,500 |

### Pricing Rules

**Rule 1 — Volume Discount**: If quantity ≥ 10, apply 10% discount on base model
**Rule 2 — Bundle Discount**: If customer adds installation + training, give 15% off installation
**Rule 3 — Competitive Win-back**: If deal source is "Competitor Switch", give additional 5% off total
**Rule 4 — Annual Contract**: If contract term = 3 years, include warranty at no charge

### Approval Flow

| Total Value | Approver | Conditions |
|-------------|----------|-----------|
| $0 - $15,000 | Sales rep | Auto-approve |
| $15,001 - $50,000 | Sales manager | Review margin, discount % |
| $50,001 - $150,000 | VP Sales | Review total, competitive pressure |
| $150,001+ | CRO | Quarterly business review context |

---

## HubSpot Commerce vs Dedicated E-commerce Platforms

### When to Use HubSpot Commerce

- You already use HubSpot CRM and want integrated payments
- You sell B2B with invoicing (Net 30, Net 60 terms)
- You run a subscription business with recurring billing
- Your sales process involves quotes, approvals, and e-signatures
- You want automated payment-to-CRM tracking (no manual reconciliation)

### When to Use Dedicated Platforms Instead

**Shopify / WooCommerce / BigCommerce for e-commerce**:
- You need a full online store with product pages, cart, checkout
- You sell 100+ products with inventory management
- You need advanced shipping calculations and tracking
- You need marketplace integration (Amazon, eBay, Etsy)
- You need advanced SEO for product pages

**Stripe / Square / Adyen for payments**:
- You process $100k+/month and want negotiated rates (2.7% vs 2.9%)
- You need advanced fraud detection (Radar, Risk Scoring)
- You need recurring billing with complex usage-based pricing
- You want direct payment processor relationship

**QuickBooks / Xero / FreshBooks for billing**:
- You need full accounting (AP, AR, GL, payroll)
- You need inventory valuation and COGS tracking
- You need tax filing preparation
- You have complex multi-entity accounting requirements

### Hybrid Approach

Many businesses use both: HubSpot Commerce for quotes + invoicing, and a dedicated e-commerce platform for the online store. Connect them via Operations Hub Data Sync or Zapier.

---

## Commerce Hub Tutorials — Advanced

### Tutorial 4: Recurring Invoice Automation

**Goal**: Automate recurring invoicing for retainer-based clients, saving hours of manual work each month.

**Step 1: Set Up Products for Retainers**
1. **Commerce** > **Products** > Create product
2. Product A: "Marketing Retainer — Bronze" — $2,000/month
3. Product B: "Marketing Retainer — Silver" — $5,000/month
4. Product C: "Marketing Retainer — Gold" — $10,000/month
5. Set billing interval: Monthly

**Step 2: Create Recurring Invoice Template**
1. **Commerce** > **Invoices** > **Templates** > Create template
2. Name: "Monthly Retainer Invoice"
3. Content:
   - Header: Company logo, name, address
   - Line items: Dynamic (from associated deal or subscription)
   - Subtotal: Sum of line items
   - Tax: 0% (or configured rate)
   - Total: Subtotal
   - Payment terms: Net 30
   - Footer: "Thank you for your continued partnership."
4. Default due days: 30

**Step 3: Build Invoice Automation Workflow**
```
Trigger: Subscription active AND billing date = Today (monthly)
Actions:
  Create invoice from subscription template
  Set invoice amount = subscription amount
  Set due date = Today + 30 days
  Send invoice to contact email
  Log invoice on contact timeline
  Create task for finance: "Verify monthly invoice batch"
```

**Step 4: Payment Tracking Automation**
```
Trigger: Invoice payment received
Actions:
  Set invoice status = "Paid"
  Update deal: Amount paid this month
  Send receipt to contact
  If payment is late (> 30 days past due)
    → Set subscription status = "Past Due"
    → Create task for account manager: "Follow up on past due invoice"
    → If 60 days past due → Send final notice → Pause subscription
```

### Tutorial 5: One-Time Payment Page for Events

**Goal**: Create a payment page for event registration that collects payment immediately.

**Step 1: Create Product**
1. **Commerce** > **Products** > Create product
2. Name: "Summit 2025 — Standard Ticket"
3. Type: One-time purchase
4. Price: $299.00
5. Description: "Full access to all sessions, lunch included"
6. SKU: TKT-SUMMIT25-STD

**Step 2: Create Payment Link**
1. **Commerce** > **Payment Links** > Create
2. Name: "Summit 2025 Registration"
3. Choose product: Summit 2025 Standard Ticket
4. Allow quantity selection (up to 5 per order)
5. Customize checkout:
   - Title: "Register for Summit 2025"
   - Description: "June 15, 2025 — Manila Convention Center"
   - Collect: Name, Email, Company, Phone
   - Thank-you page: "You're registered! Check your email for event details."
6. Share payment link via email, website, or social media

**Step 3: Post-Purchase Automation**
```
Trigger: Payment received for Summit 2025 ticket
Actions:
  Send confirmation email with event details, QR code
  Add contact to "Summit 2025 Attendees" list
  Create event check-in record
  Send calendar invite (.ics attachment)
  After event: Send follow-up survey and replay link
```

### Tutorial 6: Payment Reconciliation

**Goal**: Automatically reconcile payments received in HubSpot with bank deposits and accounting software.

**Step 1: Set Up Payment Reconciliation**
1. **Settings** > **Commerce** > **Payments** > **Reconciliation**
2. Enable auto-reconciliation
3. Connect bank account (via Plaid integration) or upload bank statement CSV
4. Match rules:
   - Exact amount match: Auto-match
   - Amount within 1%: Flag for review
   - Amount mismatch: Manual review required

**Step 2: Reconciliation Workflow**
```
Trigger: Bank deposit matched to invoice
Actions:
  Mark invoice as "Settled"
  Update deal: "Payment Settled" = true
  If all invoices in deal are settled → Move deal to "Closed Won"
  Create journal entry in connected accounting system
```

**Step 3: Handle Unmatched Payments**
```
Trigger: Bank deposit with no matching invoice
Actions:
  Create "Unidentified Payment" ticket for finance team
  Include: Amount, Date, Sender name, Transaction ID
  Set priority: Amount > $1,000 → High, else Normal
  Escalate if unresolved in 5 business days
```

### Tutorial 7: Multi-Currency Commerce Setup

**Goal**: Set up Commerce Hub to handle multiple currencies for international sales.

**Step 1: Configure Currencies**
1. **Settings** > **Commerce** > **Currencies** > Add currency
2. Primary currency: USD (for reporting)
3. Accepted currencies: EUR, GBP, CAD, AUD, JPY, PHP
4. Set exchange rate update: Automatic (daily from market rates) or Manual

**Step 2: Set Prices in Multiple Currencies**
1. **Commerce** > **Products** > Edit product
2. For each product, set prices:
   - USD: $99.00
   - EUR: €92.00
   - GBP: £79.00
   - PHP: ₱5,500
3. HubSpot shows the price in the customer's detected currency

**Step 3: Configure Currency Display**
1. **Settings** > **Commerce** > **Checkout** > Currency display
2. Options:
   - Auto-detect: Show price in visitor's browser language/region
   - Manual selector: Let customer choose currency at checkout
   - All in primary: Show all prices in USD with approximate local equivalent

**Step 4: Handle Multi-Currency Reporting**
1. All revenue converted to primary currency (USD) for reporting
2. Create custom reports filtering by transaction currency
3. Monitor FX gain/loss for multi-currency transactions:
   - Invoice in EUR at €100
   - Payment received when EUR/USD = 1.10
   - Reconciled at $110 (vs $108 at invoicing time)
   - $2 FX gain automatically tracked

**Step 5: Multi-Currency Tax Handling**
1. **Settings** > **Commerce** > **Taxes**
2. Configure tax rules per country:
   - US: State-level sales tax (Nexus-based)
   - EU: VAT based on customer country
   - UK: VAT at 20%
   - Philippines: 12% VAT
3. Tax calculated at checkout based on customer location and currency

### Tutorial 8: Commerce Analytics Dashboard

**Goal**: Build a comprehensive commerce analytics dashboard.

**Dashboard: Commerce Performance**

**Report 1: Revenue Overview**
- Single numbers: Today's Revenue, This Month, This Quarter, This Year
- Trend arrows: % vs same period last year

**Report 2: Revenue by Product**
- Horizontal bar chart
- X-axis: Revenue
- Y-axis: Product name
- Color: By product category

**Report 3: Payment Methods Breakdown**
- Pie chart
- Segments: Credit Card, PayPal, Bank Transfer, Invoice
- Value: Total amount per method

**Report 4: Monthly Recurring Revenue (MRR)**
- Line chart
- X-axis: Month
- Y-axis: MRR
- Annotations: New subscriptions, Churned subscriptions, Upgrades/downgrades

**Report 5: Churn Rate**
- Line chart (downward trend is good)
- X-axis: Month
- Y-axis: Churn %
- Target line: Industry average

**Report 6: Average Order Value**
- Single number with trend
- Also show by product category: Table

**Report 7: Payment Failures**
- Single number: Failed payments this month
- Table: Failed payments by customer, amount, date, retry count
- Action: "Retry payment" button for manual retries

**Report 8: Tax Collected**
- Single number: Total tax collected this period
- Breakdown by jurisdiction: Table

**Key Commerce Metrics to Track:**
| Metric | Formula | Target |
|--------|---------|--------|
| MRR (Monthly Recurring Revenue) | Sum of all active subscription amounts | Growing month-over-month |
| ARR (Annual Recurring Revenue) | MRR × 12 | Growing year-over-year |
| Churn Rate (monthly) | Cancelled subscriptions / Active subscriptions at start | < 5%/month (SaaS) or < 2%/month (Enterprise) |
| Customer Lifetime Value (LTV) | Average deal value × Average years as customer | > 3× CAC |
| Customer Acquisition Cost (CAC) | Total sales + marketing cost / New customers acquired | Decreasing or stable |
| LTV:CAC Ratio | LTV / CAC | > 3:1 (healthy) |
| Average Payment Collection Time | Days from invoice to payment | < 15 days |
| Failed Payment Rate | Failed payments / Total attempts | < 3% |
| Quote-to-Close Rate | Won quotes / Total quotes sent | > 60% |
| Net Revenue Retention (NRR) | (Starting MRR + Upgrades - Downgrades - Churn) / Starting MRR | > 100% (growing from existing customers) |