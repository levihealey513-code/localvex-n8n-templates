# LocalVex n8n Automation Templates

> Production-ready n8n workflow templates for local business marketing automation. Built by LocalVex — Springboro, Ohio.

---

## Folder Structure

```
/localvex-n8n-templates
  /email-campaigns
    welcome-sequence.json         # 3-part new subscriber welcome flow
    follow-up-drip.json           # 5-part nurture sequence
    re-engagement.json            # Win back 60+ day inactive subscribers
  /lead-gen
    fb-lead-to-ghl.json           # Facebook Lead Ads -> GHL CRM auto-contact
    website-form-to-crm.json      # Web form submission -> GHL pipeline
    google-lead-to-ghl.json       # Google Ads leads -> GHL
  /client-retention
    missed-call-textback.json     # Missed call -> instant SMS reply (Twilio)
    review-request-sms.json       # Post-service -> Google review request
    appointment-reminder.json     # 24hr + 1hr appointment SMS reminder
  /reporting
    weekly-client-report.json     # Pull stats -> Google Sheet -> email PDF
    monthly-summary.json          # Monthly KPI summary auto-email
  /client-onboarding
    new-client-notify.json        # Contract signed -> Slack/email notify
    welcome-email-trigger.json    # GHL tag added -> trigger welcome sequence
  /social-media
    post-scheduler.json           # Schedule posts across platforms
    lead-magnet-delivery.json     # Form fill -> deliver PDF lead magnet
  README.md
```

---

## How to Use These Templates

### Step 1 — Import into n8n
1. Open your n8n instance (cloud or self-hosted)
2. Click **+ New Workflow**
3. Click the **...** menu > **Import from file**
4. Select the `.json` file from this repo
5. Click **Save**

### Step 2 — Configure Credentials
Each workflow uses credentials you must connect once:
- **GHL (GoHighLevel)** — API key from GHL Settings > Integrations
- **Gmail/SMTP** — Google OAuth or SMTP credentials
- **Twilio** — Account SID + Auth Token from twilio.com/console
- **Google Sheets** — Google OAuth service account
- **Facebook Lead Ads** — Facebook Business API token

> Tip: In n8n, go to Settings > Credentials and add each once. All workflows using that service will share it.

### Step 3 — Activate
1. Toggle the workflow to **Active**
2. Test with a sample trigger
3. Monitor the Executions tab for errors

---

## Core Workflows — Quick Reference

| Workflow | Trigger | Action | Best For |
|---|---|---|---|
| FB Lead to GHL | New Facebook lead | Create GHL contact + add to pipeline | Restaurants, gyms, salons |
| Missed Call Textback | Missed call in GHL | Send instant SMS | ANY local business |
| Welcome Sequence | GHL tag: new-client | Send 3-email welcome series | All clients |
| Review Request | GHL tag: job-complete | Send review request SMS 2hr after | Service businesses |
| Weekly Report | Cron (every Monday 8am) | Pull data, update Sheet, email client | All clients |
| Appointment Reminder | 24hr before appointment | SMS reminder to contact | Clinics, contractors |

---

## Business Types & Recommended Automations

### Restaurants / Food Service
- Missed Call Textback
- Review Request SMS
- Birthday email campaign
- Loyalty re-engagement drip

### Gyms / Fitness Studios
- FB Lead to GHL + instant follow-up SMS
- Free trial welcome sequence
- No-show re-engagement
- Monthly challenge email

### Home Service (HVAC, Plumbing, Roofing)
- Missed Call Textback (highest ROI)
- Estimate follow-up sequence
- Seasonal campaign (pre-summer AC, pre-winter heat)
- Review request post-job

### Medical / Dental / Chiropractic
- Appointment reminder (24hr + 1hr)
- Post-visit review request
- Re-activation campaign (patients 6mo+ inactive)
- New patient welcome sequence

### Salons / Spas
- Booking confirmation + reminder
- Rebooking drip (every 4-6 weeks)
- Review request
- VIP loyalty campaign

### Real Estate
- Lead magnet delivery
- Buyer/seller nurture drip
- Open house follow-up sequence
- Listing alert automation

---

## Deliverability Checklist (Run Before Every Client Campaign)

- [ ] SPF record added to client domain DNS
- [ ] DKIM record added and verified
- [ ] DMARC policy set (start with p=none)
- [ ] Sending domain warmed up (start at 50/day, scale over 2 weeks)
- [ ] List cleaned — remove hard bounces, unsubscribes
- [ ] Test send via mail-tester.com (aim for 9+/10 score)
- [ ] Subject line tested for spam triggers (avoid ALL CAPS, excessive !!!!)
- [ ] Unsubscribe link present in every email
- [ ] Physical address in footer (CAN-SPAM requirement)

---

## Maintainer

Levi Healey — LocalVex | localvex.com
Springboro, Ohio

---

*Last updated: March 2026*
