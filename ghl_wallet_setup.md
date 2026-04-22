# GHL Wallet System Setup Guide (Custom Field + WhatsApp + Workflows)

This document explains how to set up a Wallet System inside GoHighLevel, including:
- Custom Field
- WhatsApp Templates
- Workflows for Plan Onboarding

---

# 1. Custom Field Setup

Create a custom field to store wallet balance.

- Field Type: Single Line
- Field Name: Wallet Balance
- Internal Key (recommended): contact.wallet_balance

---

# 2. WhatsApp Templates Setup

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

To ensure uninterrupted service, please add funds now.

Custom Values:
- {{1}} → {{contact.first_name}}
- {{2}} → {{contact.wallet_balance}}

---

## Template 2: wallet_balance_level_2

- Category: Utility  
- Language: English  

Message:

🚨 Urgent: Wallet Balance Almost Exhausted

Hi {{1}},
Your wallet balance is critically low ({{2}}).

Services may be interrupted anytime if the balance is not recharged immediately.

Custom Values:
- {{1}} → {{contact.first_name}}
- {{2}} → {{contact.wallet_balance}}

---

## Template 3: wallet_balance_level_0

- Category: Utility  
- Language: English  

Message:

🔒 Wallet Balance Exhausted

Hi {{1}},
Your wallet balance has been fully used.

Services are currently paused until funds are added.

Custom Values:
- {{1}} → {{contact.first_name}}

---

## Template 4: wallet_balance_exhausted_post_zero

- Category: Utility  
- Language: English  

Message:

🔒 Wallet Balance Exhausted

Hi {{1}},
Your wallet balance has been fully used.

Services are currently paused until funds are added.

Custom Values:
- {{1}} → {{contact.first_name}}

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

# 3. Workflow Setup

## Folder Creation

Create a workflow folder:
- Name: Onboarding

---

## Workflow 1: Onboarding_basic_plan

- Trigger: None (Manual / API Trigger)
- Action:
  - Type: Webhook
  - Method: POST
  - URL: Plan 1 (Basic) Webhook URL

---

## Workflow 2: Onboarding_pro_plan

- Trigger: None (Manual / API Trigger)
- Action:
  - Type: Webhook
  - Method: POST
  - URL: Plan 2 (Pro) Webhook URL

---

## Workflow 3: Onboarding_enterprise_plan

- Trigger: None (Manual / API Trigger)
- Action:
  - Type: Webhook
  - Method: POST
  - URL: Plan 3 (Enterprise) Webhook URL

---

# 4. Recommended Automation Logic (Optional)

- Level 1 → Low Balance → wallet_balance_level_1
- Level 2 → Critical → wallet_balance_level_2
- Level 3 → Zero → wallet_balance_level_0
- On Top-up → wallet_top_up_successful

---

# 5. Notes

- Ensure WhatsApp templates are approved
- Replace webhook URLs
- Map custom fields correctly

---

# 6. Outcome

- Automated wallet alerts
- Controlled service usage
- Smooth onboarding via workflows
