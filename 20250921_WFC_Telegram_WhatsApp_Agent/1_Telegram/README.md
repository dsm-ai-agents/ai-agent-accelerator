# How to Configure Telegram Bot on n8n

This guide shows the steps to connect your Telegram Bot with n8n. Replace the example placeholders with your own bot details.

---

## Prerequisites

- Telegram account  
- n8n instance (cloud or self-hosted)  
- Access to [BotFather](https://t.me/botfather) in Telegram  
- Public HTTPS URL for n8n if using webhooks  

---

## Example Bot Details (Replace with Yours)

| Field        | Example Value                       |
|--------------|-------------------------------------|
| Bot Name     | `Your Bot Display Name`             |
| Bot Username | `your_bot_username_bot`             |
| Bot Token    | `1234567890:ABCdEfGhIjKlMnOpQrStUv` |
| Chat ID      | `123456789`                         |
| Bot Link     | `https://t.me/your_bot_username_bot`|

---

## Configuration Steps

1. **Create a Bot in Telegram**
   - Open [BotFather](https://t.me/botfather) in Telegram.  
   - Run `/start` → `/newbot`.  
   - Enter your **Bot Display Name**.  
   - Enter a unique **Bot Username** (must end with `_bot`).  
   - Copy the **Bot Token** provided.  

2. **(Optional) Disable Privacy Mode**
   - In BotFather, run `/setprivacy`.  
   - Choose your bot and set privacy to **Disabled** if you want to capture all messages in group chats.  

3. **Add Telegram Credentials in n8n**
   - Go to **Credentials** in n8n.  
   - Create new credentials of type **Telegram**.  
   - Paste your Bot Token.  
   - Name the credential (e.g., `Telegram – Lead Agent`).  
   - Save.  

4. **Create a Workflow in n8n**
   - Add **Telegram Trigger** node.  
     - Operation: `On New Message`.  
     - Select your Telegram credential.  
   - Add **Telegram → Send Message** node.  
     - Chat ID: use your user or group chat ID (e.g., `123456789`).  
     - Text: type your response message.  

5. **Set Webhook (if required)**
   - Telegram bots rely on webhooks.  
   - Ensure your n8n instance is public over HTTPS.  
   - If webhook not set automatically, run this in browser:  
     ```
     https://api.telegram.org/bot<YOUR_BOT_TOKEN>/setWebhook?url=<YOUR_N8N_WEBHOOK_URL>
     ```
     Replace `<YOUR_BOT_TOKEN>` and `<YOUR_N8N_WEBHOOK_URL>` with your details.  

6. **Test Your Bot**
   - Send a message to your bot in Telegram.  
   - Confirm n8n receives it via the Trigger node.  
   - Check the Send Message node sends back a reply.  

7. **Go Live & Secure**
   - Keep your Bot Token secret (never share in public repos).  
   - Use environment variables for storing sensitive data in n8n.  
   - Monitor logs for errors or failed deliveries.  

---

## Troubleshooting

- **Webhook not working?** Make sure your n8n webhook URL is accessible over HTTPS.  
- **Bot not replying in group?** Disable privacy mode in BotFather.  
- **Multiple workflows?** Only one webhook per bot is supported; the last activated trigger takes priority.  

---

## Summary

1. Create bot with BotFather (`/newbot`)  
2. Copy Bot Token & Chat ID  
3. Configure Telegram credentials in n8n  
4. Build workflow with Trigger + Send Message  
5. Test & secure  

---

## References

- [Telegram Bot API Docs](https://core.telegram.org/bots/api)  
- [n8n Telegram Integration Docs](https://docs.n8n.io/integrations/builtin/credentials/telegram/)  
- [BotFather in Telegram](https://t.me/botfather)  
