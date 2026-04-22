# GHL Wallet System Setup Guide (Custom Field + WhatsApp Templates)

This document explains how to set up a Wallet System inside GoHighLevel, including:
- Custom Field
- WhatsApp Templates

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

# 3. Notes

- Ensure WhatsApp templates are approved before use
- Map custom field correctly in contacts
- Maintain consistent naming for templates

---

# 4. Outcome

- Automated wallet alerts
- Better user communication
- Smooth wallet experience for customers
