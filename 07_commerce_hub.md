# 7. Commerce Hub

## What It Does
HubSpot Commerce Hub brings billing, payments, subscriptions, and CPQ (Configure, Price, Quote) directly into the HubSpot platform. It connects CRM data (deals, contacts, products) to payment processing, recurring billing, and invoicing — so sales and finance teams work from the same data instead of switching between Stripe, QuickBooks, and HubSpot.

## Key Features

### Payments
- **Payment processing**: accept credit/debit cards (Visa, MC, Amex, Discover), ACH/direct debit (US only), PayPal (limited regions), and digital wallets (Apple Pay, Google Pay)
- **Payment gateways**: Stripe (built-in) with the option to connect your own Stripe account
- **Payments from quotes**: attach payment links to sales quotes — customer clicks, pays, deal closes automatically
- **Payment links**: standalone payment links (share via email, SMS, social media)
- **Checkout links**: full payment pages with product details, quantity selectors, and shipping info
- **Invoice payments**: send invoices with embedded "Pay now" button
- **Payment page branding**: customize with your logo, brand colors, and custom domain
- **Auto-close deals**: when payment succeeds, deal stage auto-advances to Closed Won
- **Payment receipts**: auto-send branded receipts with line items and payment details
- **Refunds**: process partial or full refunds directly in HubSpot
- **Chargebacks**: track and manage dispute process with notifications
- **Payouts**: view settlement history, next payout date, and transaction breakdown
- **Payment reporting**: revenue by product, rep, channel, and payment method

### Invoicing
- **Invoice creation**: create professional invoices from deals, subscriptions, or standalone
- **Invoice templates**: customize layout, logo, colors, and content blocks
- **Auto-numbering**: sequential invoice numbers with configurable prefix and starting number
- **Invoice status**: Draft, Sent, Paid, Overdue, Canceled, Void
- **Invoice scheduling**: send automatically on recurring schedule
- **Invoice reminders**: auto-send reminders for overdue invoices (customizable timing and frequency)
- **Payment terms**: Net 7, Net 15, Net 30, Net 60, Due on Receipt, Custom
- **Line items**: add products, services, discounts, taxes, shipping
- **Tax management**: configure tax rates per product or per customer region
- **Multi-currency invoicing**: send invoices in customer's currency (Enterprise)
- **Bulk invoices**: create invoices for multiple customers at once
- **Invoice archive**: searchable, filterable invoice history with full audit trail

### Subscriptions & Recurring Billing
- **Subscription creation**: create from deals, quotes, or directly from contact/company records
- **Billing frequency**: monthly, quarterly, semi-annually, annually, or custom intervals
- **Pricing models**: flat rate, per-seat, usage-based, tiered, volume-based
- **Trial periods**: free trial with auto-conversion to paid
- **Proration**: calculate partial charges for mid-cycle upgrades or downgrades
- **Subscription upgrades/downgrades**: change plan mid-cycle with prorated charges
- **Cancellation**: automated cancellation workflows with confirmation and feedback collection
- **Dunning management**: auto-retry failed payments with escalation sequence
  - Day 0: auto-retry (3 attempts)
  - Day 3: reminder email
  - Day 7: suspension notice
  - Day 14: cancellation
- **Subscription lifecycle**: Active, Past Due, Canceled, Expired, Pending
- **Revenue recognition**: track MRR, ARR, churn rate, LTV, average revenue per account
- **Usage tracking**: track and bill based on consumption (API-based metering)

### CPQ (Configure, Price, Quote)
- **Product configuration**: bundles, options, variants with conditional logic
- **Pricing rules**: volume discounts, tiered pricing, promotional pricing, contract-length discounts
- **Quote templates**: professional PDF templates with custom branding
- **Approval workflows**: quotes over a threshold need manager sign-off (configurable per amount or discount %)
- **Discount management**: per-line or overall discounts with approval gates
- **Multi-currency quotes**: quote in customer's currency (Enterprise)
- **Quote analytics**: quote-to-close rate, average discount %, quote velocity, time-to-sign
- **Locked pricing**: prevent sales reps from giving discounts beyond approved thresholds
- **Renewal quotes**: auto-generate renewal quotes from existing subscriptions
- **Contract management**: associate contract terms, start/end dates, and auto-renewal with quotes (Enterprise)

### Accounting Integration
- **QuickBooks Online**: sync invoices, payments, customers (bidirectional)
- **Xero**: sync invoices, payments, contacts
- **Stripe**: payment processing and automatic reconciliation
- **Revenue recognition**: record revenue in proper accounting periods
- **Chart of accounts mapping**: map products/categories to GL accounts
- **Sales tax**: collect, track, and report sales tax (Avalara integration available as add-on)

