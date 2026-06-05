# 3. Sales Hub

## What It Does
HubSpot Sales Hub gives sales teams the tools to manage pipelines, automate outreach, track engagement, and close deals faster. It ranges from free email tracking and meeting scheduling to enterprise forecasting, conversation intelligence, and CPQ.

## Key Features

### Email Tracking & Templates
- **Email tracking**: open notifications, click tracking, link tracking (Free)
- **Email templates**: save and reuse email templates with personalization tokens
- **Snippets**: short reusable text blocks for common replies
- **AI Snippet Recommendations**: Breeze AI suggests relevant snippets based on email context and conversation history (Pro+)
- **Sequences**: automated series of follow-up emails and tasks
- **Send later**: schedule emails to send at optimal times
- **Canned replies**: pre-written responses for common scenarios
- **Meeting scheduling**: embedded meeting link (Calendar syncs with Google/Outlook)
- **Documents**: upload and share documents with tracking (who viewed, how long)
- **Live chat**: website chat routed to sales reps

### Sequences (Pro+)
- Multi-step email + task sequences
- Auto-enroll from contact lists, deal stages, form submissions
- Enroll limits per contact to prevent over-sequencing
- Sequence analytics: reply rate, meeting booked rate, unsubscribe rate
- Sequence step types: send email, wait/delay, manual task, automate task
- Conditional branching: skip steps if contact replies
- Sequence reporting: see which sequences perform best

### Meetings
- **Meeting link**: shareable URL that shows availability
- **Round-robin**: distribute meetings among team members
- **Group meetings**: multiple people on one meeting link
- **Meeting types**: phone call, video call (Zoom/Google Meet/Microsoft Teams), in-person
- **Meeting goals**: track meeting outcomes (Discovery, Demo, Proposal, Closing)
- **Calendar sync**: two-way sync with Google Calendar, Office 365, Exchange
- **Meeting buffers**: add padding between meetings
- **Custom email reminders**: send before meeting

### Calling
- **HubSpot Calling**: make and receive calls directly in HubSpot (Sales Hub Pro+)
- **Local presence**: caller ID shows local number (US)
- **Call recording**: auto-record and store in contact timeline
- **Call transcription**: AI-powered transcription (Enterprise)
- **Call logging**: log manual calls with duration, notes, outcome
- **Power dialer**: auto-dial through call lists (Sales Hub Enterprise)
- **Call coaching**: review calls with scorecards (Enterprise)

### Conversation Intelligence (Enterprise)
- **Call transcription**: full transcription of sales calls
- **Breeze AI Call Summaries**: auto-generated call summaries with key points, action items, and next steps (Enterprise)
- **AI Coaching Suggestions**: Breeze AI identifies improvement areas and suggests coaching moments based on call patterns (Enterprise)
- **Keyword spotting**: flag when specific topics are mentioned (price, competitor, etc.)
- **Talk-to-listen ratio**: track who talks more
- **Objection tracking**: identify common objections
- **Sentiment analysis**: track emotional tone
- **Coaching scorecards**: review and rate rep calls
- **Playlist creation**: group calls by topic for training
- **AI topic recommendations**: suggested keywords based on call content

### Deal Management
- **Deal stages**: custom pipelines with probability percentages
- **Deal board**: Kanban view of pipeline
- **Deal amount & ROI tracking**: forecast revenue
- **Breeze AI Deal Insights**: AI-powered deal health scores, next-best-action recommendations, and risk flags based on historical patterns (Enterprise)
- **Line items**: associate products/services with deals
- **Discounts**: flat and percentage discounts
- **Recurring revenue**: track subscription deals
- **Auto-assignment**: round-robin or rules-based deal assignment
- **Deal split**: split revenue among multiple reps (Enterprise)
- **Forecasting**: team forecast, rep forecast, weighted pipeline, commit forecast
- **Breeze AI Forecasting Predictions**: ML-based predictive forecasts that auto-adjust based on deal velocity, rep activity, and historical close rates (Enterprise)
- **Forecast categories**: commit, best case, pipeline, closed won/lost

### Lead Management
- **Lead scoring**: behavioral + demographic scoring (Sales Hub Enterprise)
- **Predictive lead scoring via Breeze Intelligence**: ML-based lead quality scores enriched with intent data, firmographic signals, and purchase intent from Breeze Intelligence (Enterprise)
- **Lead rotation**: distribute leads round-robin
- **Lead status tracking**: New, Attempted to Contact, Connected, Qualified, Unqualified
- **Lead feed**: real-time notifications of new leads, email opens, page visits
- **Prospecting workspace**: focused view for lead outreach
- **Company insights**: technographics, recent funding, hiring news
- **LinkedIn Sales Navigator integration**: sync contacts and lists with deeper activity sync including InMail messages, profile views, and save-to-CRM actions (Pro+)

### Quotes (Pro+)
- **Quote builder**: create professional quotes from deal line items
- **Quote templates**: customizable PDF templates
- **Discount management**: per-line and overall discounts
- **Approval workflows**: quotes over threshold require manager approval
- **Electronic signature**: send with HubSpot native signing or DocuSign/HelloSign
- **Quote-to-close tracking**: see which quotes are viewed, signed, or expired
- **Product catalog**: manage products, prices, SKUs, descriptions
- **Payment links**: attach payment links to quotes (Commerce Hub)

