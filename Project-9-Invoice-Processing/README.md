# **Project 9: Automated Invoice Processing & Expense Approval Workflow**

## **Objective**

Design and build a **production-grade n8n workflow** that automatically processes incoming invoices received via email, extracts structured financial data using AI, routes invoices through an approval process based on amount thresholds, maintains a live expense ledger in Google Sheets, and generates a monthly expense summary report — all without manual data entry.

---

## **Learning Outcomes**

By completing this project, you should be able to:

* Trigger a workflow from incoming Gmail messages containing invoice data.
* Use the Basic LLM Chain to extract structured financial information from unstructured email text.
* Implement threshold-based conditional logic to route invoices for approval.
* Build a Webhook-based approval/rejection mechanism that resumes a waiting workflow.
* Maintain a structured financial ledger in Google Sheets.
* Update existing Google Sheet rows based on approval decisions.
* Use a Schedule Trigger to generate AI-written monthly expense reports.
* Design a stateful, multi-step, approval-gated automation workflow.

---

## **Estimated Time**

**4 Hours**

| Activity                                       | Suggested Time |
| ---------------------------------------------- | -------------- |
| Understanding the requirements                 | 20 minutes     |
| Designing both workflows                       | 35 minutes     |
| Building the invoice processing workflow       | 90 minutes     |
| Building the monthly report workflow           | 25 minutes     |
| Testing approval and rejection paths           | 50 minutes     |

---

## **Project Requirements**

This project consists of **two connected workflows**:

1. **Invoice Processing & Approval Workflow** — triggered when a new invoice email arrives.
2. **Monthly Expense Report Workflow** — triggered on the first day of every month.

---

## **Part 1 — Invoice Processing & Approval Workflow**

### **Trigger**

The workflow must begin automatically when a new email arrives in the connected Gmail inbox using the **Gmail Trigger** node.

> For testing purposes, you will send yourself test emails containing invoice details in the email body. The invoice data should be written as plain text in the email body (e.g., "Invoice from TechSupplies Ltd for $3,200 for cloud hosting services, dated June 15 2025, Invoice #INV-2045").

---

### **Step 1 — Read and Pass Email Content to AI**

Extract the email body text and pass it to a **Basic LLM Chain** node.

Your AI prompt must instruct the model to extract the following fields from the invoice text and return them as a structured JSON object:

```json
{
  "invoice_number": "INV-2045",
  "vendor_name": "TechSupplies Ltd",
  "invoice_date": "2025-06-15",
  "due_date": "2025-07-15",
  "amount": 3200,
  "currency": "USD",
  "category": "Cloud Infrastructure",
  "description": "Monthly cloud hosting services",
  "sender_email": "vendor@techsupplies.com"
}
```

**Expense Categories the AI should assign:**

| Category              | Examples                                      |
| --------------------- | --------------------------------------------- |
| Cloud Infrastructure  | Hosting, servers, storage, CDN                |
| Software & Licenses   | SaaS tools, subscriptions, plugins            |
| Marketing & Ads       | Ad spend, design, campaigns                   |
| Office & Operations   | Rent, utilities, supplies                     |
| Professional Services | Consulting, legal, accounting                 |
| Other                 | Anything that does not fit above              |

> You are responsible for writing a prompt that reliably extracts all fields. If a field cannot be found in the email, the AI should return `null` for that field.

---

### **Step 2 — Generate Invoice ID and Log Initial Entry**

After the AI extracts the data:

1. Generate a unique **Invoice ID** in the format `INV-[YYYYMMDD]-[3-digit-sequence]`  
   Example: `INV-20250615-001`  
   You may use a **Code node** or a **Set node** with an expression for this.

2. Log the invoice as a **new row** in the **Expense Ledger** Google Sheet with:

| Column           | Value                                    |
| ---------------- | ---------------------------------------- |
| Invoice ID       | Auto-generated                           |
| Invoice Number   | Extracted by AI                          |
| Vendor Name      | Extracted by AI                          |
| Invoice Date     | Extracted by AI                          |
| Due Date         | Extracted by AI                          |
| Amount (USD)     | Extracted by AI                          |
| Category         | Assigned by AI                           |
| Description      | Extracted by AI                          |
| Sender Email     | Extracted by AI                          |
| Received At      | Current timestamp                        |
| Approval Status  | `Pending`                                |
| Approved By      | *(blank)*                                |
| Approved At      | *(blank)*                                |
| Notes            | *(blank)*                                |

---

### **Step 3 — Threshold-Based Routing**

After logging the entry, apply the following routing logic using **IF nodes**:

| Amount          | Action                          |
| --------------- | ------------------------------- |
| Below $500      | Auto-approve immediately        |
| $500 – $2,000   | Send for manager approval       |
| Above $2,000    | Send for senior approval        |

---

### **Step 4A — Auto-Approval (Below $500)**

1. **Update the Google Sheet row** — set `Approval Status` to `Auto-Approved`, `Approved By` to `System`, and `Approved At` to current timestamp.
2. **Send a confirmation email** to the vendor's email (from the AI-extracted `sender_email`):
   - Confirm that the invoice has been received and approved.
   - Include the Invoice ID, amount, and expected payment timeline.
3. **Send an internal notification** to yourself confirming the auto-approval.

---

### **Step 4B — Manager Approval Request ($500 – $2,000)**

1. **Send an approval request email** to the manager (use your own email for testing).

   The email must include:
   - Invoice ID, Vendor Name, Amount, Category, and Description.
   - An **Approve button** (link to a Webhook URL with `?decision=approved&invoice_id=INV-xxx`).
   - A **Reject button** (link to the same Webhook URL with `?decision=rejected&invoice_id=INV-xxx`).

2. The workflow **waits** for the manager to click one of the buttons.

