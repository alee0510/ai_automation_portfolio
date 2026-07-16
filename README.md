# AI Automation & n8n Workflow Portfolio

Welcome to my AI Automation portfolio! This repository showcases production-ready, event-driven workflow automation pipelines developed using **n8n**, **Google Gemini AI**, and **PostgreSQL (PGVector)**. These workflows solve complex business challenges including automated social content pipelines, intelligent recruitment/resume screening systems, dynamic RAG pipelines, and automated error logging infrastructure.

---

## 📂 Project Structure

*   **[`workflows/`](/workflows/)**: Contains raw n8n workflow export JSON files ready to import.
*   **[`documents/`](/documents/)**: Detailed case studies, business problems, architectures, and impacts of each workflow.
*   **[`screenshots/`](/screenshots/)**: Visual representations and logs of execution runs.

---
## ⚡ Core Workflows

### 1. [AI Resume Screener & Recruiter Automation](/documents/ai_resume_screener.md)
*   **Workflow JSON**: [`AI Resume Screener & Recruiter Automation.json`](/workflows/AI%20Resume%20Screener%20&%20Recruiter%20Automation.json)
*   **Problem**: Recruiting teams spend excessive hours manually vetting resumes, matching candidate profiles to multiple job specifications, and coordinating interviews.
*   **Solution**: An intelligent end-to-end recruitment pipeline that listens for Gmail applications, parses resume attachments (PDF/DOCX), performs a Retrieval-Augmented Generation (RAG) semantic match against current JDs, evaluates candidates via Google Gemini (assigning match & confidence scores), and automatically drafts interview invitations (with Calendly links) or routes low-confidence files for human review.
*   **Key Tech Stack**: n8n, Google Gemini (LLM), PostgreSQL + PGVector, Gmail & Google Drive APIs, Calendly, Slack notifications.

### 2. [AI Content Engine & Social Publishing Automation](/documents/ai_content_engine.md)
*   **Workflow JSON**: [`Automate Content Generator - v2.json`](/workflows/Automate%20Content%20Generator%20-%20v2.json)
*   **Screenshot**: [`ai_content_generation.png`](/screenshots/ai_content_generation.png)
*   **Problem**: Content generation and posting across multiple marketing platforms (LinkedIn, Instagram, etc.) was manual, time-consuming (8+ hours/week), and highly repetitive.
*   **Solution**: A scheduled, Sheets-driven pipeline that checks for campaign ideas, generates highly targeted copy for LinkedIn/Instagram via Gemini, creates AI images, uploads media assets to Cloudinary, and automatically publishes them to social platforms, logging final published URLs and execution states.
*   **Key Tech Stack**: n8n, Gemini AI, Google Sheets API, Cloudinary API, LinkedIn API, Instagram Graph API.

### 3. [Dynamic RAG Pipeline & Vector DB Sync](/documents/dynamic_rag_pipeline.md)
*   **Workflow JSON**: [`RAG Operation Best Practice.json`](/workflows/Dynamic%20RAG%20Pipeline.json)
*   **Problem**: Stale vector databases yield outdated info and hallucinations when documents are updated or deleted from cloud storage.
*   **Solution**: An event-driven synchronization system that automatically tracks file creation, changes, and deletions in Google Drive, handles chunking and embedding generation with Gemini Embeddings, performs transactional upserts, and clears deleted records in a PostgreSQL + PGVector database.
*   **Key Tech Stack**: n8n, PostgreSQL, PGVector, Google Gemini Embeddings, Google Drive API.

---

## 🛠️ Shared Infrastructure & Utilities

### [Centralized Error Logger](/workflows/Error%20Logger.json)
*   **Workflow JSON**: [`Error Logger.json`](/workflows/Error%20Logger.json)
*   **Purpose**: A robust, reusable sub-workflow designed to streamline monitoring across the entire automation suite. Whenever a step in a primary workflow triggers an error, this sub-workflow catches it, extracts execution metadata, logs it to a PostgreSQL database table (`workflow_logs`), and fires off notifications to alert administrators.
*   **Data Captured**: `workflow_id`, `execution_id`, `log_level`, `error_type`, `message`, `context` (JSON block).

---

## 🚀 Key Technologies & Integrations
*   **Automation Platform**: [n8n](https://n8n.io/)
*   **Artificial Intelligence**: Google Gemini (Pro, Flash, and Text Embeddings)
*   **Database & Storage**: PostgreSQL (Relational) & [PGVector](https://github.com/pgvector/pgvector) (Vector database search), [Cloudinary](https://cloudinary.com/) (Asset Cloud Storage)
*   **APIs & Integrations**: Google Workspace (Sheets, Drive, Gmail), Slack, Calendly, LinkedIn API, Instagram Graph API

---

## ⚙️ How to Import and Use These Workflows
1. Install and run **n8n** (Self-hosted or Cloud).
2. Set up your credentials for:
   - PostgreSQL / PGVector database.
   - Google Workspace / Gemini API keys.
   - Social Media API clients (LinkedIn, Cloudinary, Instagram Graph API).
3. In your n8n canvas, click the menu button -> **Import from File...** and choose one of the `.json` files from the [`workflows/`](/workflows/) directory.
4. Adjust the variables and node inputs to point to your specific databases and sheets.