### Playbooks (Pro+)
- **Playbook builder**: create guided workflows for reps
- **Question templates**: discovery questions, qualification questions
- **Ask Me Anything (AMA)**: dynamic response based on input
- **Playbook triggers**: auto-assign playbook based on deal stage
- **Playbook analytics**: adoption rates, completion rates
- **Sales methodology support**: MEDDIC, BANT, SPIN, Challenger, Command of the Message

### Reporting & Forecasting
- **Sales analytics**: calls, meetings, emails, sequences, deal velocity
- **Pipeline report**: by stage, by rep, by source
- **Deal conversion**: stage-to-stage conversion rates
- **Activity tracking**: calls, emails, meetings per rep
- **Forecasting**: custom forecast periods, team hierarchies
- **Multi-currency reporting**: convert and report deal amounts, revenue, and pipeline values in any base currency with real-time exchange rate support and per-currency breakdowns (Pro+)
- **Custom report builder**: drag-and-drop report creation
- **Dashboard sharing**: share with team, exec, or stakeholders
- **Attribution reporting**: which marketing sources produce closed-won deals

## Step-by-Step: Setting Up a Sequence (Sales Pro+)

1. Sales > Sequences > Create sequence
2. Name the sequence and set a goal (Reply, Meeting booked, Call me, etc.)
3. Add steps in order:
   - **Send email**: choose template or write from scratch
   - **Wait**: set delay (hours, days, or next business day)
   - **Automatic task**: log a call, create a todo for rep
   - **Manual task**: rep must complete before sequence proceeds
4. Set enrollment criteria:
   - Contacts must have email address
   - Not enrolled in another sequence targeting same goal
   - Lifecycle stage filters (e.g., Lead or SQL only)
5. Configure unenrollment triggers:
   - Contact replies (auto-detect reply or specific keywords)
   - Meeting booked
   - Deal stage changed to Closed Won/Lost
6. Set send limits: max emails per week per contact
7. Save and activate
8. To enroll contacts: go to contact record, click Enroll in Sequence
9. Monitor in Sequence dashboard: active, completed, replied, bounced

## Step-by-Step: Creating a Deal Pipeline

1. Sales > Pipelines > Create pipeline
2. Select object: Deals
3. Name pipeline (e.g., "Standard Sales Process")
4. Add stages (example):
   - Appointment Scheduled (1%)
   - Qualified to Buy (10%)
   - Presentation Scheduled (25%)
   - Decision Maker Bought-In (50%)
   - Contract Sent (75%)
   - Closed Won (100%)
   - Closed Lost (0%)
5. Configure stage-to-stage rules:
   - Which stages can move forward/backward
   - Required properties per stage (e.g., "Close date required from Contract Sent stage")
6. Add deal rotation rules (optional): round-robin, team-based
7. Save

## Step-by-Step: Creating a Quote

1. Open a deal → More → Create quote
2. Select quote template
3. Add line items from product library or custom items
4. Set discounts (per line or overall)
5. Add terms and conditions
6. Configure payment options (if Commerce Hub enabled)
7. Set expiration date (default: 30 days)
8. Add signature options: HubSpot native e-signature, DocuSign, PandaDoc
9. Preview quote as PDF
10. Send to contact (automatically creates engagement on timeline)

## Step-by-Step: Setting Up Sales Forecasting

1. Sales > Forecasting > Configure forecast
2. Choose forecast period (Monthly, Quarterly, Custom)
3. Set forecast categories:
   - **Commit**: deals rep is confident closing
   - **Best case**: deals likely but not certain
   - **Pipeline**: all open deals
4. Add team hierarchy (Enterprise): manager sees team forecasts
5. Configure filters: exclude certain deal types or pipelines
6. Forecast settings: default probability override for forecast calculation
7. Enable forecast notifications (email alerts when deals move)

## Limits That Matter

- Email tracking: Free (200/day), Pro/Enterprise (1,000/day)
- Email templates: 500 (Pro), unlimited (Enterprise)
- Sequences: 1,000 active enrollments per user (Enterprise: 2,000)
- Sequence steps: 50 per sequence
- Meeting links per user: 5 default + custom
- Playbooks: 50 (Pro), 500 (Enterprise)
- Teams: Free (1), Starter (3), Pro (15), Enterprise (unlimited)
- Sales rep seats: contact-based pricing
- Calling minutes: US/Canada only included (international billed per minute)
- Forecast periods: 8 (Pro), unlimited (Enterprise)
- Quotes per deal: 20 (Pro), 100 (Enterprise)
- Line items per quote: 50
- Deal splits: up to 15 (Enterprise)

## Use Cases

- Automate cold email outreach with sequences
- Track email opens and clicks to prioritize hot leads
- Manage multi-stage sales pipeline with Kanban board
- Create and send professional quotes with e-signature
- Forecast revenue with team-level rollups
- Coach reps using call recordings and conversation intelligence
- Route leads to the right reps automatically
- Track product-level performance with line items

## Common Gotchas

- Sequences auto-enroll but you must set unenrollment rules or contacts will receive unnecessary follow-ups if they've already replied
- Email tracking uses a 1x1 tracking pixel — some email clients block images
- Deleting a sequence unenrolls all contacts currently enrolled
- Call recording laws vary by state/country — HubSpot provides consent tones for some jurisdictions
- Quotes created without templates can't be edited later (clone + recreate)
- Forecast accuracy depends on proper deal stage → probability mapping
- LinkedIn Sales Navigator integration requires LinkedIn Sales Navigator seat
- Sequence reply detection is not 100% accurate (depends on email being in HubSpot-connected inbox)