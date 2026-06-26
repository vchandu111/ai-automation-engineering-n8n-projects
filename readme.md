<div align="center">

# 🤖 AI Automation Engineering with n8n

### A curated collection of hands-on automation projects using n8n, Google Workspace, and AI

![n8n](https://img.shields.io/badge/n8n-Workflow%20Automation-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-34A853?style=for-the-badge&logo=google-sheets&logoColor=white)
![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)
![Google Docs](https://img.shields.io/badge/Google%20Docs-4285F4?style=for-the-badge&logo=google-docs&logoColor=white)
![AI](https://img.shields.io/badge/AI%20Powered-LLM%20Chain-7C3AED?style=for-the-badge&logo=openai&logoColor=white)

---

**7 Projects &nbsp;|&nbsp; Beginner to Advanced &nbsp;|&nbsp; Real-World Workflows**

</div>

---

## 📖 About This Repository

This repository contains **7 structured n8n automation projects** designed for students learning workflow automation. Each project is self-contained with clear requirements, expected outputs, evaluation criteria, and a recommended timeline.

Projects progress from simple form-based automations to AI-powered workflows — giving students a complete journey through modern no-code automation.

---

## 🗂️ Project Overview

| # | Project | Key Integrations | Difficulty | Duration |
|---|---------|-----------------|------------|----------|
| 1 | [Newsletter Subscription Automation](#-project-1-newsletter-subscription-automation) | Form · Google Contacts · Gmail · Sheets | ⭐ Beginner | 2 hrs |
| 2 | [Customer Feedback Collection](#-project-2-customer-feedback-collection) | Form · Gmail · Sheets | ⭐ Beginner | 2 hrs |
| 3 | [Interview Registration & Notifications](#-project-3-interview-registration--notifications) | Form · Gmail × 2 · Sheets | ⭐⭐ Intermediate | 2.5 hrs |
| 4 | [Client Inquiry Management](#-project-4-client-inquiry-management) | Form · Sheets · Gmail × 2 · Google Contacts | ⭐⭐ Intermediate | 3 hrs |
| 5 | [AI Email Classification](#-project-5-ai-powered-email-classification) | Gmail Trigger · LLM Chain · Sheets · Gmail | ⭐⭐⭐ Advanced | 3 hrs |
| 6 | [Meeting Transcript to Notes](#-project-6-meeting-transcript-to-structured-notes) | Form/Webhook · LLM Chain · Google Docs · Gmail | ⭐⭐⭐ Advanced | 3 hrs |
| 7 | [Daily AI News Digest](#-project-7-automated-daily-ai-news-digest) | Schedule Trigger · LLM Chain · Google Docs · Gmail | ⭐⭐⭐ Advanced | 3.5 hrs |

---

## ⏱️ Total Timeline

```
Week 1                          Week 2
─────────────────────────────── ───────────────────────────────
Day 1      Day 2      Day 3     Day 4      Day 5      Day 6-7
Project 1  Project 2  Project 3 Project 4  Project 5  Project 6 & 7
  2 hrs      2 hrs     2.5 hrs   3 hrs      3 hrs       6.5 hrs
```

**Total Estimated Time: ~18 Hours across 7 Projects**

---

## 📁 Repository Structure

```
ai-automation-engineering-n8n-projects/
│
├── 📂 Project-1-Newsletter-Subscription/
│   └── README.md
│
├── 📂 Project-2-Customer-Feedback/
│   └── README.md
│
├── 📂 Project-3-Interview-Registration/
│   └── README.md
│
├── 📂 Project-4-Client-Inquiry/
│   └── README.md
│
├── 📂 Project-5-AI-Email-Classification/
│   └── README.md
│
├── 📂 Project-6-Meeting-Transcript/
│   └── README.md
│
└── 📂 Project-7-Daily-News-Digest/
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
- A form that collects Name, Email, and Interested Topic
- Auto-creation of Google Contacts for every new subscriber
- A personalized welcome email sent via Gmail
- Subscriber records stored in Google Sheets

**Timeline Breakdown:**

| Activity | Time |
|----------|------|
| Understanding requirements | 15 min |
| Designing the workflow | 20 min |
| Building the workflow | 50 min |
| Testing and debugging | 35 min |

📄 [View Full Project Requirements](./Project-1-Newsletter-Subscription/README.md)

---

### 📝 Project 2: Customer Feedback Collection

> **Difficulty:** ⭐ Beginner &nbsp;|&nbsp; **Duration:** 2 Hours

Build a workflow that collects customer feedback through a form, saves it to a spreadsheet, and automatically sends a thank you email.

**Workflow:**
```
Form Trigger → Store Feedback in Google Sheets → Send Thank You Email
```

**What you'll build:**
- A feedback form collecting Name, Email, Feedback Message, and Rating (1–5)
- Automatic storage of all responses in Google Sheets
- A personalized thank you email acknowledging the customer's rating

**Timeline Breakdown:**

| Activity | Time |
|----------|------|
| Understanding requirements | 15 min |
| Designing the workflow | 20 min |
| Building the workflow | 50 min |
| Testing and debugging | 35 min |

📄 [View Full Project Requirements](./Project-2-Customer-Feedback/README.md)

---

### 🗓️ Project 3: Interview Registration & Notifications

> **Difficulty:** ⭐⭐ Intermediate &nbsp;|&nbsp; **Duration:** 2 Hours 30 Minutes

Build a workflow that handles interview registrations by sending confirmation emails to candidates, notifying HR, and logging all data in Google Sheets.

**Workflow:**
```
Form Trigger → Email to Candidate → Email to HR → Store in Google Sheets
```

**What you'll build:**
- An interview registration form collecting Candidate Name, Email, Role, and Interview Date
- Automatic confirmation email to the candidate with role and date details
- Internal notification email sent to the HR team
- Candidate records stored in Google Sheets

**Timeline Breakdown:**

| Activity | Time |
|----------|------|
| Understanding requirements | 15 min |
| Designing the workflow | 25 min |
| Building the workflow | 60 min |
| Testing and debugging | 30 min |

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

**Timeline Breakdown:**

| Activity | Time |
|----------|------|
| Understanding requirements | 15 min |
| Designing the workflow | 25 min |
| Building the workflow | 80 min |
| Testing and debugging | 40 min |

📄 [View Full Project Requirements](./Project-4-Client-Inquiry/README.md)

---

### 🧠 Project 5: AI-Powered Email Classification

> **Difficulty:** ⭐⭐⭐ Advanced &nbsp;|&nbsp; **Duration:** 3 Hours

Build an AI-driven support workflow that reads incoming emails, classifies them by category and priority using a language model, stores the results, and sends an acknowledgement to the customer.

**Workflow:**
```
Gmail Trigger → Read Email → LLM Chain (AI) → Store in Sheets → Send Acknowledgement
```

**What you'll build:**
- A Gmail Trigger that fires on every new support email
- AI-powered classification of Issue Category, Priority Level, and Summary
- Structured storage of all classified emails in Google Sheets
- Automated acknowledgement email to the customer

**Timeline Breakdown:**

| Activity | Time |
|----------|------|
| Understanding requirements | 20 min |
| Designing the workflow | 25 min |
| Building the workflow | 80 min |
| Testing and debugging | 35 min |

📄 [View Full Project Requirements](./Project-5-AI-Email-Classification/README.md)

---

### 📋 Project 6: Meeting Transcript to Structured Notes

> **Difficulty:** ⭐⭐⭐ Advanced &nbsp;|&nbsp; **Duration:** 3 Hours

Build an AI workflow that transforms raw meeting transcripts into structured notes — complete with summaries, action items, and next steps — saved to Google Docs and emailed to participants.

**Workflow:**
```
Form / Webhook → LLM Chain (AI) → Save to Google Docs → Email Summary to Participants
```

**What you'll build:**
- A form or webhook that accepts meeting transcripts
- AI-generated meeting summary, key discussion points, action items, and next steps
- A well-structured Google Doc automatically created with all sections
- A summary email sent to all meeting participants

**Timeline Breakdown:**

| Activity | Time |
|----------|------|
| Understanding requirements | 20 min |
| Designing the workflow | 25 min |
| Building the workflow | 80 min |
| Testing and debugging | 35 min |

📄 [View Full Project Requirements](./Project-6-Meeting-Transcript/README.md)

---

### 📰 Project 7: Automated Daily AI News Digest

> **Difficulty:** ⭐⭐⭐ Advanced &nbsp;|&nbsp; **Duration:** 3 Hours 30 Minutes

Build a fully automated scheduled workflow that collects AI news every morning, generates a digest using a language model, saves it to Google Docs, and emails it to subscribers — all without any manual input.

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

**Timeline Breakdown:**

| Activity | Time |
|----------|------|
| Understanding requirements | 20 min |
| Designing the workflow | 30 min |
| Building the workflow | 90 min |
| Testing and debugging | 30 min |

📄 [View Full Project Requirements](./Project-7-Daily-News-Digest/README.md)

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| **n8n** | Workflow automation platform |
| **Gmail** | Sending automated emails |
| **Google Sheets** | Storing structured data |
| **Google Docs** | Saving AI-generated documents |
| **Google Contacts** | Managing contact records |
| **Basic LLM Chain** | AI-powered text analysis and generation |
| **Schedule Trigger** | Running workflows on a time-based schedule |
| **Form Trigger / Webhook** | Accepting user input to start workflows |

---

## 📋 Submission Checklist

For every project, students must submit:

- [ ] Exported n8n workflow `.json` file
- [ ] Screenshot of the completed workflow canvas
- [ ] Screenshot of the Google Sheet / Doc output
- [ ] Screenshot of the email(s) sent
- [ ] A 150–200 word document explaining the workflow design, node purposes, and challenges

---

## 📊 Evaluation Summary

| Project | Total Marks |
|---------|-------------|
| Project 1 — Newsletter Subscription | 100 |
| Project 2 — Customer Feedback | 100 |
| Project 3 — Interview Registration | 100 |
| Project 4 — Client Inquiry Management | 100 |
| Project 5 — AI Email Classification | 100 |
| Project 6 — Meeting Transcript to Notes | 100 |
| Project 7 — Daily AI News Digest | 100 |
| **Grand Total** | **700 Marks** |

---

## ⚠️ Important Note

> Students are expected to design and implement each workflow **independently**. Project READMEs provide only the requirements — the workflow logic, node configuration, data mapping, and AI prompt design must all be developed by the student.

---

<div align="center">

**Built for learning. Designed for real-world impact.**

</div>
