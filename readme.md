<div align="center">

# 🤖 AI Automation Engineering with n8n

### A curated collection of hands-on automation projects using n8n, Google Workspace, and AI

![n8n](https://img.shields.io/badge/n8n-Workflow%20Automation-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-34A853?style=for-the-badge&logo=google-sheets&logoColor=white)
![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)
![Google Docs](https://img.shields.io/badge/Google%20Docs-4285F4?style=for-the-badge&logo=google-docs&logoColor=white)
![AI](https://img.shields.io/badge/AI%20Powered-LLM%20Chain-7C3AED?style=for-the-badge&logo=openai&logoColor=white)

---

**10 Projects &nbsp;|&nbsp; Beginner to Production-Level &nbsp;|&nbsp; Real-World Workflows**

</div>

---

## 📖 About This Repository

This repository contains **10 structured n8n automation projects** designed for students learning workflow automation. Each project is self-contained with clear requirements, expected outputs, evaluation criteria, and a recommended timeline.

Projects are organized into three tiers that progressively build real-world skills — from simple form automations all the way to multi-workflow, AI-driven production systems.

---

## 🗂️ Project Overview

| # | Project | Key Integrations | Difficulty | Duration |
|---|---------|-----------------|------------|----------|
| 1 | [Newsletter Subscription Automation](#-project-1-newsletter-subscription-automation) | Form · Google Contacts · Gmail · Sheets | ⭐ Beginner | 2 hrs |
| 2 | [Customer Feedback Collection](#-project-2-customer-feedback-collection) | Form · Gmail · Sheets | ⭐ Beginner | 2 hrs |
| 3 | [Interview Registration & Notifications](#-project-3-interview-registration--notifications) | Form · Gmail ×2 · Sheets | ⭐⭐ Intermediate | 2.5 hrs |
| 4 | [Client Inquiry Management](#-project-4-client-inquiry-management) | Form · Sheets · Gmail ×2 · Contacts | ⭐⭐ Intermediate | 3 hrs |
| 5 | [AI Email Classification](#-project-5-ai-powered-email-classification) | Gmail Trigger · LLM Chain · Sheets · Gmail | ⭐⭐ Intermediate | 3 hrs |
| 6 | [Meeting Transcript to Notes](#-project-6-meeting-transcript-to-structured-notes) | Form/Webhook · LLM Chain · Docs · Gmail | ⭐⭐ Intermediate | 3 hrs |
| 7 | [Daily AI News Digest](#-project-7-automated-daily-ai-news-digest) | Schedule · LLM Chain · Docs · Gmail | ⭐⭐ Intermediate | 3.5 hrs |
| 8 | [AI Lead Qualification & CRM Pipeline](#-project-8-ai-powered-lead-qualification--crm-pipeline) | Multi-entry · LLM Chain · IF Nodes · Calendar · Sheets | ⭐⭐⭐ Advanced | 4 hrs |
| 9 | [Invoice Processing & Approval Workflow](#-project-9-automated-invoice-processing--expense-approval-workflow) | Gmail Trigger · LLM Chain · Webhook · Sheets · Docs | ⭐⭐⭐ Advanced | 4 hrs |
| 10 | [Support Ticketing with SLA & Escalation](#-project-10-multi-channel-support-ticketing-system-with-sla--escalation) | 4 Coordinated Workflows · LLM · SLA Logic · Sheets | ⭐⭐⭐⭐ Production | 5 hrs |

---

## 🏆 Difficulty Tiers

```
⭐  BEGINNER        Projects 1–2    Core nodes, form triggers, basic integrations
⭐⭐  INTERMEDIATE   Projects 3–7    Multi-node flows, AI integration, Google services
⭐⭐⭐  ADVANCED      Projects 8–9    Branching, AI scoring, approval patterns, multi-workflow
⭐⭐⭐⭐  PRODUCTION   Project 10      Multi-workflow systems, SLA logic, stateful automation
```

---

## ⏱️ Total Timeline

```
Week 1                                        Week 2                          Week 3
──────────────────────────────────────────    ─────────────────────────────   ──────────────────
Day 1    Day 2    Day 3    Day 4    Day 5      Day 6    Day 7    Day 8         Day 9–10
Proj 1   Proj 2   Proj 3   Proj 4   Proj 5    Proj 6   Proj 7   Proj 8        Proj 9 & 10
2 hrs    2 hrs    2.5 hrs  3 hrs    3 hrs      3 hrs    3.5 hrs  4 hrs         4 hrs + 5 hrs
```

**Total Estimated Time: ~32 Hours across 10 Projects**

---

## 📁 Repository Structure

```
ai-automation-engineering-n8n-projects/
│
├── 📂 Project-1-Newsletter-Subscription/
│   └── README.md
├── 📂 Project-2-Customer-Feedback/
│   └── README.md
├── 📂 Project-3-Interview-Registration/
│   └── README.md
├── 📂 Project-4-Client-Inquiry/
│   └── README.md
├── 📂 Project-5-AI-Email-Classification/
│   └── README.md
├── 📂 Project-6-Meeting-Transcript/
│   └── README.md
├── 📂 Project-7-Daily-News-Digest/
│   └── README.md
├── 📂 Project-8-Lead-Qualification-CRM/
│   └── README.md
├── 📂 Project-9-Invoice-Processing/
│   └── README.md
└── 📂 Project-10-Support-Ticketing/
    └── README.md
```

---

## 🚀 Projects

---

### 📬 Project 1: Newsletter Subscription Automation

> **Difficulty:** ⭐ Beginner &nbsp;|&nbsp; **Duration:** 2 Hours

Build a workflow that handles newsletter sign-ups end-to-end — from collecting subscriber details to welcoming them via email and storing their data.

**Workflow:**
```
Form Trigger → Create Contact → Send Welcome Email → Store in Google Sheets
```

**What you'll build:**
- A form collecting Name, Email, and Interested Topic
- Auto-creation of Google Contacts for every new subscriber
- A personalized welcome email via Gmail
- Subscriber records stored in Google Sheets

📄 [View Full Project Requirements](./Project-1-Newsletter-Subscription/README.md)

---

### 📝 Project 2: Customer Feedback Collection

> **Difficulty:** ⭐ Beginner &nbsp;|&nbsp; **Duration:** 2 Hours

Build a workflow that collects customer feedback, saves it to a spreadsheet, and automatically sends a thank you email.

**Workflow:**
```
Form Trigger → Store Feedback in Google Sheets → Send Thank You Email
```

**What you'll build:**
- A feedback form collecting Name, Email, Feedback, and Rating (1–5)
- Automatic storage of all responses in Google Sheets
- A personalized thank you email acknowledging the customer's rating

📄 [View Full Project Requirements](./Project-2-Customer-Feedback/README.md)

---

### 🗓️ Project 3: Interview Registration & Notifications

> **Difficulty:** ⭐⭐ Intermediate &nbsp;|&nbsp; **Duration:** 2 Hours 30 Minutes

Build a workflow that handles interview registrations — sending confirmation emails to candidates, notifying HR, and logging all data in Google Sheets.

**Workflow:**
```
Form Trigger → Email to Candidate → Email to HR → Store in Google Sheets
```

**What you'll build:**
- An interview registration form collecting Candidate Name, Email, Role, and Interview Date
- Automatic confirmation email to the candidate with role and date details
- Internal notification email sent to the HR team
- Candidate records stored in Google Sheets

📄 [View Full Project Requirements](./Project-3-Interview-Registration/README.md)

---

### 🏢 Project 4: Client Inquiry Management

> **Difficulty:** ⭐⭐ Intermediate &nbsp;|&nbsp; **Duration:** 3 Hours

Build a complete client intake workflow that stores inquiries, confirms receipt with the client, saves them as a contact, and notifies you internally.

**Workflow:**
```
Form Trigger → Store in Sheets → Thank You Email → Add to Contacts → Notify Yourself
```

**What you'll build:**
- An inquiry form collecting Name, Email, Phone Number, and Description
- Google Sheets entry for every new inquiry
- A personalized thank you email to the client
- Auto-creation of a Google Contact
- An internal notification email sent to yourself

📄 [View Full Project Requirements](./Project-4-Client-Inquiry/README.md)

---

### 🧠 Project 5: AI-Powered Email Classification

> **Difficulty:** ⭐⭐ Intermediate &nbsp;|&nbsp; **Duration:** 3 Hours

Build an AI-driven support workflow that reads incoming emails, classifies them by category and priority using a language model, stores the results, and sends an acknowledgement.

**Workflow:**
```
Gmail Trigger → Read Email → LLM Chain (AI) → Store in Sheets → Send Acknowledgement
```

**What you'll build:**
- A Gmail Trigger that fires on every new support email
- AI-powered classification of Issue Category, Priority Level, and Summary
- Structured storage of all classified emails in Google Sheets
- Automated acknowledgement email to the customer

📄 [View Full Project Requirements](./Project-5-AI-Email-Classification/README.md)

---

### 📋 Project 6: Meeting Transcript to Structured Notes

> **Difficulty:** ⭐⭐ Intermediate &nbsp;|&nbsp; **Duration:** 3 Hours

Build an AI workflow that transforms raw meeting transcripts into structured notes with summaries, action items, and next steps — saved to Google Docs and emailed to participants.

**Workflow:**
```
Form / Webhook → LLM Chain (AI) → Save to Google Docs → Email Summary to Participants
```

**What you'll build:**
- A form or webhook that accepts meeting transcripts
- AI-generated summary, key discussion points, action items, and next steps
- A well-structured Google Doc automatically created with all sections
- A summary email sent to all meeting participants

📄 [View Full Project Requirements](./Project-6-Meeting-Transcript/README.md)

---

### 📰 Project 7: Automated Daily AI News Digest

> **Difficulty:** ⭐⭐ Intermediate &nbsp;|&nbsp; **Duration:** 3 Hours 30 Minutes

Build a fully automated scheduled workflow that collects AI news every morning, generates a digest using a language model, saves it to Google Docs, and emails it to subscribers.

**Workflow:**
```
Schedule Trigger → Collect News → LLM Chain (AI) → Save to Google Docs → Send Digest Email
```

**What you'll build:**
- A Schedule Trigger that runs automatically every morning
- News content collection via RSS feed or HTTP request
- AI-generated summaries, trending topics, and key takeaways
- A daily Google Doc digest with all required sections
- A formatted digest email sent to subscribers

📄 [View Full Project Requirements](./Project-7-Daily-News-Digest/README.md)

---

### 🎯 Project 8: AI-Powered Lead Qualification & CRM Pipeline

> **Difficulty:** ⭐⭐⭐ Advanced &nbsp;|&nbsp; **Duration:** 4 Hours

Build a production-grade lead management system that accepts leads from multiple sources, scores them using AI, conditionally routes them into different follow-up tracks, maintains a CRM dashboard, and auto-generates weekly pipeline reports.

**Workflow:**
```
Form / Webhook → Normalize Data → AI Lead Scoring → IF Branch (High / Medium / Low)
      High: Outreach Email + Calendar Invite + Internal Alert
    Medium: Nurture Email + Follow-Up Sheet Entry
       Low: Polite Email + CRM Log
All Leads → CRM Dashboard (Google Sheets)
Schedule Trigger → Read CRM → AI Summary → Weekly Pipeline Report Email
```

**What you'll build:**
- Dual entry points (form + webhook) feeding into a single pipeline
- Data normalization using a Set or Code node
- AI lead scoring with structured JSON output (score, tier, reason, recommended action)
- Conditional branching into three tracks based on AI tier
- Google Calendar event creation for High-tier leads
- A live CRM dashboard in Google Sheets with 14 tracked fields
- A second workflow that runs every Monday and delivers an AI-written pipeline report

**New concepts introduced:**
- Structured AI output parsing
- IF node branching with multiple paths
- Google Calendar integration
- Multi-entry-point workflow design
- Scheduled reporting on aggregated data

📄 [View Full Project Requirements](./Project-8-Lead-Qualification-CRM/README.md)

---

### 🧾 Project 9: Automated Invoice Processing & Expense Approval Workflow

> **Difficulty:** ⭐⭐⭐ Advanced &nbsp;|&nbsp; **Duration:** 4 Hours

Build a production-grade finance automation system that reads incoming invoice emails, extracts structured data using AI, routes invoices through a threshold-based approval process with Webhook-driven resume logic, maintains a live expense ledger, and generates a monthly expense report.

**Workflow:**
```
Gmail Trigger → AI Data Extraction → Generate Invoice ID → Log to Sheets
      → Send Vendor Acknowledgement
      → IF Amount < $500:   Auto-Approve
      → IF $500–$2,000:     Manager Approval Email → Webhook → Resume
      → IF > $2,000:        Senior Approval Email + AI Risk Note → Webhook → Resume
      → On Approve: Update Sheet + Email Vendor
      → On Reject:  Update Sheet + Email Vendor
Schedule Trigger → Read Ledger → AI Report → Google Docs → Monthly Report Email
```

**What you'll build:**
- A Gmail Trigger that fires on incoming invoice emails
- AI extraction of 9 structured invoice fields (vendor, amount, date, category, etc.)
- Auto-generated Invoice IDs and initial ledger entries
- Three-tier approval routing based on invoice amount thresholds
- Webhook-based approval/rejection with workflow resume (Wait node pattern)
- AI-generated risk assessment for high-value invoices
- A monthly expense report workflow generating a Google Doc and email summary

**New concepts introduced:**
- AI-driven structured data extraction from unstructured text
- Stateful, approval-gated workflows using the Wait node
- Webhook-resume pattern (pause → external action → continue)
- Row updates in Google Sheets based on external decisions
- Threshold-based financial routing logic

📄 [View Full Project Requirements](./Project-9-Invoice-Processing/README.md)

---

### 🎫 Project 10: Multi-Channel Support Ticketing System with SLA & Escalation

> **Difficulty:** ⭐⭐⭐⭐ Production &nbsp;|&nbsp; **Duration:** 5 Hours

Build a complete, autonomous support operations system consisting of four coordinated workflows sharing a single Google Sheets database. The system handles tickets from email and webhook, triages them using AI, enforces SLA deadlines, auto-escalates overdue tickets, delivers daily summaries, and processes ticket resolutions — all running without any human intervention.

**System Architecture:**
```
WORKFLOW 1 — TICKET INTAKE (Gmail Trigger + Webhook)
  Normalize → AI Triage → Ticket ID + SLA Deadline → Log → Acknowledge Customer → Route to Team

WORKFLOW 2 — SLA MONITOR (Every Hour, Schedule Trigger)
  Read Open Tickets → Check Deadlines → Escalate Overdue → Alert Manager → Nudge Team

WORKFLOW 3 — DAILY DIGEST (8AM Daily, Schedule Trigger)
  Read All Tickets → AI Ops Summary → Send Digest Email

WORKFLOW 4 — TICKET RESOLUTION (Webhook)
  Receive Resolution → Update Sheet → Send Resolution Email to Customer

All Workflows ↔ Support Ticket Database (Google Sheets)
```

**What you'll build:**
- Four coordinated workflows sharing a single 17-column Google Sheets database
- Dual intake channels (Gmail + Webhook) feeding one triage pipeline
- AI classification of department and urgency with SLA auto-calculation
- Unique Ticket ID generation per submission
- Customer acknowledgement emails with SLA commitment
- Department-based team routing with urgency-flagged subject lines
- Hourly SLA monitoring with breach detection using timestamp comparison
- Escalation email chain to managers and teams on SLA breach
- Critical alert after 3+ escalations on the same ticket
- Daily AI-generated ops digest summarizing ticket state across the system
- Webhook-based ticket resolution with customer confirmation email

**New concepts introduced:**
- Multi-workflow system design with shared state
- Timestamp-based SLA deadline logic
- Iterative monitoring with conditional escalation
- Escalation count tracking and threshold-based critical alerts
- Four-trigger coordination (2× Schedule, 1× Gmail, 1× Webhook)
- System-level thinking: how workflows interact, not just how nodes connect

📄 [View Full Project Requirements](./Project-10-Support-Ticketing/README.md)

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| **n8n** | Workflow automation platform |
| **Gmail / Gmail Trigger** | Sending emails and reacting to incoming messages |
| **Google Sheets** | Storing structured data, CRM dashboards, ledgers |
| **Google Docs** | Saving AI-generated long-form documents |
| **Google Contacts** | Managing contact records |
| **Google Calendar** | Creating events automatically |
| **Basic LLM Chain** | AI-powered analysis, classification, and generation |
| **Form Trigger** | Accepting user input to start workflows |
| **Webhook** | Receiving external data or resuming paused workflows |
| **Schedule Trigger** | Running workflows automatically on a time-based schedule |
| **IF Node** | Conditional branching based on data values |
| **Set / Code Node** | Transforming and normalizing data between nodes |
| **Wait Node** | Pausing a workflow until an external event occurs |

---

## 📋 Submission Checklist

For every project, students must submit:

- [ ] Exported n8n workflow `.json` file(s)
- [ ] Screenshot of the completed workflow canvas
- [ ] Screenshot(s) of Google Sheet / Doc outputs
- [ ] Screenshot(s) of emails sent and received
- [ ] A written document explaining the workflow design, node purposes, and challenges

---

## 📊 Evaluation Summary

| # | Project | Marks |
|---|---------|-------|
| 1 | Newsletter Subscription Automation | 100 |
| 2 | Customer Feedback Collection | 100 |
| 3 | Interview Registration & Notifications | 100 |
| 4 | Client Inquiry Management | 100 |
| 5 | AI-Powered Email Classification | 100 |
| 6 | Meeting Transcript to Notes | 100 |
| 7 | Daily AI News Digest | 100 |
| 8 | AI Lead Qualification & CRM Pipeline | 100 |
| 9 | Invoice Processing & Approval Workflow | 100 |
| 10 | Support Ticketing with SLA & Escalation | 100 |
| | **Grand Total** | **1000 Marks** |

---

## ⚠️ Important Note

> Students are expected to design and implement each workflow **independently**. Project READMEs provide only the requirements — the workflow logic, node configuration, data mapping, branching conditions, and AI prompt design must all be developed by the student. For the advanced projects (8–10), there is no single correct implementation. Students are evaluated on whether the system works correctly as a whole.

---

<div align="center">

**Built for learning. Designed for real-world impact.**

</div>
