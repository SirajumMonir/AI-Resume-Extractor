<img width="1904" height="760" alt="Screenshot 2026-04-09 092255" src="https://github.com/user-attachments/assets/e37c9f99-8cfd-4508-bd4c-dfe0797debb9" />
# 📄 AI-Powered Resume Data Extractor (PDF to Airtable ATS)

An advanced data engineering workflow built in n8n that leverages Large Language Models (LLMs) to parse unstructured PDF files (Resumes/CVs) and automatically convert them into clean, structured records in an Airtable database.

## 🚀 The Problem it Solves
Recruiters and HR teams spend countless hours manually opening PDF files, reading CVs, and copy-pasting data into spreadsheets. This workflow automates that entire data-entry process. It provides a front-end web form for direct file uploads, extracts the raw binary text, processes it through an AI, and pushes the structured data directly into a CRM/ATS.

## 🛠️ Tech Stack & Architecture
* **Workflow Engine:** n8n (Localhost via ngrok)
* **Frontend UI:** n8n Form Trigger (File upload portal)
* **Data Parser:** n8n `Extract From File` Node (PDF Binary-to-Text)
* **AI/LLM:** Meta Llama 3 (via Groq API)
* **Database:** Airtable (Acts as the Applicant Tracking System)

## 💡 How It Works
1. **File Ingestion:** The user visits a secure web link hosted by the `n8n Form Trigger` and uploads their Resume in `.pdf` format.
2. **Binary Extraction:** The binary payload is passed to the `Extract From File` node, which strips away the PDF formatting and outputs the raw text.
3. **AI Entity Extraction:** The Groq API (Llama 3) processes the raw text using a strict system prompt. It identifies the candidate's core details (`Name`, `Email`, `Phone`, `LinkedIn`, `GitHub`).
4. **JSON Structuring:** The LLM is forced to output a perfectly formatted JSON object.
5. **Database Sync:** The structured JSON is instantly mapped and pushed via API to an Airtable Base, creating a new candidate record.

## 💻 Setup Instructions
1. Initialize n8n locally (`npx n8n`).
2. Import the provided workflow JSON file into your n8n instance.
3. Obtain your Groq API Key and add it to the `Basic LLM Chain` credentials.
4. Obtain an Airtable Personal Access Token (ensure `data.records:write` and `schema.bases:read` scopes are enabled).
5. Map the AI output variables to your Airtable columns.
6. Activate the workflow, open the Form URL, and upload a test PDF to see the magic happen!

---
*Built as a portfolio project to demonstrate UI creation, Binary Data Processing, Unstructured Data Parsing, and API Integration for AI Automation Engineering roles.*
