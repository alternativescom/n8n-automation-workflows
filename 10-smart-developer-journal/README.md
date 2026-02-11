# Smart Developer Journal: GitHub & Slack to Daily Report 👨‍💻

![Screenshot](screenshot.jpg)

## Overview
**Automate your daily engineering stand-up report.**
Writing daily reports is a hassle. This workflow connects to your **GitHub** repositories and **Slack** channels to gather your day's activity. **Gemini (AI)** then summarizes your commits and discussions into a clean, formatted report (Done / Doing / Blockers) and sends it to you via Slack or Notion.

## Key Features
- **📊 Activity Aggregation:** Automatically pulls "What I coded" (GitHub Commits) and "What I discussed" (Slack Messages).
- **🧠 AI Summarization:** Gemini acts as a Tech Lead, turning technical logs into a human-readable progress report.
- **🧪 Built-in Test Mode:** Simulates a day where you "Fixed a login bug" and "Discussed UI design," allowing you to test the output formatting instantly.

## How It Works
1. **Trigger:** Runs daily at 18:00 (end of workday).
2. **Fetch:** Retrieves commits from the specified repo and messages from your team channel.
3. **Draft:** AI digests the raw text and categorizes it into "Done", "Doing", and "Blockers".
4. **Deliver:** Posts the draft report to your private Slack channel for final review.

## Setup Steps
1. **Import:** Import `workflow.json` into n8n.
2. **Credentials:** Set up GitHub, Slack, and Gemini.
3. **Config:**
   - Open **"Config"** to set `GITHUB_OWNER`, `GITHUB_REPO`, and `SLACK_CHANNEL`.
   - Set `TEST_MODE` to `true` to generate a mock report.

## Requirements
- n8n v1.x or later
- GitHub Account & Personal Access Token
- Slack Workspace & Bot Token
- Google Gemini API Key
