# **Project 8: AI-Powered Lead Qualification & CRM Pipeline**

## **Objective**

Design and build a **production-grade n8n workflow** that automatically qualifies incoming leads using AI, routes them based on their score, triggers appropriate follow-up actions for each tier, and maintains a live CRM dashboard in Google Sheets — all without any manual intervention.

---

## **Learning Outcomes**

By completing this project, you should be able to:

* Accept leads from multiple entry points (form and webhook).
* Use the Basic LLM Chain to score and qualify leads with structured AI output.
* Implement conditional branching using IF nodes to route leads by tier.
* Trigger different actions for different lead quality levels.
* Integrate Google Calendar to book meetings automatically.
* Build and maintain a CRM dashboard in Google Sheets.
* Use a Schedule Trigger to generate a weekly AI-written pipeline summary.
* Design a multi-path, production-ready automation workflow.

---

## **Estimated Time**

**4 Hours**

| Activity                              | Suggested Time |
| ------------------------------------- | -------------- |
| Understanding the requirements        | 20 minutes     |
| Designing the workflow and branches   | 35 minutes     |
| Building the core workflow            | 90 minutes     |
| Building the weekly report workflow   | 30 minutes     |
| Testing all three lead tiers          | 45 minutes     |

---

## **Project Requirements**

This project consists of **two connected workflows**:

1. **Lead Intake & Routing Workflow** — triggered when a lead is submitted.
2. **Weekly Pipeline Report Workflow** — triggered every Monday morning on a schedule.

---

## **Part 1 — Lead Intake & Routing Workflow**

### **Entry Points**

Your workflow must accept leads from **two sources**:

- **Source A:** An n8n Form Trigger (manual web form).
- **Source B:** A Webhook node (simulating a third-party integration such as a landing page or CRM tool).

Both sources must feed into the same workflow pipeline. The data format from both must be normalized before processing.

### **Input Fields**

Regardless of the source, every lead must provide the following fields:

* Full Name
* Email Address
* Company Name
* Job Title
* Budget (approximate, in USD)
* Interested Product or Service
* Message or Additional Notes

---

### **Step 1 — Normalize Input Data**

Since leads arrive from two different sources (Form and Webhook), their field names or formats may differ. Use a **Set node** or **Code node** to normalize all incoming data into a consistent structure before passing it to the AI.

**Output of this step must include:**

* `name`
* `email`
* `company`
* `job_title`
* `budget`
* `interest`
* `message`
* `source` (either `"form"` or `"webhook"`)
* `submitted_at` (current timestamp)

---

### **Step 2 — AI Lead Scoring**

Pass the normalized lead data to a **Basic LLM Chain** node.

Your AI prompt must instruct the model to evaluate the lead and return a **structured JSON response** containing:

```json
{
  "score": 85,
  "tier": "High",
  "reason": "Senior decision-maker at a mid-size company with a clear budget and specific interest.",
  "recommended_action": "Book a demo call immediately."
}
```

**Scoring Criteria to include in your prompt:**

| Factor              | Weight |
| ------------------- | ------ |
| Job Title / Seniority | High |
| Budget Range        | High   |
| Company Size (inferred) | Medium |
| Clarity of Interest | Medium |
| Message Quality     | Low    |

**Tier Definitions:**

| Tier   | Score Range | Meaning                        |
| ------ | ----------- | ------------------------------ |
| High   | 75 – 100    | Strong prospect, act immediately |
| Medium | 45 – 74     | Nurture over time              |
| Low    | 0 – 44      | Not a fit right now            |

> You are responsible for writing the AI prompt that reliably produces this structured JSON output. The downstream IF nodes depend on the `tier` field being exactly `"High"`, `"Medium"`, or `"Low"`.

---

### **Step 3 — Conditional Routing (IF Nodes)**

After extracting the `tier` value from the AI response, use **IF nodes** to route the lead into one of three branches:

```
AI Scoring
    ↓
IF tier == "High"  →  High-Value Branch
IF tier == "Medium" →  Nurture Branch
IF tier == "Low"   →  Low-Priority Branch
```

---

### **Step 4A — High-Value Lead Branch**

When a lead is classified as **High**, the workflow must:

1. **Send an immediate personalized outreach email** via Gmail.
   - Address the lead by name.
   - Reference their company and area of interest.
   - Invite them to book a call.
   - Keep the tone professional and confident.

2. **Create a Google Calendar event** for a discovery call.
   - Schedule it 2 business days from the submission date.
   - Title: `Discovery Call — [Lead Name] ([Company])`
   - Include the lead's email and interest in the event description.

3. **Send an internal alert email to yourself** via a second Gmail node.
   - Include: Lead Name, Email, Company, Job Title, Budget, AI Score, and AI Reason.
   - Subject: `🔥 High-Value Lead: [Lead Name]`

---

### **Step 4B — Medium-Value Lead Branch**

When a lead is classified as **Medium**, the workflow must:

1. **Send a nurture email** via Gmail.
   - Thank them for their interest.
   - Share a helpful resource or brief product overview.
   - End with a soft call-to-action (e.g., "Reply if you'd like to learn more").

