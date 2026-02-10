# Filter urgent Slack & Gmail alerts to Telegram using Gemini 🚨

![Screenshot](screenshot.jpg)

## Overview
**Never miss critical messages again.**
This workflow monitors **Slack** channels and **Gmail** inbox for new messages, uses **Gemini (AI)** to analyze their urgency based on context (e.g., "Server Down", "VIP Client"), and forwards ONLY the urgent ones to **Telegram**.

## Key Features
- **🧠 AI Sentiment Analysis:** Filters noise by understanding context, not just keywords.
- **⚡ Unified Inputs:** Handles messages from both Slack and Gmail in a single stream.
- **🧪 Built-in Test Mode:** Includes a Manual Trigger with mock data to verify logic instantly.

## How It Works
1. **Listen:** Monitors Slack and Gmail for new unread messages.
2. **Normalize:** Unifies data structure from different sources.
3. **Analyze:** Gemini evaluates the message and assigns a boolean `is_urgent` flag.
4. **Filter & Notify:** If `is_urgent` is true, sends an alert to your Telegram.

## Setup Steps
1. **Import:** Import `workflow.json` into n8n.
2. **Credentials:** Set up credentials for Slack, Gmail, Telegram, and Google Gemini.
3. **Config:**
   - Open the **"Configuration"** node.
   - Set your `TELEGRAM_CHAT_ID`.
   - Set `TEST_MODE` to `true` for initial verification.

## Requirements
- n8n v1.x or later
- Google Gemini API Key
- Telegram Bot Token
