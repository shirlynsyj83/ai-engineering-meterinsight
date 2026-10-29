# MeterInsight — AI-Powered Electricity Consumption Analysis and Explanation Assistant

> An AI-powered assistant that helps electricity customer-support trainees and energy-awareness facilitators analyse demonstration electricity-consumption records and understand unusual patterns using explanations grounded in official Sarawak Energy documents.

## Problem Statement

Electricity-consumption records may show unusual usage changes, but interpreting them requires both numerical analysis and reliable domain information. Customer-support trainees and energy-awareness facilitators reviewing demonstration cases need to distinguish unusual patterns from confirmed causes. MeterInsight combines machine-learning-based anomaly screening with document-grounded AI explanations to support evidence-based reviews without diagnosing meter faults or determining actual billing outcomes.

## Evidence of the Problem

- **Evidence 1:** Sarawak Energy acknowledges customer concerns about unexpectedly high bills and describes account-specific reviews involving billing history and meter information. **Source:** Sarawak Energy (6 September 2026), [*Grievance Mechanism for Customers to Address Billing Concerns*](https://www.sarawakenergy.com/media-info/media-releases/2026/grievance-mechanism-for-customers-to-address-billing-concerns).
- **Evidence 2:** Sarawak Energy distinguishes current charges, overdue amounts and arrears, showing why recorded electricity consumption and the total amount payable must be interpreted separately. **Source:** Sarawak Energy, [*Bill Management*](https://www.sarawakenergy.com/customers/bill-management).

## Initial Related Work / Existing Approaches

- **Sarawak Energy's SEB cares and Energy Insights:** Existing services provide consumption information and customer-support channels. Public descriptions do not disclose their complete analytical capabilities, so this project does not claim these features are absent. **Source:** Sarawak Energy (28 August 2026), [*Reliable Electricity Supply Maintained as Dry Weather Continues*](https://www.sarawakenergy.com/media-info/media-releases/2026/reliable-electricity-supply-maintained-as-dry-weather-continues). **Limitation for this student study:** Their internal methods are not available as a reproducible experimental baseline.
- **Retrieval-Augmented Generation (RAG):** Retrieves relevant sources to support language-model answers. **Source:** Lewis et al. (2020), [*Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*](https://arxiv.org/abs/2005.11401). **Limitation:** RAG alone does not reliably analyse consumption time series or prove the cause of an unusual pattern.
- **Isolation Forest:** A machine-learning method for detecting unusual observations. **Source:** Liu, Ting & Zhou (2008), [*Isolation Forest*](https://research.monash.edu/en/publications/isolation-forest/). **Limitation:** An anomaly score does not identify a meter fault or provide official billing guidance.

## Project Objectives

- **O1:** To design an AI-powered consumption-review workflow using a public demonstration time-series dataset and three official Sarawak Energy documents, distinguishing measured patterns, general guidance and unknown causes.
- **O2:** To develop a prototype integrating data-quality checks, lightweight machine-learning anomaly detection and source-cited document-grounded AI explanations with safeguards.
- **O3:** To evaluate detection performance, numerical correctness, answer groundedness, citation accuracy, appropriate abstention, latency and safety against simple analytical and document-search baselines.

## Target Users

Electricity customer-support trainees and energy-awareness facilitators reviewing demonstration consumption cases. This is an independent educational prototype, not an official Sarawak Energy customer-support service.

## Data Sources

- **Source 1:** Sarawak Energy, [*Smart Meter*](https://www.sarawakenergy.com/customers/smart-meter) — official smart-meter information.
- **Source 2:** Sarawak Energy, [*Bill Management*](https://www.sarawakenergy.com/customers/bill-management) — billing concepts and support procedures.
- **Source 3:** Sarawak Energy, [*Grievance Mechanism for Customers to Address Billing Concerns*](https://www.sarawakenergy.com/media-info/media-releases/2026/grievance-mechanism-for-customers-to-address-billing-concerns) — account-review guidance.

**Supplementary numerical dataset:** [UK-DALE](https://jack-kelly.com/data/) — publicly available UK household electricity measurements for demonstration and controlled anomaly tests; **not** Sarawak Energy customer data or verified meter-fault labels. Source-document content will be cited and used subject to applicable access and reuse permissions.

## Weekly Progress

| Week | Focus | Deliverable | Status |
|------|-------|-------------|--------|
| W1 | System map + project scope | README + docs | Draft prepared; verify observations and GitHub submission |