2. **Add a follow-up reminder row** in a dedicated "Follow-Up Queue" sheet in Google Sheets.
   - Columns: Name, Email, Company, Score, Tier, Submitted Date, Follow-Up Date (7 days later).

---

### **Step 4C — Low-Priority Lead Branch**

When a lead is classified as **Low**, the workflow must:

1. **Send a polite acknowledgement email** via Gmail.
   - Thank the lead for reaching out.
   - Let them know the team will be in touch if there is a fit.
   - Do not make any promises or schedule a call.

2. **Log the lead in the CRM sheet** (marked as Low priority — no follow-up action flagged).

---

### **Step 5 — Log All Leads in the CRM Dashboard (Google Sheets)**

Regardless of the tier, every lead must be logged in a master **CRM Dashboard** Google Sheet.

**Required columns:**

| Column            | Description                                 |
| ----------------- | ------------------------------------------- |
| Lead ID           | Auto-generated unique ID (e.g., `LEAD-001`) |
| Full Name         | Lead's name                                 |
| Email             | Lead's email                                |
| Company           | Company name                                |
| Job Title         | Lead's job title                            |
| Budget            | Stated budget                               |
| Interest          | Product or service of interest              |
| Source            | `form` or `webhook`                         |
| AI Score          | Numeric score from the AI                   |
| Tier              | High / Medium / Low                         |
| AI Reason         | Reason provided by the AI                   |
| Recommended Action| AI's recommended next step                  |
| Submitted At      | Timestamp of submission                     |
| Status            | Default: `New`                              |

---

## **Part 2 — Weekly Pipeline Report Workflow**

### **Trigger**

This is a **separate workflow** triggered every **Monday at 8:00 AM** using the **Schedule Trigger** node.

### **Steps**

1. **Read all rows** from the CRM Dashboard Google Sheet.
2. **Pass the data** to a **Basic LLM Chain** node.
3. The AI must generate a structured weekly summary including:
   - Total leads received this week.
   - Breakdown by tier (High / Medium / Low).
   - Top 3 high-value leads to prioritize.
   - Key observations or patterns noticed.
4. **Send the report** via Gmail to yourself.
   - Subject: `Weekly Lead Pipeline Report — [Date]`
   - Body: The AI-generated summary in a clean, readable format.

---

## **Expected Workflow Diagram**

```
Form Trigger ──┐
               ├──► Normalize Data ──► AI Lead Scoring ──► Extract Tier
Webhook    ────┘                                                  │
                                              ┌───────────────────┼───────────────────┐
                                              ▼                   ▼                   ▼
                                         High Branch       Medium Branch         Low Branch
                                              │                   │                   │
                                    Outreach Email +      Nurture Email +      Polite Email +
                                    Calendar Event +      Follow-Up Sheet      Log to CRM
                                    Internal Alert
                                              │                   │                   │
                                              └───────────────────┴───────────────────┘
                                                                  │
                                                        Log to CRM Dashboard


Schedule Trigger (Every Monday 8AM)
      ↓
Read CRM Google Sheet
      ↓
AI Weekly Summary (Basic LLM Chain)
      ↓
Send Pipeline Report Email (Gmail)
```

---

## **Deliverables**

Each student must submit the following:

1. Exported **n8n workflow (.json)** — Lead Intake Workflow.
2. Exported **n8n workflow (.json)** — Weekly Report Workflow.
3. Screenshot of both completed workflow canvases.
4. Screenshot of the CRM Dashboard Google Sheet with at least 5 test leads (across all three tiers).
5. Screenshot of the Follow-Up Queue sheet with at least 2 medium-tier entries.
6. Screenshot of the High-value outreach email sent to a test lead.
7. Screenshot of the Google Calendar event created for a High-tier lead.
8. Screenshot of the internal alert email received.
9. Screenshot of the weekly pipeline report email.
10. A document (200–250 words) explaining:
    * How the AI scoring and branching logic works.
    * How you handled data normalization from two entry points.
    * How you structured your AI prompt to produce consistent JSON output.
    * Any challenges faced and how you resolved them.

---

## **Evaluation Criteria**

| Criteria                                        |         Marks |
| ----------------------------------------------- | ------------: |
| Dual entry points working correctly             |            10 |
| Data normalization (Set / Code node)            |            05 |
| AI scoring with structured JSON output          |            20 |
| Conditional branching (all 3 tiers work)        |            15 |
| High-tier branch (email + calendar + alert)     |            15 |
| Medium-tier branch (nurture email + follow-up)  |            10 |
| Low-tier branch (acknowledgement + CRM log)     |            05 |
| CRM Dashboard completeness and accuracy         |            10 |
| Weekly pipeline report workflow                 |            05 |
| Documentation quality                           |            05 |
| **Total**                                       | **100 Marks** |

---

## **Submission Deadline**

**Recommended Completion Time:** 4 Hours

> **Note:** This is a production-level project. Students must independently design the branching logic, write effective AI prompts that return structured JSON, and handle edge cases such as missing fields or unexpected AI output formats. Partial implementations will receive partial marks.