### Payment Links & Checkout Pages
- **Payment link**: shareable URL for one-time payment (no customer login required)
- **Checkout page**: full product + quantity + price → payment details → confirmation flow
- **Embedded checkout**: embed in website, landing pages, or emails via iframe
- **Checkout customization**: logo, brand colors, custom domain, thank-you page
- **Email receipts**: auto-send branded receipt on successful payment
- **Abandoned payment recovery**: follow up on incomplete payments (via workflows triggered on payment failure event)
- **Multiple payment methods**: card, ACH, Apple Pay, Google Pay (region-dependent)

### Reporting & Analytics
- **Revenue dashboard**: total revenue, MRR, ARR, churn rate, LTV, average deal size, net revenue retention
- **Subscription analytics**: active subscriptions, churn rate, upgrade/downgrade rate, expansion revenue
- **Invoice analytics**: invoices sent, paid, overdue %, average days to payment
- **Payment analytics**: volume by method, success/failure rate, refund rate, chargeback rate
- **Quote analytics**: sent, viewed, signed, expired, won/lost with conversion funnel
- **Tax reporting**: sales tax collected by region and time period
- **Custom reports**: build reports on commerce data using Custom Report Builder

## Step-by-Step: Connecting a Stripe Account

1. Settings > Commerce > Payments > Connect payment processor
2. Select Stripe
3. Connect existing Stripe account or create new
4. Configure auto-close: "Auto-close deals when payment succeeds"
5. Set default payment methods: Credit card, ACH, PayPal, Apple Pay
6. Configure payment page branding (logo, colors, domain)
7. Save

## Step-by-Step: Creating a Subscription Product

1. Commerce > Products > Create product
2. Name: "Monthly Pro Plan"
3. Set pricing: $99/month (recurring)
4. Billing frequency: Monthly
5. Add description, SKU
6. Set tax category
7. Add to product library
8. When a deal is won with this product → subscription auto-creates

## Step-by-Step: Sending a Payment Link

1. Commerce > Payments > Create payment link
2. Enter amount and currency
3. Add description (optional)
4. Customize payment page (branding)
5. Copy link or share directly (email, SMS)
6. When customer pays:
   - Payment recorded in CRM
   - Receipt auto-sent
   - Deal auto-closed (if associated)
   - Invoice marked paid

## Step-by-Step: Creating a Subscription from a Deal

1. Create deal with product line item that has recurring price
2. Close deal → subscription auto-creates (enable in Commerce settings)
3. Subscription appears on contact record
4. Auto-billing: first payment processed, recurring schedule set
5. Failed payment → dunning sequence starts (Day 0: retry, Day 3: reminder, Day 7: suspension notice, Day 14: cancel)

## Limits That Matter

- **Availability**: payment processing only in supported countries (US, UK, Canada, Australia, EU, select others)
- **Transaction fee (HubSpot processing)**: 1.99% + $0.49 (Starter), 1.49% + $0.49 (Pro/Enterprise) — or use your own Stripe with no HubSpot transaction fee
- **Payment methods**: Credit/debit cards always; ACH (US only); PayPal (limited regions); Apple Pay/Google Pay (where supported)
- **Recurring billing**: included in Commerce Hub; not available in base HubSpot
- **Invoice numbering**: fully customizable prefix
- **Invoice due date**: set per invoice or default from payment terms
- **Proration**: supported for mid-cycle upgrades and downgrades
- **Multi-currency**: Enterprise only
- **Accounting integrations**: QuickBooks, Xero (Pro+)
- **Dunning retries**: up to 3 auto-retry attempts, then 2 reminder stages before cancellation
- **Tax calculation**: manual or Avalara integration (separate subscription/subscription fee)
- **Payment link expiration**: configurable (default 30 days)

## Use Cases

- **SaaS businesses**: manage subscriptions, billing, and dunning from the CRM
- **Service businesses**: send payment links in quotes and invoices for one-time services
- **E-commerce**: one-time payments with checkout links and product pages
- **Sales teams**: close deals with embedded payment (customer pays immediately from quote)
- **Finance teams**: reconcile payments, manage invoices, track MRR/ARR from one platform
- **Subscription businesses**: handle upgrades, downgrades, cancellations, and failed payments
- **CPQ**: configure complex product bundles with pricing rules, approval workflows, and discount gates

## Common Gotchas

- Payment processing requires business verification (KYC) before payouts start
- Stripe account currency must match HubSpot account default currency
- Refunds are processed immediately — no "pending" state for credit card refunds
- Subscription auto-creation from deals only works if the product has a recurring price set
- Dunning emails are transactional (not counted in marketing email sends)
- Abandoned payment recovery requires you to set up workflows triggered on payment failure event
- Tax is not automatically calculated unless using Avalara integration (separate cost)
- Commerce Hub is not available in all countries — check HubSpot's supported list
- Payment links expire after a configurable duration (default: 30 days)
- Quotes with payment links show payment options only if Commerce Hub is active on the account
- ACH payments take 3-5 business days to settle; card payments settle in 1-2 days