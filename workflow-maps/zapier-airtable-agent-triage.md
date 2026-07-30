# Zapier Agent: Insurance Claim Triage & Risk Classification

## Project Overview
This project demonstrates the configuration of an autonomous AI Agent built in Zapier Copilot designed to handle non-deterministic claim intake workflows. Unlike linear Zaps, this Agent applies judgment, text analysis, and risk evaluation to incoming claim dispute emails.

---

## Workflow Architecture

```text
[Gmail Trigger: New Dispute Email]
       │
       ▼
[AI Agent / AI by Zapier: Risk Reasoning & Evaluation]
       ├── Classifies Risk: Routine | Moderate | High-Risk Litigation
       ├── Summarizes Case: 2–3 Sentence Core Summary
       └── Formulates Plan: Recommended Action Steps
       │
       ▼
[Airtable & Output Notification: Slack / Email Alert]
