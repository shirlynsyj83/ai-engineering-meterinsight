# MeterInsight
> **Document-Grounded Electricity Consumption Review Assistant**

**Status:** Preliminary AI Engineering Lab (Part C) Week 1 project scope. Proposed student prototype; not an operational Sarawak Energy service, and not endorsed by the company.

## What does MeterInsight do?
MeterInsight helps electricity customer-support trainees study **demonstration** consumption cases. It checks time-series data quality, flags unusual usage patterns with a lightweight machine-learning model, and explains related smart-meter and billing concepts using cited Sarawak Energy public documents. It deliberately **does not** diagnose defective meters, identify wrongdoing, adjudicate bills, or operate electrical infrastructure.

## Domain
Energy / Smart Metering / Customer-Support Training.

## Problem Statement
Electricity consumption changes, incomplete readings, and bill-payment components are often confused. A change in a consumption record cannot by itself establish the cause of an actual bill increase. MeterInsight will test whether integrating measured-pattern screening with a small document-grounded assistant helps users distinguish observations, general guidance, and unresolved account-specific questions.

## Evidence of the Problem
1. Sarawak Energy's [billing grievance mechanism (6 Sep 2026)](https://www.sarawakenergy.com/media-info/media-releases/2026/grievance-mechanism-for-customers-to-address-billing-concerns) acknowledges concerns about unexpectedly high bills and describes reviews using billing history, meter information, and account records.
2. Sarawak Energy's [Bill Management](https://www.sarawakenergy.com/customers/bill-management) page distinguishes current charges from overdue amounts and arrears, supporting a need to separate energy usage from the total payable amount.

This evidence supports the use case; **it does not demonstrate a deficiency in Sarawak Energy's current systems**.

