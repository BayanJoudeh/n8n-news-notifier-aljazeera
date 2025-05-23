# Aljazeera Feed Monitor - n8n Workflow

This repository contains a simple n8n workflow designed to monitor the Aljazeera English RSS feed and send email notifications whenever new items are published. It serves as a basic example of automation using n8n, focusing on free and readily available tools.

## Workflow Overview

The workflow performs the following steps:

1.  **Triggers periodically:** Uses a Schedule Trigger to run automatically at a configured interval (e.g., every hour).
2.  **Reads Aljazeera RSS Feed:** Fetches the latest items from the Aljazeera English main RSS feed URL.
3.  **Sends Email Notification:** For each new item found, it formats and sends an email containing the title, link, and content snippet.

![Workflow Screenshot]![Aljazeera Feed Monitor Workflow](https://github.com/user-attachments/assets/dc1b1c52-5f86-40c1-aca8-94e04654a69a)


*(Image: Aljazeera Feed Monitor Workflow.png shows the visual layout of the n8n workflow)*

## Features

*   **Automated Monitoring:** Runs automatically on a schedule.
*   **Focused:** Specifically monitors the Aljazeera English feed (but can be adapted).
*   **Free to Run:** Utilizes n8n's core nodes and relies on free services (RSS feeds, free tiers of SMTP providers like SendGrid, Brevo, Mailgun, or Gmail with App Passwords).
*   **Simple Setup:** Requires minimal configuration after importing.

## Prerequisites

*   An active n8n instance. This can be:
    *   [n8n Cloud](https://n8n.cloud/) (offers a free tier with usage limits)
    *   A self-hosted n8n instance (completely free, requires your own server or computer). See [n8n installation docs](https://docs.n8n.io/hosting/installation/).
*   SMTP Credentials for sending email (e.g., from SendGrid, Brevo, Mailgun, or a Gmail App Password).

## How to Use

1.  **Download:** Download the `Aljazeera_Feed_Monitor.json` file from this repository.
2.  **Import:** Open your n8n instance, go to "Workflows", click the "Import from File" button, and select the downloaded `Aljazeera_Feed_Monitor.json` file.
3.  **Configure:** After importing, you need to configure a few nodes:
    *   **Schedule Trigger (Configure Time):** Click on this node and set the desired schedule (e.g., every hour, every day at a specific time).
    *   **RSS Feed Read (Configure URL):** This node is pre-configured with the Aljazeera English feed URL (`https://www.aljazeera.com/xml/rss/all.xml`). You can change it here if needed.
    *   **Send Email (Configure Credentials & Recipient):**
        *   Click on this node.
        *   **Credentials:** Select your pre-configured SMTP credential from the dropdown list. If you haven't configured one yet, go to "Credentials" in the n8n sidebar, click "Add Credential", select "SMTP", and enter the details (Host, Port, User, Password/API Key) from your email provider (SendGrid, Brevo, Gmail App Password, etc.). Remember to use the correct Port and SSL/TLS settings (e.g., Port 587 usually needs SSL/TLS OFF, Port 465 usually needs SSL/TLS ON).
        *   **To Email:** Replace `YOUR_EMAIL_ADDRESS_HERE` (or the value in the workflow parameters) with the email address where you want to receive the notifications.
        *   *(Optional)* Modify the Subject and Text/HTML fields if you want to change the email format. The defaults use expressions like `{{$json.title}}`, `{{$json.link}}`, and `{{$json.contentSnippet}}` to pull data from the RSS feed.
4.  **Save & Activate:** Save the workflow and toggle the "Active" switch to ON.

Your workflow will now run automatically according to the schedule you set, sending you Aljazeera news updates!

## Note on n8n Cloud Trials

This workflow is shared as a JSON file. You import it into *your own* n8n instance (Cloud or Self-Hosted). The functionality does not depend on the original creator's n8n account status. You can use this workflow on the n8n Cloud free tier or a self-hosted instance indefinitely, subject only to the limitations of your chosen n8n plan or hosting resources.
