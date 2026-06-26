# **Project 2: Customer Feedback Collection Automation**

## **Objective**

Design and build an **n8n workflow** that automates the process of collecting customer feedback. The workflow should store feedback in Google Sheets and automatically send a thank you email to the customer upon submission.

---

## **Learning Outcomes**

By completing this project, you should be able to:

* Trigger a workflow using a Form Trigger node.
* Store structured data in Google Sheets using n8n.
* Send automated, personalized emails using Gmail.
* Map form field data across multiple nodes.
* Build a functional end-to-end automation workflow.

---

## **Estimated Time**

**2 Hours**

| Activity                       | Suggested Time |
| ------------------------------ | -------------- |
| Understanding the requirements | 15 minutes     |
| Designing the workflow         | 20 minutes     |
| Building the workflow          | 50 minutes     |
| Testing and debugging          | 35 minutes     |

---

## **Project Requirements**

You are required to build an automation workflow that performs the following tasks whenever a customer submits a feedback form.

### **Input Form Fields**

Your form must collect the following information:

* Customer Name
* Email
* Feedback Message
* Rating (1–5)

---

## **Workflow Requirements**

The workflow must perform the following actions in sequence:

1. Trigger when a customer submits the feedback form.
2. Save the feedback details into **Google Sheets**.
3. Send a personalized thank you email using **Gmail**.

---

## **Google Sheets Requirements**

Create a Google Sheet with the following columns:

* Customer Name
* Email
* Feedback
* Rating
* Submitted Time

Each new feedback entry should be stored as a new row in the sheet.

---

## **Email Requirements**

The thank you email must:

* Thank the customer for submitting their feedback.
* Mention the rating they provided.
* Appreciate their time and effort.
* Use a professional and friendly tone throughout.

---

## **Workflow Constraints**

* The workflow must begin with a **Form Trigger**.
* Use **Google Sheets** to store all feedback entries.
* Use **Gmail** to send the thank you email.
* Ensure all form fields are correctly mapped to the appropriate nodes.
* The workflow should execute automatically after each form submission.

---

## **Expected Workflow**

The completed workflow should follow this sequence:

```
Form Trigger
      ↓
Store Feedback (Google Sheets)
      ↓
Send Thank You Email (Gmail)
```

---

## **Deliverables**

Each student must submit the following:

1. Exported **n8n workflow (.json)**.
2. Screenshot of the completed workflow.
3. Screenshot of the Google Sheet showing stored feedback entries.
4. Screenshot of the thank you email received by the customer.
5. A brief document (150–200 words) explaining:
   * The workflow design.
   * The purpose of each node used.
   * Any challenges faced during implementation.

---

## **Evaluation Criteria**

| Criteria                          |         Marks |
| --------------------------------- | ------------: |
| Workflow functions correctly      |            30 |
| Correct use of required n8n nodes |            20 |
| Proper data mapping               |            20 |
| Google Sheets integration         |            10 |
| Email personalization             |            10 |
| Documentation and submission      |            10 |
| **Total**                         | **100 Marks** |

---

## **Submission Deadline**

**Recommended Completion Time:** 2 Hours

> **Note:** Students are expected to design and implement the workflow independently. Only the requirements are provided; the workflow logic, node configuration, and implementation details should be developed by the student.
