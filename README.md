# 🤖 n8n Workflow: AI Telegram Support Bot

## Description

This workflow connects a **Telegram Bot** with **OpenAI (or Gemini)** through n8n to act as a **sales support assistant** for an online store.  
It processes customer messages using a custom **guideline** and responds in a friendly, brand-specific tone.  
It can also fetch product prices and links from **Google Sheets** and send them back to the user via Telegram.

---

## 🚀 Workflow Overview

![Workflow Diagram](images/workflow-diagram.png)

### Workflow Steps

1. **Trigger – Telegram “On New Message”**
   - Starts when a customer sends a message to the Telegram bot.
   - The bot token is obtained from **BotFather** on Telegram.

2. **AI Agent – Process Customer Message**
   - Uses **OpenAI Chat Model (GPT-4 mini)** or **Gemini** to interpret messages.
   - Input:
     - **Source for Prompt:** User’s Telegram message  
     - **System Message (Guideline):** A custom set of rules defining:
       - Tone of conversation  
       - How to greet users (only once)  
       - How to handle angry or impatient customers  
       - When to provide product info or say a product is unavailable  

3. **Google Sheets – Product Data**
   - Connected to store inventory data via Google Cloud credentials.
   - Used by the AI to provide accurate prices and purchase links.

4. **Send Message – Telegram**
   - Sends the AI-generated response back to the user.

---

## 🧠 Example Guideline (System Message)

```text
You are a polite and helpful sales assistant for Zahra’s online store.
- Greet the user only in the first message.
- Use a friendly and professional tone.
- If the user is upset, respond calmly and kindly.
- If asked about prices, check Google Sheets data and provide price + purchase link.
- If the product does not exist, apologize and inform them it’s unavailable.
