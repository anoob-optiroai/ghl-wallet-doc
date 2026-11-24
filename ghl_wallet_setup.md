# GHL Wallet System Setup Guide (Custom Fields + WhatsApp & Email Templates)

This document explains how to set up a Wallet System inside GoHighLevel, including:
- Custom Fields (Wallet Balance + Topup URL)
- Workflow field mapping
- WhatsApp Templates
- Email Templates

---

# 1. Custom Field Setup

Create two contact custom fields.

## Field 1: Wallet Balance

Stores the customer's current wallet balance.

- Field Type: Single Line
- Field Name: Wallet Balance
- Internal Key (recommended): contact.wallet_balance

## Field 2: Topup URL

Stores the customer's personal wallet top-up link, so every alert can include a "recharge now" link.

- Field Type: Single Line
- Field Name: Topup URL
- Internal Key (recommended): contact.topup_url

---

# 2. Workflow Field Mapping

In the notification workflow (trigger: Inbound Webhook), add an **Update Contact Field** action before the WhatsApp/email actions and map:

| Custom Field | Value from Inbound Webhook Trigger |
|---|---|
| Wallet Balance | Inbound Webhook Trigger → Balance Formatted |
| Topup URL | Inbound Webhook Trigger → Topup Url |

The webhook sends `topupUrl` with every alert (e.g. `https://dashboard.ghlwallet.app/topup?locationId=...`, or your custom domain if one is set). Click "Test" on the webhook in the GHL Wallet app first so these fields appear in the mapping list.

---

# 3. WhatsApp Templates Setup

## Folder Creation

Create a folder:
- Name: GHL WALLET

---

## Template 1: wallet_balance_level_1

- Category: Utility  
- Language: English  

Message:

💰 Wallet Balance Running Low

Hi {{1}},
Your current wallet balance is {{2}}, and based on your recent usage, it may get exhausted soon.

To ensure uninterrupted service, please add funds now:
{{3}}

Custom Values:
- {{1}} → {{contact.first_name}}
- {{2}} → {{contact.wallet_balance}}
- {{3}} → {{contact.topup_url}}

---

## Template 2: wallet_balance_level_2

- Category: Utility  
- Language: English  

Message:

🚨 Urgent: Wallet Balance Almost Exhausted

Hi {{1}},
Your wallet balance is critically low ({{2}}).

Services may be interrupted anytime if the balance is not recharged immediately.

Recharge now: {{3}}

Custom Values:
- {{1}} → {{contact.first_name}}
- {{2}} → {{contact.wallet_balance}}
- {{3}} → {{contact.topup_url}}

---

## Template 3: wallet_balance_level_0

- Category: Utility  
- Language: English  

Message:

🔒 Wallet Balance Exhausted

Hi {{1}},
Your wallet balance has been fully used.

Services are currently paused until funds are added.

Add funds here to resume: {{2}}

Custom Values:
- {{1}} → {{contact.first_name}}
- {{2}} → {{contact.topup_url}}

---

## Template 4: wallet_balance_exhausted_post_zero

- Category: Utility  
- Language: English  

Message:

🔒 Wallet Balance Exhausted

Hi {{1}},
Your wallet balance has been fully used.

Services are currently paused until funds are added.

Add funds here to resume: {{2}}

Custom Values:
- {{1}} → {{contact.first_name}}
- {{2}} → {{contact.topup_url}}

---

## Template 5: wallet_top_up_successful

- Category: Utility  
- Language: English  

Message:

✅ Wallet Top-Up Successful

Hi {{1}},
Your wallet has been successfully recharged.

💰 Current Balance: {{2}}

You can now continue using all services without interruption.

Thank you!

Custom Values:
- {{1}} → {{contact.first_name}}
- {{2}} → {{contact.wallet_balance}}

---

# 4. Email Templates Setup

Create these in Marketing → Emails → Templates, inside a folder named **GHL WALLET**. They use the same custom fields as the WhatsApp templates, so the workflow's Update Contact Field step must run before the Send Email step.

Merge fields used:
- {{contact.first_name}} → customer's first name
- {{contact.wallet_balance}} → current balance (e.g. ₹450.00)
- {{contact.topup_url}} → customer's personal top-up link

---

## Email 1: wallet_balance_level_1

- Subject: 💰 Your wallet balance is running low
- Preview text: Add funds now to avoid any interruption.

Body:

Hi {{contact.first_name}},

Your current wallet balance is **{{contact.wallet_balance}}**. Based on your recent usage, it may run out soon.

To keep your services running without interruption, please add funds now.

If the button doesn't work, copy this link into your browser:
{{contact.topup_url}}

Thank you!

Button:
- Text: Recharge Wallet
- Link: {{contact.topup_url}}

---

## Email 2: wallet_balance_level_2

- Subject: 🚨 Urgent: your wallet balance is almost exhausted
- Preview text: Recharge now to avoid service interruption.

Body:

Hi {{contact.first_name}},

Your wallet balance is critically low: **{{contact.wallet_balance}}**.

Your services may be interrupted at any time if the wallet is not recharged immediately.

If the button doesn't work, copy this link into your browser:
{{contact.topup_url}}

Thank you!

Button:
- Text: Recharge Wallet
- Link: {{contact.topup_url}}

---

## Email 3: wallet_balance_level_0

- Subject: 🔒 Your wallet balance is exhausted
- Preview text: Services are paused. Add funds to resume.

Body:

Hi {{contact.first_name}},

Your wallet balance has been fully used, and your services are currently paused.

Add funds to your wallet to resume them right away.

If the button doesn't work, copy this link into your browser:
{{contact.topup_url}}

Thank you!

Button:
- Text: Recharge Wallet
- Link: {{contact.topup_url}}

---

## Email 4: wallet_balance_exhausted_post_zero

- Subject: 🔒 Reminder: your wallet is still empty
- Preview text: Your services remain paused until funds are added.

Body:

Hi {{contact.first_name}},

Your wallet balance is still exhausted (**{{contact.wallet_balance}}**), so your services remain paused.

Recharge your wallet to resume them.

If the button doesn't work, copy this link into your browser:
{{contact.topup_url}}

Thank you!

Button:
- Text: Recharge Wallet
- Link: {{contact.topup_url}}

---

## Email 5: wallet_top_up_successful

- Subject: ✅ Wallet top-up successful
- Preview text: Your wallet has been recharged.

Body:

Hi {{contact.first_name}},

Your wallet has been recharged successfully.

💰 Current balance: **{{contact.wallet_balance}}**

You can continue using all services without interruption. Top up again anytime here:
{{contact.topup_url}}

Thank you!

---

# 5. Notes

- Ensure WhatsApp templates are approved before use
- Map both custom fields (Wallet Balance, Topup URL) in the workflow before the WhatsApp step, so the template variables are filled
- When submitting templates for approval, use a sample like `https://dashboard.ghlwallet.app/topup?locationId=abc123` for the Topup URL variable
- Maintain consistent naming for templates
- In each email template, set the button link to the {{contact.topup_url}} merge field (not a fixed URL), so every customer gets their own top-up link
- Send a test email to yourself from the template to check the link opens your top-up page

---

# 6. Outcome

- Automated wallet alerts
- Better user communication
- Smooth wallet experience for customers
