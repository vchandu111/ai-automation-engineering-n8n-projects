# **Project 10: Multi-Channel Support Ticketing System with SLA & Escalation**

## **Objective**

Design and build a **production-grade n8n support operations system** consisting of multiple coordinated workflows. The system should receive support requests from two channels (email and webhook), classify and triage them using AI, assign ticket IDs, route tickets to the appropriate team, monitor SLA deadlines, escalate overdue tickets automatically, and deliver daily and weekly operational reports — all running autonomously without any manual intervention.

---

## **Learning Outcomes**

By completing this project, you should be able to:

* Build a multi-workflow system where separate workflows coordinate with each other through shared data in Google Sheets.
* Trigger workflows from both a Gmail Trigger and a Webhook simultaneously.
* Use AI to triage, classify, and generate responses for incoming support requests.
* Generate and manage unique ticket IDs.
* Implement SLA deadline tracking using timestamps and scheduled workflows.
* Build an escalation workflow that identifies and acts on overdue tickets.
* Route notifications to different teams based on AI-assigned department and urgency.
* Generate AI-written operational summaries from tabular Sheets data.
* Design a complete, autonomous, production-grade support operations system.

---

## **Estimated Time**

**5 Hours**

| Activity                                              | Suggested Time |
| ----------------------------------------------------- | -------------- |
| Understanding the full system requirements            | 25 minutes     |
| Designing all four workflows and their interactions   | 40 minutes     |
| Building Workflow 1 (Ticket Intake)                   | 75 minutes     |
| Building Workflow 2 (SLA Monitor & Escalation)        | 45 minutes     |
| Building Workflow 3 (Daily Digest)                    | 30 minutes     |
| Building Workflow 4 (Ticket Resolution)               | 30 minutes     |
| End-to-end testing across all workflows               | 55 minutes     |

---

## **System Overview**

This project is a **system of four coordinated workflows** sharing a central Google Sheets database:

| Workflow | Trigger | Purpose |
|----------|---------|---------|
| Workflow 1 — Ticket Intake | Gmail Trigger + Webhook | Receive, classify, route, and log new tickets |
| Workflow 2 — SLA Monitor | Schedule Trigger (every hour) | Detect overdue tickets and escalate them |
| Workflow 3 — Daily Digest | Schedule Trigger (every day, 8AM) | Send daily ticket summary to support manager |
| Workflow 4 — Ticket Resolution | Webhook | Receive ticket close/update events and update records |

All four workflows read from and write to the same **Ticket Database** Google Sheet.

---

## **Google Sheets Setup**

Before building any workflow, create a Google Sheet called **Support Ticket Database** with the following columns:

| Column            | Description                                                      |
| ----------------- | ---------------------------------------------------------------- |
| Ticket ID         | Auto-generated unique ID (e.g., `TKT-20250615-001`)             |
| Customer Name     | Name of the person who submitted the request                     |
| Customer Email    | Email of the customer                                            |
| Channel           | `email` or `webhook`                                             |
| Subject           | Subject line or request title                                    |
| Description       | Full content of the support request                              |
| Department        | AI-assigned: `Technical`, `Billing`, `Account`, `General`       |
| Urgency           | AI-assigned: `Critical`, `High`, `Medium`, `Low`                |
| AI Summary        | 1–2 sentence AI-generated summary of the issue                  |
| Assigned Team Email | Email address of the team the ticket was routed to             |
| Status            | `Open`, `Escalated`, `Resolved`, `Closed`                       |
| SLA Deadline      | Calculated based on urgency (see SLA table below)               |
| Opened At         | Timestamp when ticket was created                               |
| Escalated At      | Timestamp when ticket was escalated (blank if not escalated)    |
| Resolved At       | Timestamp when ticket was resolved (blank if open)              |
| Resolution Notes  | Notes added when ticket is resolved                             |
| Escalation Count  | Number of times this ticket has been escalated (default: `0`)   |

---

## **SLA Definitions**

