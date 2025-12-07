# AI Grading Automation Workflows Backup

[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

A standard-compliant README for the **AI Grading Automation System**, a multi-agent, human-in-the-loop hyperautomation solution designed for educational institutions.

This repository contains the **version-controlled backup** of all **n8n automation workflows** that power the AI-enabled grading system used by university instructors. These workflows orchestrate a full evaluation pipeline integrating **multi-agent reasoning**, **Google Workspace**, **Gemini/GPT**, **Supabase**, and advanced **hyperautomation lifecycle (HAL)** patterns.

The system dramatically reduces grading time, standardizes evaluation criteria, and augments the instructor with intelligent, auditable decision support.

## Table of Contents

- [Background](#background)
- [Install](#install)
- [Usage](#usage)
- [Architecture & Multi-Agent System](#architecture--multi-agent-system)

  - [Human-in-the-Loop (HITL)](#human-in-the-loop-hitl)
  - [Agent Memory](#agent-memory)
  - [Hyperautomation Lifecycle (HAL)](#hyperautomation-lifecycle-hal)

- [Security](#security)
- [Business Model: B2B and B2C Strategy](#business-model-b2b-and-b2c-strategy)
- [Contributors](#contributors)
- [License](#license)

## Background

University instructors spend **6 to 8 hours** manually grading a single group of assignments. This produces:

- Delayed feedback cycles
- Inconsistent scoring due to fatigue
- Lack of standardized rubrics
- Limited visibility and traceability
- High operational burden

The AI Grading Automation System solves this by implementing a **multi-agent orchestration layer** that automatically:

1. Generates rubrics using pedagogical agents
2. Classifies and preprocesses student deliverables
3. Executes LLM-based evaluations
4. Produces personalized feedback
5. Logs grades automatically
6. Routes results for human approval before delivery

This repository preserves all the **n8n workflows** that enable the system.

## Install

To run these workflows, you need:

- A deployed **n8n instance** (Docker, cloud container, or SaaS)
- API credentials for:

  - Google Drive / Google Sheets
  - Gmail or Outlook
  - Gemini or GPT
  - Supabase

Clone this backup repository:

```sh
git clone https://github.com/LePeanutButter/ai-grading-automation-workflows-backup.git
cd ai-grading-automation-workflows-backup
```

Import the JSON workflows through the n8n UI.

## Usage

This repository is strictly a **workflow backup**, ready to be imported into any n8n instance.
Once imported, the automations will:

1. Detect new assignments in Google Drive
2. Retrieve or generate the appropriate rubric
3. Preprocess and analyze the content
4. Evaluate with LLMs through agentic workflows
5. Request human approval (HITL)
6. Email personalized feedback
7. Log results in Google Sheets

## Architecture & Multi-Agent System

The system implements a **distributed multi-agent architecture** on top of n8n, where each workflow component embodies a functional agent with a defined responsibility.

### Core Agents

| Agent                         | Responsibility                                                     |
| ----------------------------- | ------------------------------------------------------------------ |
| **Rubric Agent**              | Generates and adapts rubrics using LLMs and pedagogical frameworks |
| **Evaluation Agent**          | Analyzes submissions and produces scoring + personalized feedback  |
| **Document Agent**            | Handles preprocessing: OCR, parsing, format validation             |
| **Memory Agent**              | Stores rubric history, instructor preferences, course context      |
| **Compliance Agent**          | Enforces security, anonymization, and audit requirements           |
| **Feedback Delivery Agent**   | Sends personalized emails to students                              |
| **Instructor Approval Agent** | Manages HITL checkpoints                                           |

This multi-agent structure supports scalability, modularity, and clear separation of responsibilities, aligning with modern agentic design best practices.

### Human-in-the-Loop (HITL)

The system is intentionally **not fully autonomous**. It embeds a strict HITL safeguard:

- Every AI-generated evaluation must be **reviewed, corrected, or approved** by the instructor.
- Feedback is only delivered after explicit human confirmation.
- All HITL interventions are logged for **audit, version control, and fairness guarantees**.

This creates a hybrid workflow that enhances instructor productivity while maintaining academic integrity.

### Agent Memory

The system includes a **memory layer** managed through Supabase and internal n8n storage:

- Saves rubric versions
- Tracks instructor preferences
- Stores historical submissions
- Maintains course-level context
- Logs evaluation patterns for consistency

This memory enables more consistent evaluations and reduces repetitive tasks across assignments, semesters, and courses.

### Hyperautomation Lifecycle (HAL)

The system implements the **Hyperautomation Lifecycle (HAL)** end-to-end:

1. **Discover:** Identify bottlenecks: grading, rubric creation, feedback delays.
2. **Analyze:** Process breakdown, stakeholder interviews, latency assessment.
3. **Design:** Multi-agent architecture + rubric generation model + HITL checkpoints.
4. **Automate:** n8n workflows, LLM pipelines, and automatic data routing.
5. **Orchestrate:** Cross-service coordination via Google Workspace, Supabase, email pipelines.

6. **Optimize:** Metrics dashboards (Grafana), accuracy tuning, cost reduction.
7. **Govern:** Audit logs, access control, security policies, compliance oversight.

This positions the solution as a **full hyperautomation platform**, not just an LLM tool.

## Security

Security was a first-class requirement throughout the system design.

### Credential Security

- All secrets stored via **n8n Credential Manager**, encrypted at rest.
- No credentials embedded in workflows.

### Data Protection

- Deliverables are **anonymized** before LLM processing.
- Sensitive metadata is redacted.

### Transport Security

- All communications use TLS:

  - n8n -> Google APIs
  - n8n -> Email services
  - n8n -> Supabase

### Access Control

- Instructors authenticate through secure channels.
- Only authorized users can approve or release feedback.

### Auditability

- Every evaluation, modification, decision, and data access is logged:

  - Timestamp
  - Instructor identity
  - AI evaluation
  - Final feedback

This aligns with institutional requirements for educational data protection.

## Business Model: B2B and B2C Strategy

The automation system supports two commercialization strategies:

### **B2C (Direct-to-Teacher)**

Individual instructors can purchase grading automation as a service.

- Fast onboarding
- Low cost per workflow
- Individual academic use
- Immediate ROI (pays for itself after grading one group)

### **B2B (Institutional Licensing)**

Universities can integrate the system at scale.

- Multi-course and multi-semester deployments
- Centralized dashboards for academic analytics
- Integration with LMS systems (Canvas, Moodle, Blackboard)
- Governance + audit layers for administrative oversight
- Volume-based pricing

The combination of agent automation, HAL governance, and data security strengthens the B2B value proposition and makes the solution scalable at institutional levels.

## Contributors

- [Jcro15](https://github.com/Jcro15) - Juan Camilo Rojas Ortiz
- [lrvalencia](https://www.linkedin.com/in/lrvalencia/) - Luiggi Valencia Vélez
- [LePeanutButter](https://github.com/LePeanutButter) - Santiago Botero

## License

[MIT](LICENSE) © Juan Camilo Rojas Ortiz, Luiggi Valencia Vélez, Santiago Botero García

---

This **README** follows the Standard Readme specification.