## Initial Related Work / Existing Approaches
1. **SEB cares and Energy Insights** — existing consumption-monitoring and customer-support channels. [Official description (28 Aug 2026)](https://www.sarawakenergy.com/media-info/media-releases/2026/reliable-electricity-supply-maintained-as-dry-weather-continues). Public descriptions do not establish the full underlying analytics, so we do not claim Sarawak Energy lacks ML.
2. **Retrieval-Augmented Generation (RAG)** — combines retrieved source evidence with generation; on its own it does not analyse numeric time series or guarantee factual explanations. [Lewis et al. (2020)](https://arxiv.org/abs/2005.11401).
3. **Isolation Forest** — detects unusual multivariate observations without verified fault labels; its scores are **not** causes or calibrated fault probabilities. [Liu et al. (2008)](https://research.monash.edu/en/publications/isolation-forest/).

## Engineering Gap / Limitation
Can a small, reproducible training prototype integrate **deterministic data-quality checks**, **learned unusual-pattern screening**, and **source-grounded explanations**, while clearly distinguishing observations from unsupported causal conclusions? The measured benefit over simple anomaly screening and document search remains a **hypothesis to evaluate**, not a claim about the company's capability gap.

## Project Objectives
- **O1:** Design a bounded consumption-review workflow using three official Sarawak Energy public documents and one public demonstration dataset.
- **O2:** Develop a prototype with data-quality checks, one lightweight anomaly detector, and cited document-grounded explanations with abstention controls.
- **O3:** Evaluate detection performance in controlled tests, numerical correctness, evidence support, appropriate abstention, and latency against simple baselines.

## Target Users
Customer-support trainees and energy-awareness facilitators using anonymised demonstration scenarios. Actual company staff or customers are not participating by default.

## Public Documents (used as AI grounding sources)
1. [Sarawak Energy — Smart Meter](https://www.sarawakenergy.com/customers/smart-meter)
2. [Sarawak Energy — Bill Management](https://www.sarawakenergy.com/customers/bill-management)
3. [Sarawak Energy — Grievance Mechanism for Customers to Address Billing Concerns (6 Sep 2026)](https://www.sarawakenergy.com/media-info/media-releases/2026/grievance-mechanism-for-customers-to-address-billing-concerns)

These are **three separate publicly accessible web documents**; the lab does not require all sources to be PDFs. Public access does not imply redistribution or training rights. Record source title, URL, access date, selected sections, and permissions before using externally hosted text.

## Numeric Demonstration Dataset
**UK-DALE (UK Domestic Appliance-Level Electricity)** — [dataset](https://jack-kelly.com/data/) and [paper](https://doi.org/10.1038/sdata.2015.7). Use only a **small subset of whole-house, low-frequency power measurements** to evaluate a demonstration time-series pipeline. It contains UK households, not Sarawak Energy records, billing outcomes, or verified meter-fault labels.

Handle timestamps, gaps and unit conversion carefully. Convert watts to interval kWh using elapsed time, not by treating power as energy. Do not apply Malaysian tariff calculations to UK-DALE homes.

## Planned MVP
1. Load a small sample household power time series; check coverage, missing intervals and units.
2. Generate daily features and a simple moving/weekday baseline.
3. Fit **one** Isolation Forest model and flag unusual days for further review.
4. Answer smart-meter and billing questions through keyword/semantic retrieval from the three public sources with citations.
5. Present findings in separate sections: **observed measurements**, **possible unusual pattern**, **what official guidance says**, and **what cannot be concluded**.
6. Offer a small Streamlit/Gradio interface for a prepared demonstration case.

**No** live meter connection, customer account access, operational decision, or automatic billing outcome is planned. A large language model will **not** be trained from scratch.

## Evaluation Plan
- **Numeric side:** chronological train/test split, training-only preprocessing, baseline vs Isolation Forest. Use labelled *synthetic injections* (missing blocks, flatlines, level shifts) to assess alert detection; synthetic anomalies are not verified meter faults.
- **Document side:** held-out factual, explanatory, mixed numeric-and-document, unsupported and unsafe questions. Compare keyword retrieval, document-only prompting and the combined workflow.
- **Metrics:** controlled-event precision/recall/F1 where labelled; false-alert frequency on unlabelled natural observations (not an assumed ground-truth false-positive rate); numerical accuracy; evidence/citation support; abstention appropriateness; median/p95 latency.
- **Protocol:** specify fixed splits, question gold references, model settings and evaluation thresholds before final testing. No results have been measured yet.

## Responsible AI & Security
- **Misleading causality:** anomaly scores do not prove a defective meter, tampering, or what caused a bill increase. Show uncertainty and abstain.
- **Privacy:** no personal bills, addresses, customer IDs or live smart-meter readings; public/synthetic educational examples only.
- **Safety:** never instruct users to open meters or interact with electrical installations; direct real account disputes to authorised channels.
- **Representativeness:** clearly disclose that UK-DALE is from UK households and cannot validate utility-scale operation in Sarawak.
- **Data rights and prompt injection:** preserve source links, review reuse rights, avoid uploading restricted content, keep retrieved text untrusted and never commit credentials.

## Proposed System Architecture
See [conceptual diagram](docs/week1_system_map.png) and [diagram notes](docs/week1_system_map.md).

## Repository Structure
```text
README.md
.gitignore
docs/
  week1_observation_sheet.md
  week1_project_scope.md
  week1_system_map.png
  week1_system_map.dot
  week1_system_map.md
  GITHUB_SETUP.md
data/
src/
notebooks/
prompts/
evaluation/
  question_set_template.md
```

## Weekly Progress
| Week | Focus | Deliverable | Status |
| --- | --- | --- | --- |
| W1 | Scope, source selection, conceptual system and GitHub record | README + three lab files | Draft prepared; real GitHub repository not yet created |
| W2 | Requirements, dataset sampling and baseline design | Requirements and gold questions | Planned |
| W3+ | Prototype, verification and evaluation | Code and evidence | Planned |

## Coursework Note
This is an independent undergraduate project, not an official Sarawak Energy application. The `week1_observation_sheet.md` file explicitly distinguishes observations from the printed EduAdvisor example and live observations you must perform yourself if required.
