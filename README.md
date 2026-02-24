
# Agentic Email-to-Task Automation System

An AI-powered workflow that converts actionable emails into structured tasks inside Notion using an agentic architecture built in n8n.

This project demonstrates how large language models can be integrated with workflow orchestration tools to automate task creation from unstructured email inputs.

---

## Project Overview

Many work tasks originate from email conversations rather than task management systems. Manually converting emails into structured tasks is repetitive and error-prone.

This system automates that process by:

* Monitoring incoming emails in Gmail
* Classifying whether an email requires action
* Extracting structured task information using AI
* Validating the output through workflow logic
* Creating tasks automatically in a Notion database
* Preventing duplicate task entries

The goal is not just automation, but building an explainable agentic workflow with clear decision points.

---

## System Architecture

The workflow follows a layered structure:

### 1️⃣ Input Layer

* Gmail Trigger (new incoming emails)
* Email content extraction

### 2️⃣ AI Reasoning Layer

* Classification Agent
  Determines whether the email is:

  * Action required
  * FYI
  * Ignore

* Task Extraction Agent
  Extracts structured data:

  * Title
  * Description
  * Deadline (if provided explicitly)
  * Priority

### 3️⃣ Workflow Logic Layer

* JSON parsing and validation
* Conditional routing
* Duplicate detection against existing Notion tasks

### 4️⃣ Output Layer

* Task creation in Notion database

---

## End-to-End Workflow

1. A new email is received.
2. The system extracts the email body.
3. The classification agent determines if action is required.

   * If not → workflow ends.
4. If action is required → extraction agent generates structured task data.
5. The JSON output is parsed and validated.
6. The system checks for duplicate tasks in Notion.
7. If no duplicate exists → a new task is created.

---

## Tech Stack

* **n8n** – Workflow orchestration
* **Gmail Trigger Node** – Email ingestion
* **OpenAI API** – Classification and extraction
* **Notion API** – Task storage
* **JSON + Conditional Nodes** – Logic control

---

## Current Limitations

* Relative deadlines (e.g., “tomorrow”, “end of week”) are not consistently interpreted.
* The system processes one task per email.
* No conversation thread context awareness.
* No feedback loop for correcting incorrect classifications.

This project focuses on architecture and agentic workflow design rather than full production hardening.

---

## Use Cases

* Freelancers managing client requests
* Consultants handling multi-project email flows
* Project managers tracking actionable emails
* Knowledge workers with high inbox volume

---

## Setup Overview

1. Install and run n8n.
2. Import the provided workflow JSON file.
3. Configure credentials for:

   * Gmail
   * OpenAI
   * Notion
4. Activate the workflow.

Environment variables should be stored in a `.env` file (never committed), with a `.env.example` template included in the repository.

---

## Purpose of This Project

This project showcases:

* Agentic AI design patterns
* LLM + tool integration
* Deterministic workflow orchestration
* Guardrails for safe automation
* Practical AI application using no-code/low-code tools

It serves as a foundation that can be extended into a production-grade email-to-task automation system.

---

## Author

Syeda Sarah Mashhood
AI & Workflow Automation Projects

-