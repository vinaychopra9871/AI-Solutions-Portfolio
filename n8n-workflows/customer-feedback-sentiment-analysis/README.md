# AI Powered Customer Feedback Sentiment Analysis Automation

## Overview

An end-to-end AI automation workflow built using n8n that analyzes customer feedback submitted through Google Forms.

The workflow classifies feedback sentiment using the Hugging Face Inference API, updates Google Sheets with sentiment labels and confidence scores, and automatically sends HTML email alerts whenever negative feedback is detected.

---

## Features

- Google Forms integration
- Automatic sentiment analysis
- Confidence score generation
- Google Sheets update
- Negative feedback detection
- HTML email alerts
- Real-time workflow automation

---

## Workflow

```mermaid
flowchart TD
    A[Google Form Submission]
    B[Google Sheets Trigger]
    C[Hugging Face Sentiment Analysis]
    D[Update Google Sheet]
    E{Negative Feedback?}
    F[End]
    G[Read Google Sheet]
    H[Generate Summary]
    I[Send HTML Email Alert]

    A --> B
    B --> C
    C --> D
    D --> E
    E -- No --> F
    E -- Yes --> G
    G --> H
    H --> I
```
---

## Technologies

- n8n
- Hugging Face Inference API
- Google Sheets API
- Gmail
- JavaScript
- REST API

---
## Import Workflow

### Prerequisites

Before importing the workflow, ensure you have:

- An active n8n instance
- A Google account
- A Hugging Face account with an Inference API key
- A Gmail account for sending notifications

---

### Setup Instructions

1. Download `customer-feedback-sentiment-analysis.json`.

2. Import the workflow into n8n:
   - Open **n8n**
   - Click **Import from File**
   - Select the downloaded workflow JSON

3. Configure the required credentials:
   - Google Sheets OAuth2
   - Google Sheets Trigger OAuth2
   - Gmail OAuth2

4. Create a Google Form linked to a Google Sheet with the following columns:

   - Timestamp
   - Customer Name
   - Email Address
   - Please share your feedback
   - Sentiment
   - Confidence

5. Update the workflow configuration:
   - Select your Google Spreadsheet in both Google Sheets nodes.
   - Select the correct worksheet.
   - Replace the placeholder below with your own Hugging Face API key:

   ```
   Authorization: Bearer YOUR_HUGGINGFACE_API_KEY
   ```

6. Update the Gmail node:
   - Replace `your_email@gmail.com` with the email address where you want to receive alerts.

7. Save and activate the workflow.

---

### Workflow Trigger

Whenever a new response is submitted through the Google Form:

- The workflow is triggered automatically.
- Customer feedback is analyzed using Hugging Face's multilingual sentiment analysis model.
- The sentiment and confidence score are written back to Google Sheets.
- If the feedback is classified as **Negative**, an HTML email alert is sent containing:
  - Latest customer feedback
  - Sentiment
  - Confidence score
  - Overall feedback summary (Positive, Neutral, Negative, Total)

---

### Notes

- API keys and credentials are **not included** in this repository.
- Replace all placeholder values with your own credentials before running the workflow.
- The Google Sheet used in this repository is for demonstration purposes. You can replace it with your own sheet after importing the workflow.

---
## Improvements which can be incorporated

- Power BI Dashboard
- Slack Notifications
- Microsoft Teams Alerts
- Trend Analysis
- Weekly Reports
- AI-generated Feedback Summaries
