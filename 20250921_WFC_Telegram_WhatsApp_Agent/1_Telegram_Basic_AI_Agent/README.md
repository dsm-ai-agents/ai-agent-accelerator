# Telegram AI Agent (Basic Test Bot) – Documentation

This document describes a **basic Telegram AI Agent workflow** in n8n.  
It is meant as a **test setup** before implementing the full Lead Qualification Agent.  

The workflow file used:  
`[In Class] Telegram API - 21 SEP 2025.json`:contentReference[oaicite:0]{index=0}

---

## 📌 Overview

This is a simple 4-node workflow:  

1. **Telegram Trigger** → Captures incoming messages  
2. **AI Agent** → Sends the message to an AI model  
3. **Google Gemini Chat Model** → Provides the response  
4. **Send a text message** → Returns the reply to Telegram  

This loop allows you to test that your Telegram bot and AI integration are working end-to-end.  

---

## ⚙️ Node by Node Setup

### 1. Telegram Trigger
- **Node type:** `n8n-nodes-base.telegramTrigger`  
- **Purpose:** Starts the workflow whenever a user sends a message to your Telegram bot.  
- **Key Config:**  
  - Credentials: `Telegram API` (BotFather token)  
  - Captures:  
    - `message.text` → user’s message  
    - `message.chat.id` → user’s chat ID  
    - `message.from.first_name` → user’s name  

---

### 2. AI Agent
- **Node type:** `@n8n/n8n-nodes-langchain.agent`  
- **Purpose:** Acts as the middle logic layer between Telegram input and the LLM.  
- **Config:**  
  - Takes input: `={{ $json.message.text }}` (user message from Telegram)  
  - For now, no complex prompt — just passes the text along.  
- **Why:** This node is flexible — later you can insert prompts (like the Lead Qualification flow).  

---

### 3. Google Gemini Chat Model
- **Node type:** `@n8n/n8n-nodes-langchain.lmChatGoogleGemini`  
- **Purpose:** Provides the AI response.  
- **Config:**  
  - Credentials: `KN DSM Google Gemini(PaLM) API`  
  - Connected as the LLM backend for the AI Agent node.  

---

### 4. Send a Text Message
- **Node type:** `n8n-nodes-base.telegram`  
- **Purpose:** Sends the AI Agent’s response back to the user in Telegram.  
- **Key Config:**  
  - Chat ID: `={{ $('Telegram Trigger').item.json.message.chat.id }}`  
  - Text: `={{ $json.output }}` (the AI response)  
  - Credentials: `Telegram API` (same as Trigger node)  

---

## ✅ Test Use Case

1. User sends any message in Telegram.  
2. Bot replies with an AI-generated response (using Google Gemini).  
3. Confirms that:
   - Telegram connection works  
   - AI Agent node works  
   - Gemini model responds correctly  
   - Response is sent back  

---

## 🚀 Next Step

Once this test workflow is verified:  
- Replace the **AI Agent prompt** with the **Lead Qualification prompt**.  
- Add logic for **BANT criteria**.  
- Store responses in a CRM or Google Sheet.  

---

This basic test ensures your **Telegram AI bot is functional** before building the full **Lead Qualification Bot**.  
