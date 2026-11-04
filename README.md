# psorbit-microservices
Production-grade event-driven lead triage, missed-call recovery, and follow-up sequence engines built in n8n.

# Real Estate Speed-to-Lead & Inbound Recovery Engine

Production-grade, event-driven intake and recovery pipelines built in **n8n** for real estate teams and high-ticket service businesses. 

Designed to replace bloated CRM add-ons with deterministic, sub-60-second speed-to-lead response workflows.

---

## ⚡ Core Systems Included

### 1. Inbound Lead Triage Engine (`01_inbound_lead_triage.json`)
* **Trigger:** Webhook listener capturing raw portal/ad payloads (Meta Ads, Zillow, Web forms).
* **Processing:** Contact data normalization to E.164 standard; rule-based budget & timeline intent scoring (1–10).
* **Dispatch:** Pushes a high-priority mobile card to Slack/Discord with a 1-tap call button within 5 seconds.
* **Storage:** Commits structured lead record to a centralized database/ledger.

### 2. 5-Stage Follow-Up Cadence Dispatcher (`02_followup_cadence_dispatcher.json`)
* **Trigger:** Scheduled cron running daily at 9:00 AM.
* **Logic:** Evaluates active leads across a 21-day timeline (Days 1, 3, 7, 14, 21).
* **Execution:** Dynamically dispatches SMS/email outreach copy and updates the next touchpoint.
* **Safety:** Automatic halt condition the moment a prospect responds.

### 3. Missed-Call Instant Recovery (`03_missed_call_recovery.json`)
* **Trigger:** Telephony webhook intercepting unanswered/busy inbound calls.
* **Response:** Fires an immediate, natural SMS text-back within 15 seconds to engage the caller before they dial a competitor.
* **Queue:** Enters caller into high-priority callback ledger.

---

## 🛠️ Tech Stack & Prerequisites
* **Orchestration:** n8n (v1.x+)
* **Data Standards:** E.164 phone formatting, JSON schema validation
* **Integrations:** Twilio / Webhook telephony, Slack / Discord Webhooks, Supabase / PostgreSQL / Google Sheets

---

## 🚀 How to Import into n8n

1. Clone or download this repository.
2. Open your n8n workspace.
3. Click **Workflows** $\rightarrow$ **Add Workflow**.
4. In the canvas menu (`...`), select **Import from File**.
5. Select any of the JSON files from the `/workflows` directory.
6. Replace the environment variables/credential nodes with your own API credentials (e.g., Twilio Account SID, Slack Webhook URL).
7. Activate the workflow.

---

## 📄 License
MIT License. Engineered and maintained by [PS Orbit Studio](https://psorbit.com).