3. A **Webhook node** receives the manager's decision and resumes the workflow.

4. Based on the decision:

   **If Approved:**
   - Update the Google Sheet row: `Approval Status = Approved`, `Approved By = Manager`.
   - Send a confirmation email to the vendor.
   - Send an internal notification to yourself.

   **If Rejected:**
   - Update the Google Sheet row: `Approval Status = Rejected`.
   - Send a rejection email to the vendor explaining that the invoice could not be processed.
   - Send an internal notification to yourself.

---

### **Step 4C — Senior Approval Request (Above $2,000)**

Follow the same approval pattern as Step 4B, but:

- The approval request email must be sent to a **senior approver** (use a second email address for testing, or CC yourself).
- The email subject must clearly indicate: `[HIGH VALUE] Invoice Approval Required — $X,XXX`.
- The approval email body must also include an **AI-generated risk note** — pass the invoice details back to the Basic LLM Chain and ask it to briefly assess whether the invoice looks standard or raises any concerns (e.g., unusually high amount, vague description, unknown vendor).

---

### **Step 5 — Send Vendor Acknowledgement on Receipt**

Immediately after Step 1 (regardless of amount), send an **acknowledgement email** to the vendor (use `sender_email` extracted by AI):

- Confirm that the invoice has been received.
- Provide the auto-generated Invoice ID for their reference.
- Mention that the team will process it within the standard timeline.

---

## **Part 2 — Monthly Expense Report Workflow**

### **Trigger**

A **separate workflow** triggered on the **1st of every month at 9:00 AM** using the **Schedule Trigger** node.

### **Steps**

1. **Read all rows** from the Expense Ledger Google Sheet.
2. Filter rows where the invoice date falls within the **previous calendar month**.
3. Pass the filtered data to a **Basic LLM Chain** node.
4. The AI must generate a monthly expense report including:
   - Total amount approved for the month.
   - Breakdown by category (total per category).
   - Count of auto-approved vs. manually approved vs. rejected invoices.
   - Top 3 vendors by spend.
   - Any observations or flags (e.g., unusually high spend in a category).
5. **Save the report** to a new Google Doc titled: `Expense Report — [Month] [Year]`.
6. **Email the report** to yourself.
   - Subject: `Monthly Expense Report — [Month Year]`
   - Body: The AI-generated summary in a clean, readable format.

---

## **Expected Workflow Diagram**

```
Gmail Trigger (New Invoice Email)
      ↓
Extract Invoice Data (Basic LLM Chain → JSON)
      ↓
Generate Invoice ID + Log to Google Sheets (Status: Pending)
      ↓
Send Vendor Acknowledgement Email (Gmail)
      ↓
IF Amount < $500 ──────────────────► Auto-Approve
                                          │
                                  Update Sheet + Email Vendor
                                  + Internal Notification

IF $500 – $2,000 ──────────────► Manager Approval Email (with Webhook links)
                                          │
                                    Webhook receives decision
                                          │
                              Approved ──┤├── Rejected
                                 │                │
                          Update Sheet     Update Sheet
                          Email Vendor     Email Vendor
                          Notify Self      Notify Self

IF > $2,000 ───────────────────► Senior Approval Email (with AI risk note)
                                          │
                                    Webhook receives decision
                                          │
                              Approved ──┤├── Rejected
                                 │                │
                          Update Sheet     Update Sheet
                          Email Vendor     Email Vendor
                          Notify Self      Notify Self


Schedule Trigger (1st of Month, 9AM)
      ↓
Read Expense Ledger (Google Sheets)
      ↓
Filter by Previous Month
      ↓
AI Monthly Summary (Basic LLM Chain)
      ↓
Save to Google Docs
      ↓
Send Report Email (Gmail)
```

---

## **Deliverables**

Each student must submit the following:

1. Exported **n8n workflow (.json)** — Invoice Processing Workflow.
2. Exported **n8n workflow (.json)** — Monthly Report Workflow.
3. Screenshot of both completed workflow canvases.
4. Screenshot of the Expense Ledger Google Sheet with at least **6 test invoices** covering all three approval tiers.
5. Screenshot of the approval request email (showing Approve/Reject links).
6. Screenshot of the vendor acknowledgement email.
7. Screenshot of the vendor confirmation email after approval.
8. Screenshot of the vendor rejection email after rejection.
9. Screenshot of the monthly expense report Google Doc.
10. Screenshot of the monthly report email.
11. A document (200–250 words) explaining:
    * How the AI extracts invoice fields and how you handled missing or ambiguous data.
    * How the threshold routing logic works.
    * How the Webhook-based approval mechanism is implemented.
    * Any challenges faced and how you resolved them.

---

## **Evaluation Criteria**

| Criteria                                              |         Marks |
| ----------------------------------------------------- | ------------: |
| Gmail Trigger fires correctly                         |            05 |
| AI data extraction with structured JSON output        |            20 |
| Invoice ID generation and initial Sheet logging       |            10 |
| Vendor acknowledgement email on receipt               |            05 |
| Threshold-based routing (all 3 tiers)                 |            15 |
| Auto-approval path works correctly                    |            05 |
| Manager approval with Webhook resume                  |            15 |
| Senior approval with AI risk note                     |            10 |
| Sheet rows updated correctly after decisions          |            05 |
| Monthly report workflow (Schedule + AI + Doc + Email) |            05 |
| Documentation quality                                 |            05 |
| **Total**                                             | **100 Marks** |

---

## **Submission Deadline**

**Recommended Completion Time:** 4 Hours

> **Note:** This is a production-level project. The most technically challenging part is the Webhook-based approval pattern — the workflow must pause and wait for an external action to resume it. Students must independently research and implement the **Wait node** or equivalent mechanism in n8n to achieve this. Partial implementations will receive partial marks.
