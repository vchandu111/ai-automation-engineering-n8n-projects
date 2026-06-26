# **Project 7: Automated Daily AI News Digest**

## **Objective**

Design and build an **n8n workflow** that automatically generates and delivers a daily AI news digest. The workflow should collect relevant AI news, summarize it using a language model, save the digest to Google Docs, and send it to subscribers via Gmail — all on a scheduled basis.

---

## **Learning Outcomes**

By completing this project, you should be able to:

* Use the Schedule Trigger node to run a workflow automatically at a set time.
* Collect and pass news content to an AI model using the Basic LLM Chain node.
* Generate structured summaries and highlights using AI.
* Save AI-generated content to Google Docs.
* Send scheduled digest emails using Gmail.
* Build a fully automated, scheduled AI-driven workflow in n8n.

---

## **Estimated Time**

**3 Hours 30 Minutes**

| Activity                       | Suggested Time |
| ------------------------------ | -------------- |
| Understanding the requirements | 20 minutes     |
| Designing the workflow         | 30 minutes     |
| Building the workflow          | 90 minutes     |
| Testing and debugging          | 30 minutes     |

---

## **Project Requirements**

You are required to build a scheduled automation workflow that generates and distributes a daily AI news digest without any manual input.

### **Trigger**

The workflow must run automatically every morning using the **Schedule Trigger** node. You may choose the time (e.g., 8:00 AM daily).

---

## **Workflow Requirements**

The workflow must perform the following actions in sequence:

1. **Trigger automatically** every morning using the **Schedule Trigger** node.
2. **Collect AI news content** — you may use an RSS Feed node, HTTP Request node, or provide curated sample news text as a starting point.
3. **Send the news content** to the **Basic LLM Chain** node for AI processing.
4. The AI must generate:
   * Short summaries of each article or topic.
   * Key highlights from the day's AI news.
   * A list of trending AI topics.
   * Key takeaways for the reader.
5. **Save the final digest** to **Google Docs**.
6. **Send the digest** to subscribers using **Gmail**.

---

## **Google Docs Requirements**

The Google Doc created or updated each day must contain the following clearly labeled sections:

* Date
* Top AI News
* Article Summaries
* Trending Topics
* Key Takeaways

The content of each section should be populated using the AI-generated output.

---

## **Email Requirements**

The daily digest email sent to subscribers must:

* Include the AI-generated news summary.
* Keep the content concise and easy to read.
* Highlight the top trending AI topics.
* End with a friendly and engaging sign-off.

---

## **AI Prompt Guidelines**

When configuring the **Basic LLM Chain** node, your prompt should instruct the AI to:

* Read and analyze the provided news content.
* Write a short summary for each article or topic.
* Identify and list the top trending AI topics of the day.
* Generate key takeaways that a reader would find valuable.
* Keep the language clear, concise, and engaging.

You are responsible for writing an effective prompt that produces a clean, readable digest suitable for a daily email.

---

## **Workflow Constraints**

* The workflow must begin with a **Schedule Trigger** node set to run daily.
* Use the **Basic LLM Chain** node to process and summarize news content.
* Use **Google Docs** to save the generated digest.
* Use **Gmail** to send the digest to subscribers.
* The workflow must run fully automatically without any manual intervention.
* Ensure the AI output is correctly mapped into the Google Doc and email body.

---

## **Expected Workflow**

The completed workflow should follow this sequence:

```
Schedule Trigger (Every Morning)
      ↓
Collect AI News Content (RSS / HTTP Request / Sample Input)
      ↓
Summarize & Analyze with Basic LLM Chain (AI)
      ↓
Save Digest to Google Docs
      ↓
Send Digest Email to Subscribers (Gmail)
```

---

## **Deliverables**

Each student must submit the following:

1. Exported **n8n workflow (.json)**.
2. Screenshot of the completed workflow.
3. Screenshot of the Schedule Trigger configuration.
4. Screenshot of the generated Google Doc with all required sections.
5. Screenshot of the digest email sent to subscribers.
6. Screenshot of the AI prompt configured in the Basic LLM Chain node.
7. A brief document (150–200 words) explaining:
   * The workflow design.
   * How news content is collected and passed to the AI.
   * The purpose of each node used.
   * Any challenges faced during implementation.

---

## **Evaluation Criteria**

| Criteria                              |         Marks |
| ------------------------------------- | ------------: |
| Workflow triggers on schedule         |            15 |
| AI output quality and structure       |            25 |
| Google Docs integration               |            15 |
| Correct use of required n8n nodes     |            15 |
| Email digest quality and readability  |            10 |
| AI prompt quality                     |            10 |
| Documentation and submission          |            10 |
| **Total**                             | **100 Marks** |

---

## **Submission Deadline**

**Recommended Completion Time:** 3 Hours 30 Minutes

> **Note:** Students are expected to design and implement the workflow independently. Only the requirements are provided; the workflow logic, node configuration, AI prompt design, news collection method, and implementation details should be developed by the student.
