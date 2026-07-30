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
```
---

## Configuration & Setup

* **Trigger App:** Gmail (`New Email` / `New Dispute Email`)
* **Core Logic:** AI by Zapier (`Predict Response` / `Run Prompt`)
* **Primary System Prompt:**
  > "You are an AI Claims Assistant. Review the incoming claim dispute email body from Gmail.
  > 1. Classify the complexity level into one of three categories: Routine, Moderate, or High-Risk Litigation.
  > 2. Summarize the key facts of the dispute in 2–3 sentences.
  > 3. Recommend clear next steps for the handling team based on standard claim guidelines."

* **Database Target:** Airtable (`Claim Disputes & Risk Intake Base`)
  * **Logged Fields:** `Claim ID`, `Sender Email`, `Dispute Summary`, `Complexity Tier` (`Routine` | `Moderate` | `High-Risk Litigation`), `Recommended Next Steps`, `Status`
  * **Workflow Role:** Acts as the primary system of record, storing structured dispute data and evaluation outputs from the AI Agent step for historical tracking and audit logs.

---

## Technical Reflection & Analysis

### Zap vs. Agent Comparison
* **Deterministic vs. Non-Deterministic:** Standard Zaps execute fixed field-mapping pipelines without decision-making. AI Agents evaluate unstructured text, interpret intent, and dynamically apply rules based on context.
* **Production Considerations:** Publishing for live production requires re-authenticating Slack channels for real-time `#claims-alerts` routing and mapping exact sheet columns (e.g., matching dispute type fields instead of default project templates).
