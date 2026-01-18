# B2B Sales Automation

![Status](https://img.shields.io/badge/Status-Production_Ready-success)
![ROI](https://img.shields.io/badge/ROI-€3.250/year-brightgreen)
![Cost](https://img.shields.io/badge/Build_Cost-$3.46-blue)

## TL;DR

**Problem:** Sales reps spend only 28% of their time selling – the rest goes to admin tasks.
**Solution:** Hybrid AI – deterministic workflows for reports, probabilistic assistant for analysis.
**Result:** 2.5h/week saved, 938× ROI.

[📊 Demo](#what-i-built) • [🔍 Development Story](./docs/JOURNEY.md) • [⚖️ Tool Comparison](./docs/TOOL-COMPARISON.md)

---

## My Solution: Hybrid Architecture

| Use Case | Architecture | Why? |
|----------|--------------|------|
| Weekly Reports | **Deterministic** (Workflow) | Identical format, auditable, no hallucinations |
| Ad-hoc Analysis | **Probabilistic** (Assistant) | Flexible interpretation, context-dependent |

```
Accounts (WHO)   +   Invoices (HOW)   +   Tickets (HAPPY?)
                         ↓
            Priority Score: Top 3 accounts this week
```

---

## What I Built

### Workflow: Weekly Sales Report

Every Monday 9:00 AM. Identical output for identical data.

```mermaid
flowchart LR
    Trigger((Mon 9:00)) --> FileA[📄 accounts.csv]
    Trigger --> FileB[📄 invoices.csv]
    Trigger --> FileC[📄 tickets.csv]

    FileA --> Check{JS Validation}
    FileB --> Check
    FileC --> Check

    Check -- ✓ OK --> Agent[Agent: Analyze &<br/>Rank Top 3]
    Check -- ✗ Fail --> Stop[❌ Alert]
    Agent --> Output[📧 Email Report]

    style Agent fill:#d4e6f1,stroke:#2980b9,stroke-width:2px
    style Output fill:#d5f5e3,stroke:#27ae60,stroke-width:2px
```

<details>
<summary><strong>Screenshot: Workflow Canvas</strong></summary>
<p align="center">
  <img src="implementation/Workflows/Weekly-Sales-Report/screenshots/canvas.png" alt="Workflow Canvas" width="700">
</p>
</details>

<details>
<summary><strong>Screenshot: Email Output</strong></summary>

![Email Output](implementation/Workflows/Weekly-Sales-Report/screenshots/workflow_deterministic_email-output.png)
</details>

### Assistant: Sales Research

User-initiated. Variable interpretation. Same data foundation.

**Example queries:**
- "Show me the top 3 accounts for this week"
- "Which customers have elevated churn risk?"
- "Create a pre-call briefing for TechFlow GmbH"

<details>
<summary><strong>Screenshot: Chat Response</strong></summary>
<p align="center">
  <img src="implementation/Assistants/Sales%20Research%20Assistant/screenshots/assistant_probabilistic_chat-response.png" alt="Assistant Response" width="600">
</p>
</details>

---

## Key Technical Decisions

1. **Fail-Fast Validation:** JS validation runs *before* the LLM call → errors caught at $0 cost
2. **Simulated Data Layer:** CSV files model real API payloads → ready for Salesforce/HubSpot integration

**Key Learning:** 80% of build costs occurred when the Agent executed with bad data. Validate first.

> Deep Dive: [Scoring Logic](./docs/SCORING.md) • [Full Journey](./docs/JOURNEY.md) • [Why LangDock?](./docs/TOOL-COMPARISON.md)

---

## Contact

**Yunus Ishaq** – Sales & AI Enthusiast

[![Email](https://img.shields.io/badge/Email-yunus%40ishaq.de-red)](mailto:yunus@ishaq.de)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-yunusishaq-blue)](https://www.linkedin.com/in/yunusishaq/)

---

*December 2025*