| Urgency   | SLA Response Time | Meaning                                           |
| --------- | ----------------- | ------------------------------------------------- |
| Critical  | 1 hour            | System down, data loss, business-critical issue   |
| High      | 4 hours           | Major feature broken, significant business impact |
| Medium    | 24 hours          | Minor issue, workaround available                 |
| Low       | 72 hours          | General inquiry, feature request, cosmetic issue  |

The **SLA Deadline** for each ticket is calculated as: `Opened At + SLA Time for that Urgency Level`.

---

## **Team Routing**

Route tickets to different teams based on the AI-assigned department. Use the following mapping (replace with your own test email addresses):

| Department | Assigned Team Email           |
| ---------- | ----------------------------- |
| Technical  | technical-team@yourdomain.com |
| Billing    | billing-team@yourdomain.com   |
| Account    | account-team@yourdomain.com   |
| General    | support-team@yourdomain.com   |

> For testing, you may use your own email address for all teams, but the subject line must clearly reflect which team is being notified.

---

## **Workflow 1 — Ticket Intake**

### **Triggers**

This workflow has **two entry points**:

- **Entry Point A:** Gmail Trigger — fires when a new email arrives in a designated support inbox.
- **Entry Point B:** Webhook — receives POST requests simulating tickets from a third-party tool (e.g., a web chat widget or external form).

Both entry points must feed into the same processing pipeline after normalization.

### **Step 1 — Normalize Input**

Use a **Set node** or **Code node** to extract and standardize the following fields from both sources:

* `customer_name`
* `customer_email`
* `subject`
* `description`
* `channel` (`email` or `webhook`)
* `received_at` (current timestamp)

---

### **Step 2 — AI Triage and Classification**

Pass the normalized data to a **Basic LLM Chain** node.

Your prompt must instruct the AI to analyze the support request and return a structured JSON response:

```json
{
  "department": "Technical",
  "urgency": "High",
  "summary": "Customer is unable to log in after a password reset. The account appears locked.",
  "suggested_reply": "Thank you for reaching out. We have received your request regarding login access and our technical team will look into this within 4 hours."
}
```

**Classification Guidelines to include in your prompt:**

*Department Classification:*
- `Technical` — bugs, errors, login issues, feature not working
- `Billing` — invoices, charges, refunds, payment failures
- `Account` — profile changes, cancellations, access requests
- `General` — general questions, feedback, feature requests

*Urgency Classification:*
- `Critical` — service completely down, data loss, security breach
- `High` — major functionality broken, cannot complete core tasks
- `Medium` — partial issue, workaround exists
- `Low` — minor inconvenience, general question, enhancement request

> You are responsible for designing a prompt that produces consistent, structured JSON. The downstream routing and SLA logic depends entirely on the `department` and `urgency` fields being valid and correctly cased.

---

### **Step 3 — Generate Ticket ID and Calculate SLA Deadline**

1. Generate a unique **Ticket ID** in the format: `TKT-[YYYYMMDD]-[3-digit-sequence]`  
   Example: `TKT-20250615-007`

2. Calculate the **SLA Deadline** based on the AI-assigned urgency:
   - Critical: current time + 1 hour
   - High: current time + 4 hours
   - Medium: current time + 24 hours
   - Low: current time + 72 hours

Use a **Code node** or **Set node with expressions** to implement this logic.

---

### **Step 4 — Log Ticket in Google Sheets**

Write a new row to the **Support Ticket Database** sheet with all fields populated. Set:
- `Status` = `Open`
- `Escalation Count` = `0`

---

### **Step 5 — Send Customer Acknowledgement Email**

Send an automated email to the customer via **Gmail**:

- Address the customer by name.
- Confirm that their ticket has been received.
- Include the **Ticket ID** for reference.
- Mention the urgency level and the **SLA response time** they can expect.
- Use the **AI-generated `suggested_reply`** as the body of the email (you may customize the format around it).

---

### **Step 6 — Route to Assigned Team**

