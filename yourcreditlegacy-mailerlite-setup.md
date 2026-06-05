# Your Credit Legacy — MailerLite Setup Guide
## Lead Magnet Flow + 5-Email Nurture Sequence

This guide walks you through wiring the "Free Credit Legacy Playbook" lead-magnet form on `index.html` to your MailerLite account so new subscribers automatically receive the PDF and enter a 5-email nurture sequence.

**Estimated setup time:** 30–40 minutes

---

## 1. Create Your MailerLite Account

1. Go to [mailerlite.com](https://www.mailerlite.com) and sign up using **info@yourcreditlegacy.com**
2. Verify your domain in **Settings → Domains** — required so your emails land in inboxes, not spam
3. Complete your sender details:
   - **From name:** Your Credit Legacy
   - **From email:** info@yourcreditlegacy.com
   - **Reply-to:** info@yourcreditlegacy.com
4. Under **Settings → Domains**, add the SPF, DKIM, and DMARC records to your Hostinger DNS — MailerLite will show you exactly what to add

---

## 2. Create a Custom Field for Credit Score

You need a custom field to store the credit score range each lead submits.

1. Go to **Subscribers → Fields → Add field**
2. **Field name:** `credit_score`
3. **Field type:** Text
4. Save

---

## 3. Create the Subscriber Group

1. Go to **Subscribers → Groups → Create group**
2. Name it: **Credit Playbook Leads**
3. Save and **copy the Group ID** (visible in the URL — looks like `123456789`)

---

## 4. Create the Embedded Form

1. Go to **Forms → Embedded forms → Create form**
2. Name: **Credit Playbook — Free Guide Download**
3. Assign to group: **Credit Playbook Leads**
4. Add these fields (names must match exactly):
   - `email` — required
   - `name` — built-in
   - `phone` — built-in
   - `credit_score` — the custom field you created in Step 2
5. Set success behavior to: *Show success message* (the site handles its own UI)
6. Save. From the embed code screen, copy:

```
https://assets.mailerlite.com/jsonp/ACCOUNT_ID/forms/FORM_ID/subscribe
```

You need:
- **Account ID** — the number after `/jsonp/`
- **Form ID** — the number after `/forms/`

---

## 5. Wire the Three IDs into the Site

Open `index.html`. Around line 780, find the form tag:

```html
<form class="lf-form" id="leadForm"
      data-ml-form
      data-ml-account-id="REPLACE_WITH_ML_ACCOUNT_ID"
      data-ml-form-id="REPLACE_WITH_ML_FORM_ID"
      data-ml-group-id="REPLACE_WITH_ML_GROUP_ID"
      novalidate>
```

Replace:
- `REPLACE_WITH_ML_ACCOUNT_ID` → your Account ID
- `REPLACE_WITH_ML_FORM_ID` → your Form ID
- `REPLACE_WITH_ML_GROUP_ID` → your Group ID

Save the file and redeploy to Hostinger.

---

## 6. Set Up the Automated PDF Delivery (Email 1)

This sends the Playbook the instant someone subscribes.

1. Go to **Automations → Create automation**
2. Name: **Credit Playbook — Nurture Sequence**
3. **Trigger:** *When a subscriber joins a group* → **Credit Playbook Leads**
4. Add step: **Email** (send immediately — 0 minute delay)

### Email 1 — Instant Delivery

**Subject:** Your Credit Legacy Playbook is here

**Preview text:** 8 pages. The exact system we use. Start tonight.

**Body:**

```
Hi {$name},

Your free copy of The Credit Legacy Playbook is ready — download it below.

Inside you'll find:
- The 5 factors that control your score (and how to move each one)
- A week-by-week 90-day action plan
- The exact dispute letter structure our specialists use
- What can and can't be removed from your report
- How to unlock business funding once your credit is repaired

→ Download The Credit Legacy Playbook: [attach PDF or link to credit_repair_guide.pdf on your site]

This isn't generic advice. It's the same framework we walk our clients through — and it works.

If you have any questions as you read through it, just reply to this email. We read every response.

Talk soon,

Your Credit Legacy Team
940-220-0760 | info@yourcreditlegacy.com
yourcreditlegacy.com
```

5. **Attach the PDF** — upload `credit_repair_guide.pdf` from the ZIP to this email step (or host it at `yourcreditlegacy.com/credit_repair_guide.pdf` and use a link)
6. Set delay: **Immediately (0 minutes)**
7. Save — do NOT activate yet, finish all 5 emails first

---

## 7. The Full 5-Email Nurture Sequence

Add each email as a new step in the same automation after Email 1.

---

### Email 2 — Day 3: Your Score, Explained

**Delay:** 3 days after Email 1

**Subject:** Why your credit score is lower than it should be

**Preview text:** Most people don't know about these silent score killers.

**Body:**

```
Hi {$name},

Most people with damaged credit have the same story:

They did everything "right" — paid some bills on time, never went bankrupt —
and still can't get approved for a car, an apartment, or a business loan.

Here's why: it's usually not one big thing. It's a combination of smaller
items that stack up silently:

- A collection account from 4 years ago that never got resolved
- A hard inquiry from a credit application you forgot about
- Credit utilization that's too high across two or three cards
- An account that's reporting an incorrect balance

The Playbook we sent walks through each of these. But if you'd rather have
us look at your actual report and tell you exactly what's holding you back —
that's what we do.

A free credit analysis takes about 20 minutes. No obligation.

→ Get my free analysis: https://pulse.disputeprocess.com/jsp/custom_form.jsp?tab_id=N0pOZWtMN1QySTNrelRXd0VnK2JVZz09&cust_type=2&company_id=MnJnNllMZUk5T2hSZy8wMmlwdzdUQT09&isLinkFromIframe=1&redirect_url=

Your Credit Legacy Team
```

---

### Email 3 — Day 7: A Real Client Result

**Delay:** 4 days after Email 2 (7 days total)

**Subject:** From 541 to 718 in 87 days

**Preview text:** Here's exactly what we did.

**Body:**

```
Hi {$name},

One of our clients came to us with a 541 credit score.

She had three collections, two hard inquiries from a car loan she didn't
get approved for, and a charge-off from 2021.

Within 87 days:
- All three collections were removed
- Both unauthorized inquiries were disputed and deleted
- Her score jumped to 718
- She got approved for the apartment she'd been trying to rent for a year

This isn't unusual. It's what a focused, properly executed dispute strategy
looks like.

If you're sitting on a score that's lower than it should be, the Playbook
you downloaded is step one. Step two is letting us handle it for you.

→ Apply now — it's free to start: https://signup.yourcreditlegacy.com/

Your Credit Legacy Team
940-220-0760 | info@yourcreditlegacy.com
```

---

### Email 4 — Day 14: Business Funding

**Delay:** 7 days after Email 3 (14 days total)

**Subject:** Your credit score is blocking more than you think

**Preview text:** Most people don't realize this affects their business too.

**Body:**

```
Hi {$name},

Here's something most credit repair companies won't tell you:

Your personal credit score directly affects your ability to access
business funding — even if your business is profitable.

Lenders look at your personal credit when evaluating:
- SBA loans
- Business lines of credit
- Equipment financing
- Business credit cards

A score below 650 can get you denied outright. A score above 700 opens
doors to $50K–$500K in business capital.

This is why we don't just repair credit. We get our clients
business-funding-ready.

Once your score hits the right threshold, we help you identify the right
lenders and structure the right application.

→ See our Business Funding services: https://yourcreditlegacy.com/#services
→ Or apply to start today: https://signup.yourcreditlegacy.com/

Your Credit Legacy Team
```

---

### Email 5 — Day 21: Last Nudge + Free Monitoring

**Delay:** 7 days after Email 4 (21 days total)

**Subject:** One more thing we want you to have

**Preview text:** A 7-day free trial — no credit card needed.

**Body:**

```
Hi {$name},

One last thing before we give you some space:

If you haven't already, sign up for a 7-day free trial of SmartCredit.

It gives you:
- Daily score updates from all 3 bureaus
- Real-time alerts for any new inquiries or changes
- Identity theft protection

This is especially useful if you're in the middle of disputing items —
you'll see changes hit your report in real time instead of waiting for a
monthly update.

→ Start my free 7-day SmartCredit trial: https://www.smartcredit.com/?PID=19180

And whenever you're ready to move forward — whether that's credit repair,
business funding, or just a free 20-minute call — we're here.

→ Get started: https://pulse.disputeprocess.com/jsp/custom_form.jsp?tab_id=N0pOZWtMN1QySTNrelRXd0VnK2JVZz09&cust_type=2&company_id=MnJnNllMZUk5T2hSZy8wMmlwdzdUQT09&isLinkFromIframe=1&redirect_url=

Your Credit Legacy Team
940-220-0760 | info@yourcreditlegacy.com
yourcreditlegacy.com
```

---

## 8. Activate the Automation

Once all 5 emails are set up:
1. Review each email one more time
2. Click **Activate** on the automation
3. It will now trigger automatically every time someone fills in the form on the site

---

## 9. Test the Full Flow

1. Open `index.html` (live on Hostinger) in an incognito browser tab
2. Scroll to the "Free Resource" section
3. Fill in the form with a personal email address (not info@…)
4. Submit — you should see the green success card and the PDF should auto-download
5. Check that email's inbox — the Playbook delivery email should arrive within 1–2 minutes
6. Confirm the subscriber appears in MailerLite under **Credit Playbook Leads** with correct fields
7. Wait 3 days (or manually trigger in MailerLite) to confirm Email 2 sends
8. Delete the test subscriber before going live

---

## 10. Sequence Summary

| # | Day | Subject | Goal |
|---|-----|---------|------|
| 1 | 0   | Your Credit Legacy Playbook is here | Deliver PDF immediately |
| 2 | 3   | Why your credit score is lower than it should be | Educate + soft CTA |
| 3 | 7   | From 541 to 718 in 87 days | Social proof + apply CTA |
| 4 | 14  | Your credit score is blocking more than you think | Business funding upsell |
| 5 | 21  | One more thing we want you to have | SmartCredit + final CTA |

---

## 11. Troubleshooting

**Form submits but nothing appears in MailerLite:**
- Confirm all three IDs (Account, Form, Group) are correct in `index.html`
- Open browser DevTools → Console — look for a CORS or 404 error from `assets.mailerlite.com`
- Make sure the form is **Published** in MailerLite (not draft)

**PDF delivery email going to spam:**
- Complete domain verification (SPF, DKIM, DMARC) in MailerLite Settings → Domains
- Hostinger DNS usually takes 15–30 minutes to propagate

**Subscribers come in without name/phone:**
- Confirm `name` and `phone` are enabled fields on the form inside MailerLite (not hidden)

---

## 12. What's Already Done on the Site

- Form HTML is live in `index.html` with correct MailerLite field names, honeypot, and accessibility labels
- JavaScript submits to MailerLite via JSONP and handles the success/error UI automatically
- PDF auto-downloads on form submission as a fallback (even if email is delayed)
- A "Download Guide Now" button appears on the success card
- All 3 IDs are clearly marked as `REPLACE_WITH_...` placeholders — just swap them in

**You only need to do Steps 1–8 above. The site is wired and waiting.**

---

Questions? Reach out at info@yourcreditlegacy.com or call 940-220-0760.

— Your Credit Legacy
