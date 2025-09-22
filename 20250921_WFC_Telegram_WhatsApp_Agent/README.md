# AI Agent Setup – Master Guide

This repository is structured to help you **step-by-step** set up and test both **Telegram** and **WhatsApp AI Agents**.  
By following the order of the folders, you can start with a **basic test bot** and gradually progress to a **Lead Qualification Agent** using the BANT framework.

---

## 📂 Folder Structure

### 0_LEAD_PROMPT_GUIDE
- Contains the **Lead Qualification Prompt Guide**.  
- This explains the **BANT process** (Budget, Authority, Need, Timeline) and how to use prompts to qualify leads.  
- Start here to understand the framework before building advanced agents.

---

### 1_Telegram_Basic_AI_Agent
- A **basic Telegram AI bot** setup using n8n.  
- Nodes:
  1. **Telegram Trigger** – captures messages  
  2. **AI Agent** – forwards text to AI model  
  3. **Google Gemini Chat Model** – generates response  
  4. **Send a Text Message** – replies to user in Telegram  
- Purpose: ✅ Test Telegram bot integration with AI before adding business logic.

---

### 2_Telegram_Lead_Qualification_Agent
- Builds on the basic agent.  
- Adds the **Lead Qualification Prompt** to guide conversation using BANT.  
- Bot asks for missing info step by step (email, budget, timeline, authority).  
- Ends with a **scored lead output** (HOT/WARM/COLD).  
- Purpose: 🎯 Use Telegram to **collect, qualify, and score leads** automatically.

---

### 3_WhatsApp_Basic_AI_Agent
- A **basic WhatsApp AI bot** setup using n8n.  
- Nodes:
  1. **WhatsApp Trigger** – captures messages  
  2. **AI Agent** – forwards input to AI  
  3. **Google Gemini Chat Model** – generates response  
  4. **Send Message** – replies to user in WhatsApp  
- Purpose: ✅ Test WhatsApp Business API + AI connectivity.

---

### 4_WhatsApp_Lead_Qualification_Agent
- Builds on the basic WhatsApp agent.  
- Adds the **Lead Qualification Prompt** for BANT-based conversations.  
- Bot collects:
  - Name  
  - Email  
  - Budget  
  - Timeline  
  - Authority  
- Produces a **structured JSON output** for CRM or follow-up.  
- Purpose: 🎯 Automate lead qualification directly from WhatsApp chats.

---

## 🚀 Recommended Execution Process

1. **Understand the Prompt Framework**  
   - Read `0_LEAD_PROMPT_GUIDE` carefully.  
   - Familiarize yourself with BANT questions & scoring.  

2. **Test Telegram AI Bot**  
   - Deploy `1_Telegram_Basic_AI_Agent`.  
   - Confirm that the bot responds with AI-generated messages.  

3. **Add Lead Qualification to Telegram**  
   - Upgrade to `2_Telegram_Lead_Qualification_Agent`.  
   - Validate step-by-step conversation flow.  

4. **Test WhatsApp AI Bot**  
   - Deploy `3_WhatsApp_Basic_AI_Agent`.  
   - Confirm message send/receive flow works.  

5. **Add Lead Qualification to WhatsApp**  
   - Upgrade to `4_WhatsApp_Lead_Qualification_Agent`.  
   - Confirm leads are collected and scored properly.  

---

## ✅ Outcome

By completing these steps, you will have:

- A **working Telegram AI Agent** for both testing and qualification.  
- A **working WhatsApp AI Agent** for both testing and qualification.  
- A **scalable framework** to expand into other use cases (customer support, appointment booking, etc.).  

---

## 📌 Notes

- Keep your **API tokens** (Telegram, WhatsApp, Gemini) safe.  
- Always test **basic agents first** before adding prompts.  
- Store qualified leads in a **CRM, Google Sheets, or Airtable** for tracking.  

---

🔥 This process ensures that you move from **simple AI response testing** → **structured qualification workflows** step by step.  
