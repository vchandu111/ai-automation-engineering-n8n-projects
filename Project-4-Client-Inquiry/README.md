# **Project 4: Client Inquiry Management Automation**

## **Objective**

Design and build an **n8n workflow** that automates the process of managing client inquiries. The workflow should store client details, send a confirmation email to the client, add the client to Google Contacts, and notify you when a new inquiry is received.

---

## **Learning Outcomes**

By completing this project, you should be able to:

* Use a Form Trigger as the entry point of a workflow.
* Store client data in Google Sheets.
* Send automated personalized emails using Gmail.
* Add contacts to Google Contacts from a workflow.
* Send internal notification emails using a second Gmail node.
* Build a multi-step, multi-node automation workflow.

---

## **Estimated Time**

**3 Hours**

| Activity                       | Suggested Time |
| ------------------------------ | -------------- |
| Understanding the requirements | 15 minutes     |
| Designing the workflow         | 25 minutes     |
| Building the workflow          | 80 minutes     |
| Testing and debugging          | 40 minutes     |

---

## **Project Requirements**

You are required to build an automation workflow that performs the following tasks whenever a client submits an inquiry form.

### **Input Form Fields**

Your form must collect the following information:

* Name
* Email
* Phone Number
* Description (of their inquiry or requirement)

---

## **Workflow Requirements**

The workflow must perform the following actions in sequence:

1. Trigger when a client submits the inquiry form.
2. Store the client's details in **Google Sheets**.
3. Send a **thank you confirmation email** to the client using **Gmail**.
4. Add the client as a contact in **Google Contacts**.
5. Send a **notification email to yourself** using a second **Gmail** node.

---

## **Google Sheets Requirements**

Create a Google Sheet with the following columns:

* Name
* Email
* Phone Number
* Description

Each new client inquiry should be stored as a new row in the sheet.

---

## **Email Requirements**

### Client Thank You Email

The email sent to the client must:

* Address the client by name.
* Thank them for reaching out.
* Inform them that their inquiry has been received and that you will follow up shortly.
* Use a warm and professional tone.

Example message:

> Hello [Name], thank you for contacting us. We have received your inquiry and will share more details with you shortly.

### Internal Notification Email (to Yourself)

The email sent to yourself must:

* Include the client's name.
* Include the client's email address.
* Include the client's description or inquiry details.
* Serve as an alert that a new client request has been submitted.

---

## **Workflow Constraints**

* The workflow must begin with a **Form Trigger**.
* Use **Google Sheets** to store client details.
* Use **Gmail** to send the client thank you email.
* Use **Google Contacts** to add the client as a contact.
* Use a **second Gmail node** to send yourself a notification.
* Ensure all fields are correctly mapped across all nodes.
* The workflow should execute automatically after each form submission.

---

## **Expected Workflow**

The completed workflow should follow this sequence:

```
Form Trigger
      ↓
Store Client Details (Google Sheets)
      ↓
Send Thank You Email to Client (Gmail)
      ↓
Add Client to Google Contacts
      ↓
Send Notification Email to Yourself (Gmail)
```

---

## **Deliverables**

Each student must submit the following:

1. Exported **n8n workflow (.json)**.
2. Screenshot of the completed workflow.
3. Screenshot of the Google Sheet showing stored client details.
4. Screenshot of the thank you email received by the client.
5. Screenshot of the created Google Contact.
6. Screenshot of the notification email received by you.
7. A brief document (150–200 words) explaining:
   * The workflow design.
   * The purpose of each node used.
   * Any challenges faced during implementation.

---

## **Evaluation Criteria**

| Criteria                            |         Marks |
| ----------------------------------- | ------------: |
| Workflow functions correctly        |            25 |
| Correct use of required n8n nodes   |            20 |
| Proper data mapping                 |            15 |
| Google Sheets integration           |            10 |
| Client email personalization        |            10 |
| Google Contacts integration         |            10 |
| Internal notification email         |            05 |
| Documentation and submission        |            05 |
| **Total**                           | **100 Marks** |

---

## **Submission Deadline**

**Recommended Completion Time:** 3 Hours

> **Note:** Students are expected to design and implement the workflow independently. Only the requirements are provided; the workflow logic, node configuration, and implementation details should be developed by the student.
