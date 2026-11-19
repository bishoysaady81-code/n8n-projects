# OMNA People – HR automation with n8n

An HR system that screens job applications with AI, answers employee policy questions from company documents, and coaches candidates on their CVs. The workflows run in n8n and the website talks to them directly.

**Live site:** https://bishoysaady81-code.github.io/n8n-projects/

The site works only while the author's computer, Docker, n8n and ngrok are running. When they are off, the status badge shows Offline.

## Workflows

| Workflow | Trigger | What it does |
|---|---|---|
| Recruitment 1 – Intake form | Form | Validates a PDF CV, saves it to Drive, logs the application in a sheet |
| Recruitment 2 – AI screening | Every hour | Scores new CVs with AI, emails invites or declines |
| Recruitment 3 – Error handler | Error + schedules | Logs failures, emails alerts, sends a daily digest, checks the queue |
| RAG – HR assistant | Chat | Answers only from the company policy documents |
| Policy loader | n8n start, daily, manual | Loads policy documents from Drive into the assistant's knowledge base |
| Job application coach | Form | Reads a CV against a job post and emails a coaching report |

## Services used

n8n (Docker), ngrok, GitHub Pages, Google Sheets, Google Drive, Gmail, Google Gemini (embeddings), OpenRouter (chat model).

## Import the workflows

1. In n8n, create a workflow, open the **…** menu and choose **Import from File**. Repeat for each file in `workflows/`.
2. Create your own credentials (Google OAuth2, Gemini, OpenRouter) and select them in every node with a warning triangle.
3. Replace every `YOUR_ID` with your own Sheet or Drive folder.
4. Set the error workflow to *Recruitment 3 – Error handler* in the other workflows' settings.
5. Use the same memory key and embeddings model in the RAG workflow and the Policy loader.
6. Publish the workflows and copy each trigger's Production URL into `CONFIG` in `index.html`.

No keys, IDs or email addresses are included in this repository.
