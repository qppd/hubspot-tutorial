# 7. Commerce Hub

## What It Does
HubSpot Commerce Hub brings billing, payments, subscriptions, and CPQ (Configure, Price, Quote) into the HubSpot platform. It connects CRM data (deals, contacts, products) directly to payment processing, recurring billing, and invoicing — so sales and finance teams work from the same data.

## Key Features

### Payments
- **Payment processing**: accept credit/debit cards, ACH/direct debit (US only), PayPal (limited regions)
- **Payment gateways**: Stripe (built-in), with ability to connect custom Stripe accounts
- **Payments from quotes**: attach payment links to sales quotes — customer clicks, pays, deal closes automatically
- **Payment links**: standalone payment links (share via email, SMS, social)
- **Checkout links**: payment pages with product details and quantity selectors
- **Invoice payments**: send invoices with "pay now" button
- **Payment branding**: customize payment page with your logo, colors, domain
- **Auto-close deals**: when payment succeeds, deal stage auto-advances to Closed Won
- **Payment receipts**: auto-send branded receipts
- **Refunds**: process partial or full refunds from HubSpot
- **Chargebacks**: track and manage dispute process
- **Payouts**: view settlement history, next payout date
- **Payment reporting**: revenue by product, by rep, by channel

### Invoicing
- **Invoice creation**: create professional invoices from deals, subscriptions, or standalone
- **Invoice templates**: customize layout, logo, colors
- **Auto-numbering**: sequential invoice numbers (configurable prefix)
- **Invoice status**: Draft, Sent, Paid, Overdue, Canceled
- **Invoice scheduling**: send automatically on recurring schedule
- **Invoice reminders**: auto-send reminders for overdue invoices
- **Payment terms**: Net 7, Net 15, Net 30, Net 60, Due on receipt, Custom
- **Line items**: add products, services, discounts, taxes
- **Tax management**: configure tax rates per product or per customer region
- **Currency**: multi-currency invoicing (Enterprise)
- **Bulk invoices**: create invoices for multiple customers at once
- **Invoice archive**: searchable, filterable invoice history

### Subscriptions & Recurring Billing
- **Subscription creation**: create from deals, quotes, or directly
- **Billing frequency**: monthly, quarterly, semi-annually, annually, custom
- **Pricing models**: flat rate, per-seat, usage-based, tiered, volume
- **Trial periods**: free trial with auto-conversion to paid
- **Proration**: calculate partial charges for mid-cycle changes
- **Subscription upgrades/downgrades**: change plan mid-cycle
- **Cancellation**: automated cancellation workflows
- **Dunning management**: auto-retry failed payments with escalation (reminders, then suspension, then cancellation)
- **Subscription lifecycle**: Active, Past Due, Canceled, Expired
- **Revenue recognition**: track MRR, ARR, churn, LTV
- **Usage tracking**: track and bill based on consumption (API-based)

### CPQ (Configure, Price, Quote)
- **Product configuration**: bundles, options, variants
- **Pricing rules**: volume discounts, tiered pricing, promotional pricing
- **Quote templates**: professional PDF templates
- **Approval workflows**: quotes over threshold need manager sign-off
- **Discount management**: per-line or overall discounts
- **Multi-currency quotes**: quote in customer's currency (Enterprise)
- **Quote analytics**: quote-to-close rate, average discount %, quote velocity
- **Locked pricing**: prevent sales reps from giving discounts beyond approved threshold
- **Renewal quotes**: auto-generate renewal quotes from existing subscriptions
- **Contract management**: associate contract terms with quotes (Enterprise)

### Accounting Integration
- **QuickBooks Online**: sync invoices, payments, customers (bidirectional)
- **Xero**: sync invoices, payments, contacts
- **Stripe**: payment processing and reconciliation
- **Revenue recognition**: record revenue in accounting periods
- **Chart of accounts mapping**: map products/categories to GL accounts
- **Sales tax**: collect, track, and report sales tax (Avalara integration available)

### Payment Links & Checkout
- **Payment link**: shareable URL for one-time payment
- **Checkout page**: product + quantity + price → payment details → confirmation
- **Embedded checkout**: embed in website, landing pages, or emails
- **Checkout customization**: logo, brand colors, custom domain
- **Email receipts**: auto-send on successful payment
- **Abandoned payment recovery**: follow up on incomplete payments (via workflows)
- **Multiple payment methods**: card, ACH, digital wallets (region-dependent)

### Reporting & Analytics
- **Revenue dashboard**: total revenue, MRR, ARR, churn rate, LTV, average deal size
- **Subscription analytics**: active subscriptions, churn rate, upgrade/downgrade rate
- **Invoice analytics**: invoices sent, paid, overdue, average days to payment
- **Payment analytics**: volume, methods, failure rate, refund rate
- **Quote analytics**: sent, viewed, signed, expired, won/lost
- **Tax reporting**: sales tax collected by region
- **Custom reports**: build on commerce data using custom report builder

## Step-by-Step: Connecting a Stripe Account

1. Settings > Commerce > Payments > Connect payment processor
2. Select Stripe
3. Connect existing Stripe account or create new
4. Configure auto-close: "Auto-close deals when payment succeeds"
5. Set default payment methods: Credit card, ACH, PayPal
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

- Payment processing: only available in supported countries (US, UK, Canada, Australia, select EU)
- Transaction fee: 1.99% + $0.49 (Starter), 1.49% + $0.49 (Pro/Enterprise) — or use your own Stripe
- Payment methods: Credit/debit cards required; ACH (US only); PayPal (limited regions)
- Recurring billing: included in Commerce Hub (not in base HubSpot)
- Invoice number prefix: customizable
- Invoice due date: set per invoice or default from payment terms
- Subscription proration: supported for upgrades/downgrades
- Multi-currency: Enterprise only
- Accounting integrations: QuickBooks, Xero (Pro+)
- Dunning retries: up to 5 retries before subscription suspension
- Tax calculation: Avalara integration (separate subscription)

## Use Cases

- SaaS businesses: manage subscriptions, billing, dunning from CRM
- Service businesses: send payment links in quotes and invoices
- E-commerce: one-time payments, checkout links
- Sales teams: close deals with integrated payment (customer pays immediately)
- Finance teams: reconcile payments, manage invoices, track MRR
- Subscription businesses: handle upgrades/downgrades/cancellations
- CPQ: configure complex products with pricing rules, approvals, and discounts

## Common Gotchas

- Payment processing requires verification of your business (KYC) before payouts
- Stripe account currency must match HubSpot account default currency
- Refunds are processed immediately — no "pending" state for credit cards
- Subscription auto-creation from deals only works if the product has a recurring price
- Dunning emails are separate from HubSpot marketing emails (transactional, not counted in marketing sends)
- Abandoned payment recovery requires workflows configured on payment failure event
- Tax is not automatically calculated unless using Avalara integration
- Commerce Hub is not available in all countries (check HubSpot's supported countries list)
- Payment links expire after set duration (default: 7 days) — configure in settings
- Quotes with payment links show payment option only if Commerce Hub is active