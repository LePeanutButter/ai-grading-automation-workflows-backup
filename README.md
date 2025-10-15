# AI Grading Automation Workflows Backup

[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

This repository contains the official backup of all **n8n workflows** used in the AI Grading Automation system for educators.  
These workflows orchestrate intelligent automation for academic grading and feedback, integrating **Google Workspace**, **LLMs (OpenAI/Gemini)**, and custom logic to streamline the evaluation process.

> This repository is not the full application — it is a version-controlled archive of the workflows that power it.

## Table of Contents

- [Background](#background)
- [Features](#features)
- [Architecture](#architecture)
- [Install](#install)
- [Usage](#usage)
- [Configuration](#configuration)
- [Data Flow](#data-flow)
- [License](#license)

## Background

University professors spend between **6 to 8 hours** per group grading assignments manually.  
This process is repetitive, time-consuming, and often inconsistent due to fatigue or lack of standardized rubrics.

The AI Grading Automation system solves this using **n8n** workflows to:

1. Assist in rubric creation with AI.
2. Grade student submissions automatically (.ipynb, PDF, DOCX).
3. Generate preliminary feedback for teacher approval.
4. Register results and send personalized feedback to students.

This repository ensures those workflows are safely backed up and versioned for recovery, auditing, and reuse.

## Features

The backed-up workflows include automation for:

- **AI-Assisted Rubric Generation** (OpenAI/Gemini)
- **Automated File Evaluation** (.ipynb, PDF, DOCX)
- **Feedback Delivery via Gmail/Outlook**
- **Grade Recording in Google Sheets**
- **Secure API & Credential Management**
- **Custom Error Handling and Logging**

Each workflow is stored as a `.json` file exported from n8n, ready to be re-imported into any compatible instance.

## Architecture

The system integrates the following components through n8n workflows:

- **n8n** – Automation orchestrator
- **Google Drive** – Submission storage
- **Google Sheets** – Grade logging
- **LLMs (OpenAI/Gemini)** – Evaluation and feedback generation
- **Email Services** – Feedback delivery
- **Rubric Repository** – Evaluation criteria

Workflow orchestration follows this pipeline:

```plaintext
Teacher → Google Drive → n8n → LLM → Google Sheets → Email → Student
```

## Install

### Prerequisites

To use the workflows in this backup:

- A running **n8n** instance (e.g. via Azure Web App for Containers)
- API credentials for:
  - Google Drive & Sheets
  - Gmail/Outlook
  - OpenAI or Gemini

### Setup

```bash
# Clone this backup repository
git clone https://github.com/LePeanutButter/ai-grading-automation-for-educators.git
cd ai-grading-automation-for-educators

# Import workflows into n8n
# (Use the n8n UI or CLI to import .json files from /workflows)
```

Environment variables should be configured via your hosting platform (e.g. Azure Portal).

## Usage

These workflows are designed to:

1. Detect new student submissions in **Google Drive**
2. Retrieve the appropriate rubric
3. Use **LLMs** to analyze and grade the work
4. Allow teachers to validate feedback
5. Send personalized results via email

You can customize or extend the workflows as needed once imported into your n8n instance.

## Configuration

All credentials and secrets should be managed securely using tools like environment variables.

## Data Flow

| Input                       | Process                            | Output                |
| --------------------------- | ---------------------------------- | --------------------- |
| Student Submissions (Drive) | Rubric Validation + LLM Evaluation | Grades in Sheets      |
| Rubric Repository           | AI Assistance                      | Validated Rubric      |
| Feedback Draft              | Teacher Approval                   | Email Sent to Student |

## License

[MIT](LICENSE) © 2025 Juan Camilo Rojas Ortiz, Luiggi Valencia Vélez, Santiago Botero García
