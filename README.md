# n8n Automation Workflows 🚀

![n8n Version](https://img.shields.io/badge/n8n-v1.x-ff6d5a?logo=n8n)
![License](https://img.shields.io/badge/license-MIT-blue)
![Status](https://img.shields.io/badge/workflows-6%2F20-green)

A curated collection of practical, production-ready **n8n workflows** for business automation, marketing, and personal productivity.

Unlike standard templates, every workflow in this repository includes a **Built-in Test Mode (Mock Data)**. This allows you to verify the logic and behavior instantly without needing to wait for real-world triggers or set up complex external data sources immediately.

## 📂 Workflow Collection

| Workflow Name | Description | Tech Stack (Nodes) |
| :--- | :--- | :--- |
| [**01. AI Book Advisor**](./01-ai-book-advisor) | **Monetization Ready.** An AI agent that researches books, summarizes reviews, and sends HTML emails with affiliate links. | OpenAI, Google Books, Custom Search, Gmail |
| [**02. Urgent Alert Filter**](./02-urgent-alert-filter) | **Noise Reduction.** Monitors Slack & Gmail, uses AI to filter out non-urgent messages, and alerts Telegram only for emergencies. | Gemini, Slack, Gmail, Telegram |
| [**03. Smart Expense Manager**](./03-smart-expense-manager) | **Back-office Auto.** Scans receipts from Google Drive, extracts data via AI, and auto-approves expenses under a set limit. | Gemini, Google Drive, Sheets, Slack |
| [**04. Marketing Anomaly Detector**](./04-marketing-anomaly-detector) | **KPI Watchdog.** Cross-references GA4 traffic with Shopify sales to detect "High Traffic / Low CVR" anomalies. | GA4, Shopify, Slack |
| [**05. Global Cart Recovery**](./05-global-cart-recovery) | **Multi-language CRO.** Detects abandoned carts, identifies the user's country, and sends AI-localized recovery emails. | Shopify, Gemini, GA4, Gmail |
| [**06. Elderly Care Monitor**](./06-elderly-care-monitor) | **Health & Safety.** Monitors LINE activity and sentiment to detect distress signals from elderly family members. | LINE, Gemini, Google Sheets |
| [**07. AI Nightly Butler**](./07-ai-nightly-butler) | **Voice Journal.** Sorts voice notes into Diary, Tasks, and Health logs using AI, then sends a nightly summary. | Webhook, Gemini, Sheets, Gmail |
| [**08. Lazy Chef**](./08-ai-recipe-generator) | **AI Recipe Gen.** Generates 3 recipe variations (Speed/Healthy/Creative) from leftovers and emails a visual menu. | Form, Gemini, Google Search, Sheets |
| [**09. Smart Morning Guard**](./09-smart-morning-guard) | **AI Morning Alarm.** Checks weather & train delays at 5 AM. Wakes you up early only if Gemini detects an emergency. | OpenWeather, RSS, Gemini, Gmail |
| [**10. Smart Developer Journal**](./10-smart-developer-journal) | **Auto Daily Report.** Aggregates GitHub commits & Slack messages, then AI writes your "Done/Doing/Blockers" report. | GitHub, Slack, Gemini |
| [**11. AI Invoice Clerk**](./11-ai-invoice-clerk) | **Accounting Auto.** Monitors Gmail for invoices, uses Gemini Vision to extract data (Amount/Vendor), and logs to Sheets. | Gmail, Gemini Vision, Sheets, Slack |
| [**12. Smart Tax Accountant**](./12-smart-tax-accountant) | **Tax Return Helper.** Upload receipt images via Form. AI extracts data and auto-categorizes expenses (Japanese Tax Titles). | Form, Gemini Vision, Sheets |
| [**13. Smart Lead Scraper**](./13-smart-lead-scraper) | **Sales Automation.** Input a keyword (e.g. "AI Startups"), scrapes Google Search, and AI builds a company list in Sheets. | Google Search, Gemini, Sheets, Form |

*(More workflows are currently under development. Target: 20+)*

## ✨ Key Features across all workflows

- **🧪 Built-in Test Mode:**
  Each workflow comes with a "Manual Trigger" and "Mock Data" nodes. You can run and visualize the full logic flow immediately after importing.
- **🧠 AI-Powered:**
  Utilizes LLMs (Gemini / OpenAI) not just for text generation, but for logical decision-making (e.g., urgency filtering, sentiment analysis).
- **🎨 Standardized Layout:**
  Cleanly organized with sticky notes (Yellow for context, Grey for grouping) following n8n best practices.

## 🚀 How to Use

1. **Clone or Download:**
   Clone this repository or download the specific `workflow.json` file you need.
2. **Import to n8n:**
   - Go to your n8n dashboard.
   - Click **"Add workflow"** > **"Import from..."** > **"Local File"**.
3. **Setup Credentials:**
   - Check the `README.md` inside each folder for required credentials.
   - Configure the nodes (look for the red `!` icons).
4. **Run Test:**
   - Toggle the **Test Mode** switch (if available in the Config node) or simply click **"Execute Workflow"** to run with mock data.

## 👤 Author

**Alternatives.com**
https://alternativecomputers.org/
- Focusing on AI automation and practical business workflows.
- Open for collaboration and feedback.

---
*Disclaimer: These workflows are provided as-is. Please review and test them in your environment before deploying to production.*
