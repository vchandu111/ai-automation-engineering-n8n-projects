# **Project 3: Interview Registration & Notification Automation**

## **Objective**

Design and build an **n8n workflow** that automates the process of handling interview registrations. The workflow should confirm the registration with the candidate, notify the HR team, and store all candidate details in Google Sheets.

---

## **Learning Outcomes**

By completing this project, you should be able to:

* Use a Form Trigger as the entry point of a workflow.
* Send emails to multiple recipients using separate Gmail nodes.
* Store structured data in Google Sheets.
* Map form data correctly across multiple nodes.
* Build a multi-branch notification workflow in n8n.

---

## **Estimated Time**

**2 Hours 30 Minutes**

| Activity                       | Suggested Time |
| ------------------------------ | -------------- |
| Understanding the requirements | 15 minutes     |
| Designing the workflow         | 25 minutes     |
| Building the workflow          | 60 minutes     |
| Testing and debugging          | 30 minutes     |

---

## **Project Requirements**

You are required to build an automation workflow that performs the following tasks whenever a candidate submits an interview registration form.

### **Input Form Fields**

Your form must collect the following information:

* Candidate Name
* Email
* Role Applied For
* Interview Date

---

## **Workflow Requirements**

The workflow must perform the following actions in sequence:

1. Trigger when a candidate submits the registration form.
2. Send an **interview confirmation email** to the candidate using **Gmail**.
3. Send a **candidate details email** to the HR team using a separate **Gmail** node.
4. Store the candidate's information in **Google Sheets**.

---

## **Google Sheets Requirements**

Create a Google Sheet with the following columns:

* Candidate Name
* Email
* Role
* Interview Date
* Submission Time

Each new registration should be stored as a new row in the sheet.

---

## **Email Requirements**

### Candidate Confirmation Email

The email sent to the candidate must:

* Confirm that their interview has been successfully registered.
* Mention the role they applied for.
* Mention the scheduled interview date.
* Wish the candidate good luck.

### HR Notification Email

The email sent to HR must:

* Include the candidate's full name and email address.
* Mention the role the candidate applied for.
* Clearly state the interview date.
* Use a professional tone suitable for internal communication.

---

## **Workflow Constraints**

* The workflow must begin with a **Form Trigger**.
* Use **two separate Gmail nodes** — one for the candidate and one for HR.
* Use **Google Sheets** to store all registration details.
* Ensure all form fields are correctly mapped to each node.
* The workflow should execute automatically after each form submission.

---

## **Expected Workflow**

The completed workflow should follow this sequence:

```
Form Trigger
      ↓
Send Confirmation Email to Candidate (Gmail)
      ↓
Send Candidate Details Email to HR (Gmail)
      ↓
Store Candidate Data (Google Sheets)
```

---

## **Deliverables**

Each student must submit the following:

1. Exported **n8n workflow (.json)**.
2. Screenshot of the completed workflow.
3. Screenshot of the Google Sheet showing stored candidate details.
4. Screenshot of the confirmation email received by the candidate.
5. Screenshot of the notification email sent to HR.
6. A brief document (150–200 words) explaining:
   * The workflow design.
   * The purpose of each node used.
   * Any challenges faced during implementation.

---

## **Evaluation Criteria**

| Criteria                          |         Marks |
| --------------------------------- | ------------: |
| Workflow functions correctly      |            25 |
| Correct use of required n8n nodes |            20 |
| Proper data mapping               |            20 |
| Google Sheets integration         |            10 |
| Candidate email personalization   |            10 |
| HR email with correct details     |            05 |
| Documentation and submission      |            10 |
| **Total**                         | **100 Marks** |

---

## **Submission Deadline**

**Recommended Completion Time:** 2 Hours 30 Minutes

> **Note:** Students are expected to design and implement the workflow independently. Only the requirements are provided; the workflow logic, node configuration, and implementation details should be developed by the student.
