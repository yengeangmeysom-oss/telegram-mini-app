# Telegram Mini App - Setup and Testing Guide

This repository contains a simple Telegram Mini App (`index.html`) for testing purposes.  
This guide will help you deploy, connect, and test your Mini App with Telegram.

---

## Step 1: Prepare Your Mini App Code

- Create or use the provided `index.html` file.
- This file is a static web page with a simple UI for Telegram Mini App testing.

---

## Step 2: Create a GitHub Account (If Needed)

- Sign up for a free account at [GitHub](https://github.com/join).

---

## Step 3: Create a New GitHub Repository

1. Log into GitHub.
2. Click the **+** icon in the top-right corner → **New repository**.
3. Name your repository (e.g., `telegram-mini-app`).
4. Set the repository visibility to **Public**.
5. Click **Create repository**.

---

## Step 4: Upload Mini App Code to Your Repository

1. Navigate to your repository page.
2. Click **Add file** → **Upload files**.
3. Upload the `index.html` file.
4. Commit the changes.

---

## Step 5: Enable GitHub Pages Hosting

1. Go to the **Settings** tab of your repository.
2. Scroll down to the **Pages** section.
3. Under **Source**, select branch: `main` (or `master`).
4. Select folder: `/ (root)`.
5. Click **Save**.
6. Wait a few moments for GitHub to provide a live URL (e.g., `https://your-username.github.io/telegram-mini-app/`).

---

## Step 6: Create a Telegram Bot

1. Open Telegram app.
2. Search for **@BotFather**.
3. Send `/newbot` and follow the prompts to create a bot.
4. Save your **bot token** provided by BotFather.

---

## Step 7: Find Your Telegram Chat ID

1. Start a chat with your bot.
2. Send any message.
3. Visit this URL (replace `<YOUR_BOT_TOKEN>`): https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getUpdates
4. Look for `"chat":{"id":123456789}` in the JSON response. This is your chat ID.

---

## Step 8: Send a Message with Mini App Button Using Telegram Bot API

Use `curl` or any HTTP client to send a message that includes an inline button opening your Mini App.

curl -X POST "https://api.telegram.org/bot<YOUR_BOT_TOKEN>/sendMessage" \
-H "Content-Type: application/json" \
-d '{
"chat_id": "<YOUR_CHAT_ID>",
"text": "Open Telegram Mini App",
"reply_markup": {
 "inline_keyboard": [[
   {
     "text": "Open Mini App",
     "web_app": {
       "url": "https://<your-github-username>.github.io/<repo-name>/index.html"
     }
   }
 ]]
}
}'

---

## Step 9: Test Your Mini App Inside Telegram

1. Open your Telegram chat with the bot.
2. Tap the Open Mini App button.
3. Your Mini App will open within Telegram.
4. Use the app UI for testing.

---

## Step 10: Handle Mini App Data in Your Bot

1. When using Telegram Web Apps API to send data (tg.sendData()), your bot will receive callback_query updates.
2. Implement bot logic to handle these updates as needed.

