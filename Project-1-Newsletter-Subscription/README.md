# **Project 1: Newsletter Subscription Automation**

## **Objective**

Design and build an **n8n workflow** that automates the process of handling newsletter subscriptions. The workflow should collect subscriber information, communicate with the subscriber, and maintain records using Google services.

---

## **Learning Outcomes**

By completing this project, you should be able to:

* Create a workflow using n8n.
* Use a Form Trigger as the workflow entry point.
* Integrate Google Contacts, Gmail, and Google Sheets.
* Map data between multiple nodes.
* Build a complete end-to-end automation workflow.

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

You are required to build an automation workflow that performs the following tasks whenever a user submits a newsletter subscription form.

### **Input Form Fields**

Your form must collect the following information:

* Name
* Email
* Interested Topic

---

## **Workflow Requirements**

The workflow must perform the following actions in sequence:

1. Trigger when a user submits the form.
2. Create a new contact using **Google Contacts**.
3. Send a personalized welcome email using **Gmail**.
4. Store the subscriber's information in **Google Sheets**.

---

## **Google Sheets Requirements**

Create a Google Sheet with the following columns:

* Name
* Email
* Interested Topic
* Signup Date

Each new subscriber should be stored as a new row in the sheet.

---

## **Email Requirements**

The welcome email must:

* Greet the subscriber using their name.
* Thank them for subscribing to the newsletter.
* Mention the topic they selected during registration.
* End with a friendly closing message.

---

## **Workflow Constraints**

* The workflow must begin with a **Form Trigger**.
* Use **Google Contacts** to create the contact.
* Use **Gmail** to send the welcome email.
* Use **Google Sheets** to store subscriber information.
* Ensure all fields are correctly mapped between nodes.
* The workflow should execute automatically after each form submission.

---

## **Expected Workflow**

The completed workflow should follow this sequence:

```
Form Trigger
      ↓
Create Contact (Google Contacts)
      ↓
Send Welcome Email (Gmail)
      ↓
Store Subscriber Details (Google Sheets)
```

---

## **Deliverables**

Each student must submit the following:

1. Exported **n8n workflow (.json)**.
2. Screenshot of the completed workflow.
3. Screenshot of the Google Sheet showing stored subscriber details.
4. Screenshot of the created Google Contact.
5. Screenshot of the welcome email received.
6. A brief document (150–200 words) explaining:
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
