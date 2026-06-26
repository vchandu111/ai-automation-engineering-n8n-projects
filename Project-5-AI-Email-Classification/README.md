# **Project 5: AI-Powered Customer Support Email Classification**

## **Objective**

Design and build an **n8n workflow** that automatically classifies incoming customer support emails using AI. The workflow should read the email, analyze its content using a language model, store the results in Google Sheets, and send an acknowledgement email to the customer.

---

## **Learning Outcomes**

By completing this project, you should be able to:

* Trigger a workflow using the Gmail Trigger node.
* Use the Basic LLM Chain node to send content to an AI model.
* Extract structured information from AI-generated responses.
* Store AI-analyzed data in Google Sheets.
* Send automated acknowledgement emails using Gmail.
* Build an AI-integrated automation workflow in n8n.

---

## **Estimated Time**

**3 Hours**

| Activity                       | Suggested Time |
| ------------------------------ | -------------- |
| Understanding the requirements | 20 minutes     |
| Designing the workflow         | 25 minutes     |
| Building the workflow          | 80 minutes     |
| Testing and debugging          | 35 minutes     |

---

## **Project Requirements**

You are required to build an automation workflow that processes every new incoming support email and classifies it using AI.

### **Trigger**

The workflow must begin automatically when a new email arrives in the connected Gmail inbox.

---

## **Workflow Requirements**

The workflow must perform the following actions in sequence:

1. **Trigger** when a new email is received using the **Gmail Trigger** node.
2. **Read the email content** from the incoming message.
3. **Send the email content** to the **Basic LLM Chain** node for AI analysis.
4. The AI must extract and return the following details:
   * **Issue Category** (e.g., Billing, Technical, Account, General)
   * **Priority Level** (e.g., Low, Medium, High)
   * **Short Summary** of the email content
5. **Store all details** in **Google Sheets**.
6. **Send an acknowledgement email** to the customer using **Gmail**.

---

## **Google Sheets Requirements**

Create a Google Sheet with the following columns:

* Customer Name
* Customer Email
* Subject
* Issue Category
* Priority
* AI Summary
* Received Date

Each processed email should be stored as a new row in the sheet.

---

## **Email Requirements**

The acknowledgement email sent to the customer must:

* Thank the customer for contacting support.
* Inform them that their issue is currently being reviewed.
* Reference the subject of their original email.
* End with a professional and reassuring closing message.

---

## **AI Prompt Guidelines**

When configuring the **Basic LLM Chain** node, your prompt should instruct the AI to:

* Read the provided email content.
* Identify the type or category of the issue.
* Determine the urgency or priority level.
* Generate a concise summary (2–3 sentences).

You are responsible for writing an effective prompt that produces consistent and structured output.

---

## **Workflow Constraints**

* The workflow must begin with a **Gmail Trigger** node.
* Use the **Basic LLM Chain** node for AI-based classification.
* Use **Google Sheets** to store all analyzed email data.
* Use **Gmail** to send the acknowledgement email.
* Ensure the AI output is correctly parsed and mapped to the Google Sheets columns.
* The workflow should execute automatically for each new incoming email.

---

## **Expected Workflow**

The completed workflow should follow this sequence:

```
Gmail Trigger (New Email Received)
      ↓
Read Email Content
      ↓
Analyze with Basic LLM Chain (AI)
      ↓
Store Results (Google Sheets)
      ↓
Send Acknowledgement Email (Gmail)
```

---

## **Deliverables**

Each student must submit the following:

1. Exported **n8n workflow (.json)**.
2. Screenshot of the completed workflow.
3. Screenshot of the Google Sheet showing classified email entries.
4. Screenshot of the acknowledgement email sent to the customer.
5. Screenshot of the AI prompt configured in the Basic LLM Chain node.
6. A brief document (150–200 words) explaining:
   * The workflow design.
   * How the AI classification works.
   * The purpose of each node used.
   * Any challenges faced during implementation.

---

## **Evaluation Criteria**

| Criteria                            |         Marks |
| ----------------------------------- | ------------: |
| Workflow triggers correctly         |            20 |
| AI classification accuracy          |            25 |
| Correct use of required n8n nodes   |            15 |
| Proper data mapping                 |            15 |
| Google Sheets integration           |            10 |
| Acknowledgement email quality       |            05 |
| AI prompt quality                   |            05 |
| Documentation and submission        |            05 |
| **Total**                           | **100 Marks** |

---

## **Submission Deadline**

**Recommended Completion Time:** 3 Hours

> **Note:** Students are expected to design and implement the workflow independently. Only the requirements are provided; the workflow logic, node configuration, AI prompt design, and implementation details should be developed by the student.
