# Lead Qualification via Telegram Bot (BANT Framework)

This document explains how to set up a **Telegram Bot for lead qualification** using **BANT criteria** (Budget, Authority, Need, Timeline).  
It includes both the **framework for development** and a **downloadable prompt file**.

---

## 📌 Why BANT?
BANT is a classic sales qualification framework:
- **B**udget → Do they have money to buy?  
- **A**uthority → Are they the decision-maker?  
- **N**eed → Do they need your solution?  
- **T**imeline → When will they buy?  

Using this in a **Telegram Bot workflow** helps automate lead collection, qualification, and scoring.

---

## ⚙️ Development Framework

### 1. **Trigger**
- Use **Telegram Trigger node** in n8n to capture incoming messages.  
- Extract:
  - `message.text`  
  - `chat.id`  
  - `from.first_name`

### 2. **Memory Tracking**
- Store lead information across multiple messages:
  - Name (from Telegram profile or first user input)  
  - Email  
  - Budget  
  - Timeline  
  - Authority  

### 3. **Conversation Flow**
- Bot should ask **one missing piece of info at a time**.  
- Prioritized sequence: **Name → Email → Budget → Timeline → Authority**.  
- Once all details are collected → Send **thank you message** and mark lead as qualified.  

### 4. **Answer Normalization**
- Convert multiple-choice answers (A/B/C/D) into full-text values.  
- Example:  
  - Input: `A` → Output: `"Under $1,000/month"`

### 5. **Lead Scoring**
- Add logic to score based on urgency & authority:
  - High urgency + decision authority = **HOT LEAD**  
  - Medium urgency + partial authority = **WARM LEAD**  
  - Low urgency + no authority = **COLD LEAD**  

### 6. **Final Output**
- Return structured JSON for logging, CRM integration, or further automation.

---

## 📝 Prompt File

Instead of embedding the full prompt here, you can download and reuse it:

👉 [LEAD_QUAL_PROMPT_FOR_DOWNLOAD_21SEP2025.txt](./LEAD_QUAL_PROMPT_FOR_DOWNLOAD_21SEP2025.txt)

This file contains the **exact ready-to-use prompt** for your Telegram → n8n → AI qualification workflow.  

---

## 🚀 Next Steps

- Add this into your **Telegram → AI Agent → CRM (HubSpot/Sheets)** pipeline.  
- Log all qualified leads automatically.  
- Trigger **email follow-ups** or assign to a sales rep instantly.  

---

✅ This framework ensures your Telegram Bot doesn’t just chat — it **collects, qualifies, and scores leads** automatically.  
