# How to Configure WhatsApp Business Cloud API on n8n

This guide explains how to integrate WhatsApp Business Cloud API with n8n. Replace the **example placeholders** with your own details.

---

## Prerequisites

- Meta / Facebook account  
- Meta Business Manager account  
- WhatsApp Business profile with a phone number  
- n8n instance (cloud or self-hosted)  
- Admin access to Meta Developer settings  

---

## Example WhatsApp API Details (Replace with Yours)

| Field                   | Example Value        |
|--------------------------|----------------------|
| App ID (Client ID)       | `123456789012345`    |
| App Secret (Client Sec.) | `a1b2c3d4e5f6g7h8i9` |
| Access Token             | `EAAGm0PX4ZCpsBA...` |
| Business Account ID      | `9876543210`         |
| Phone Number ID          | `111222333444`       |

---

## Configuration Steps

1. **Create & Configure a Meta App**
   - Visit [Meta for Developers](https://developers.facebook.com/apps/).  
   - Click **Create App** → choose *Business*.  
   - Add **WhatsApp** product to your app.  
   - Fill in required details (App name, email, etc.).  

2. **Get WhatsApp Credentials**
   - In the app dashboard, go to **WhatsApp → API Setup**.  
   - Copy:  
     - **App ID** (use as Client ID)  
     - **App Secret** (use as Client Secret)  
     - **Business Account ID**  
     - **Access Token** (temporary or long-lived)  
     - **Phone Number ID** (from the test or business number setup)  

3. **Create WhatsApp Credentials in n8n**
   - Open **n8n → Credentials**.  
   - Create credential type **WhatsApp API** → enter:  
     - *Access Token*  
     - *Business Account ID*  
   - Create credential type **WhatsApp OAuth2** (for triggers) → enter:  
     - *Client ID* (App ID)  
     - *Client Secret* (App Secret)  

4. **Set Up a Workflow**
   - Add a **WhatsApp Trigger** node → operation: *On New Message*.  
   - Link it with your OAuth credential.  
   - Add a **WhatsApp Send Message** node →  
     - Credential: WhatsApp API  
     - Phone Number ID: your value  
     - Recipient: target phone number  
     - Message: text template  

5. **Configure Webhooks**
   - In Meta Developer settings → **Webhooks** → Add callback URL.  
   - Use the webhook URL from your n8n workflow trigger.  
   - Subscribe to events like `messages` or `message_received`.  

6. **Test the Flow**
   - Send a test message from your WhatsApp to the business number.  
   - Confirm the workflow captures it and responds.  

7. **Go Live**
   - Move your Meta app from *Development* to *Live*.  
   - Use a long-lived access token.  
   - Secure all tokens via environment variables in n8n.  

---

## Troubleshooting

- **Message not received?** → Check webhook subscription in Meta dashboard.  
- **Token expired?** → Generate a new long-lived access token.  
- **Webhook not triggered?** → Ensure your n8n instance is publicly accessible over HTTPS.  

---

## Summary

1. Create Meta App + add WhatsApp product  
2. Collect App ID, Secret, Business Account ID, Access Token, Phone Number ID  
3. Configure credentials in n8n  
4. Build workflow with Trigger + Send Message  
5. Add webhook in Meta → link with n8n  
6. Test → Go live → Secure credentials  

---

## References

- [WhatsApp Cloud API Documentation](https://developers.facebook.com/docs/whatsapp)  
- [n8n WhatsApp Integration Docs](https://docs.n8n.io/integrations/builtin/credentials/whatsapp/)  
- [Meta for Developers Dashboard](https://developers.facebook.com/apps/)  