Send a **team notification email** via a second Gmail node to the assigned team's email address:

The email must include:
- Ticket ID
- Customer Name and Email
- Department and Urgency
- AI Summary of the issue
- Full description of the request
- SLA Deadline (formatted as a readable date and time)
- Subject: `[URGENCY] New Ticket Assigned — TKT-XXXXXXXX-XXX`

For **Critical** urgency tickets, the subject line must begin with `🚨` and the email must also be CC'd to yourself as a safety net.

---

## **Workflow 2 — SLA Monitor & Escalation**

### **Trigger**

**Schedule Trigger** — runs **every hour**.

### **Steps**

1. **Read all rows** from the Support Ticket Database where `Status` = `Open` or `Escalated`.
2. For each row, **compare the current time against the SLA Deadline**.
3. If the current time has **passed the SLA Deadline**:

   a. **Update the row** in Google Sheets:
      - Set `Status` = `Escalated`
      - Set `Escalated At` = current timestamp
      - Increment `Escalation Count` by 1

   b. **Send an escalation alert email** to yourself (the support manager):
      - Subject: `⚠️ SLA Breached — [Ticket ID]`
      - Body: Include Ticket ID, Customer Name, Department, Urgency, AI Summary, how long the SLA has been breached, and the escalation count.

   c. **Send a follow-up nudge email** to the assigned team:
      - Remind them that this ticket has breached its SLA.
      - Include all ticket details and a note on how long it has been overdue.

4. If a ticket's `Escalation Count` reaches **3 or more**, send a **critical escalation email** to yourself with a subject: `🚨 CRITICAL: Ticket [ID] has been escalated 3+ times — Immediate attention required`.

> The workflow must handle cases where no overdue tickets exist without failing. Use error handling or a conditional check before the email step.

---

## **Workflow 3 — Daily Digest**

### **Trigger**

**Schedule Trigger** — runs every day at **8:00 AM**.

### **Steps**

1. **Read all rows** from the Support Ticket Database.
2. Pass the data to a **Basic LLM Chain** node.
3. The AI must generate a daily operations summary including:
   - Total open tickets (by department and urgency).
   - Tickets that breached SLA in the last 24 hours.
   - Tickets resolved in the last 24 hours.
   - Average response time for resolved tickets.
   - Top 3 most urgent open tickets requiring immediate attention.
   - One-line recommendation or observation from the AI.
4. **Send the digest email** to yourself via Gmail:
   - Subject: `Daily Support Digest — [Date]`
   - Body: The AI-generated summary in a clean, readable format.

---

## **Workflow 4 — Ticket Resolution**

### **Trigger**

**Webhook** — receives a POST request when a support agent closes or updates a ticket.

### **Expected Webhook Payload**

```json
{
  "ticket_id": "TKT-20250615-007",
  "resolved_by": "Agent Name",
  "resolution_notes": "Resolved by resetting the user's MFA settings.",
  "status": "Resolved"
}
```

### **Steps**

1. Receive the webhook payload.
2. **Find the matching row** in the Support Ticket Database by `Ticket ID`.
3. **Update the row**:
   - Set `Status` = `Resolved` (or `Closed` if specified).
   - Set `Resolved At` = current timestamp.
   - Set `Resolution Notes` = from payload.
4. **Send a resolution email** to the customer via Gmail:
   - Address them by name.
   - Confirm that their issue (Ticket ID) has been resolved.
   - Include a brief summary of the resolution.
   - Thank them for their patience.
   - Invite them to reopen if the issue persists.

---

## **Expected System Diagram**

```
┌─────────────────────────────────────────────────────────────────┐
│                     WORKFLOW 1 — TICKET INTAKE                  │
│                                                                  │
│  Gmail Trigger ─┐                                               │
│                 ├─► Normalize ─► AI Triage ─► Generate ID      │
│  Webhook ───────┘               & Classify    & SLA Deadline    │
│                                                    │             │
│                                          Log to Google Sheets   │
│                                                    │             │
│                                     ┌──────────────┴──────┐    │
│                                     ▼                      ▼    │
│                             Acknowledge Customer    Route to Team│
│                                  (Gmail)              (Gmail)    │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│              WORKFLOW 2 — SLA MONITOR (Every Hour)              │
│                                                                  │
│  Schedule Trigger ─► Read Open Tickets ─► Check SLA Deadlines  │
│                                                    │             │
│                                    ┌───────────────┴──────┐    │
│                                    ▼                       ▼    │
│                             SLA Breached?            Within SLA  │
│                                    │                  (skip)     │
│                          Update Sheet (Escalated)               │
│                          Alert Manager (Gmail)                  │
│                          Nudge Team (Gmail)                     │
│                          If Count ≥ 3 → Critical Alert          │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│              WORKFLOW 3 — DAILY DIGEST (8AM Daily)              │
│                                                                  │
│  Schedule Trigger ─► Read All Tickets ─► AI Summary            │
│                                               │                  │
│                                       Send Digest Email         │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│              WORKFLOW 4 — TICKET RESOLUTION (Webhook)           │
│                                                                  │
│  Webhook ─► Find Ticket in Sheets ─► Update Status & Notes     │
│                                               │                  │
│                                    Send Resolution Email to      │
│                                    Customer (Gmail)              │
└─────────────────────────────────────────────────────────────────┘

                    All Workflows Share:
              ┌─────────────────────────────┐
              │   Support Ticket Database   │
              │       (Google Sheets)       │
              └─────────────────────────────┘
```

---

## **Deliverables**

Each student must submit the following:

1. Exported **n8n workflow (.json)** for all **four workflows** (4 separate files).
2. Screenshot of all four completed workflow canvases.
3. Screenshot of the **Support Ticket Database** Google Sheet with at least **8 test tickets** across all departments and urgency levels.
4. Screenshot of a **customer acknowledgement email** received after ticket creation.
5. Screenshot of a **team routing email** for a Critical urgency ticket.
6. Screenshot of an **SLA breach escalation alert** email.
7. Screenshot of a **ticket resolution email** sent to a customer.
8. Screenshot of a **daily digest email**.
9. A document (250–300 words) explaining:
   * How the four workflows interact with each other through the shared Google Sheet.
   * How the AI triage prompt is structured and what makes it reliable.
   * How the SLA monitoring logic works using timestamps.
   * The most technically challenging part of the project and how you solved it.
   * Any edge cases you handled (e.g., no overdue tickets, missing fields in webhook payload).

---

## **Evaluation Criteria**

| Criteria                                                   |         Marks |
| ---------------------------------------------------------- | ------------: |
| Workflow 1: Dual entry points (email + webhook) working    |            10 |
| Workflow 1: AI triage with structured JSON output          |            15 |
| Workflow 1: Ticket ID + SLA Deadline calculation           |            10 |
| Workflow 1: Customer acknowledgement email                 |            05 |
| Workflow 1: Team routing email with urgency-based subject  |            05 |
| Workflow 2: SLA monitoring logic (correct timestamp check) |            15 |
| Workflow 2: Escalation email to manager and team           |            05 |
| Workflow 2: Critical alert after 3+ escalations            |            05 |
| Workflow 3: Daily digest with AI summary                   |            10 |
| Workflow 4: Ticket resolution webhook + email to customer  |            10 |
| Google Sheet accuracy across all workflows                 |            05 |
| Documentation quality                                      |            05 |
| **Total**                                                  | **100 Marks** |

---

## **Submission Deadline**

**Recommended Completion Time:** 5 Hours

> **Note:** This is the most complex project in this course. It requires building **four coordinated workflows** that share a single data source. Students must independently design the system architecture, manage shared state through Google Sheets, write reliable AI prompts, and implement timestamp-based SLA logic. This project is intentionally open-ended — there is no single correct implementation. Students are evaluated on whether the system works correctly as a whole, not just whether individual nodes are configured. Partial implementations will receive partial marks.
