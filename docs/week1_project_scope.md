# Part C Project Scoping Template

Updated: 29 October 2026. Revised from the previous ESG project. Preliminary Week 1 scope; objectives and evaluation thresholds will be refined in Topic 2.

## Project Name

**MeterInsight**

*Subtitle: Document-Grounded Electricity Consumption Review Assistant.*

Adapted from the previously proposed **Uncertainty-Aware Smart-Meter Data-Quality and Consumption-Change Diagnosis** project. This semester prototype retains data-quality checking and learned consumption-pattern screening, while narrowing diagnosis to evidence-supported review. It does not establish the physical cause of a change, certify a meter fault, determine theft, adjudicate a bill, or control electrical equipment.

## Domain

Energy / Smart Metering / Customer-Support Training

## Problem Statement

Customer-support trainees reviewing electricity-consumption concerns need to distinguish observed usage changes, incomplete measurement data and billing concepts that require account-level verification. Public consumption records alone cannot establish why a particular Sarawak Energy bill increased, and a generic language model could incorrectly present a possible explanation as a confirmed cause. MeterInsight will combine lightweight machine-learning analysis of demonstration consumption records with explanations grounded in official Sarawak Energy documents, explicitly separating measured findings, general guidance and unresolved questions for human review.

## Evidence of the Problem

**Evidence 1:** Sarawak Energy acknowledges concerns about unexpectedly high bills and describes individual reviews using account history, billing records and available meter information. This establishes a real review need and the limits of conclusions based on consumption alone; it does not establish that the existing review service is ineffective.

**Source / citation:** Sarawak Energy. (6 September 2026). *Grievance Mechanism for Customers to Address Billing Concerns.*

https://www.sarawakenergy.com/media-info/media-releases/2026/grievance-mechanism-for-customers-to-address-billing-concerns

**Evidence 2:** Sarawak Energy's bill-management documentation distinguishes current charges, overdue amounts and arrears, and explains available customer-support processes. These distinctions support the need to separate a change in measured energy use from a change in the amount payable.

**Source / citation:** Sarawak Energy. (n.d.). *Bill Management.* Accessed 29 October 2026.

https://www.sarawakenergy.com/customers/bill-management

## Initial Related Work (at least 3)

**Study / solution 1:** Sarawak Energy's existing SEB cares, Energy Insights and customer-review channels.

**Source / citation:** Sarawak Energy. (28 August 2026). *Reliable Electricity Supply Maintained as Dry Weather Continues* — describes hourly, daily and monthly consumption views through Energy Insights.

https://www.sarawakenergy.com/media-info/media-releases/2026/reliable-electricity-supply-maintained-as-dry-weather-continues

Sarawak Energy. (6 September 2026). *Grievance Mechanism for Customers to Address Billing Concerns* — describes human review and the available channels, including Carina.

https://www.sarawakenergy.com/media-info/media-releases/2026/grievance-mechanism-for-customers-to-address-billing-concerns

**Key limitation:** Public descriptions do not expose these systems' complete analytical capabilities or provide a reproducible benchmark for this student study. They establish relevant existing services; they do not justify claiming that the company lacks anomaly detection or grounded explanations. The proposed project is an independent training and evaluation prototype, not a replacement service.

**Study / solution 2:** Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks.

**Source / citation:** Lewis, P., et al. (2020). *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*. NeurIPS 2020.

https://arxiv.org/abs/2005.11401

**Key limitation:** Retrieval can provide source context, but does not itself analyse numeric consumption records or guarantee correct causal reasoning. Numerical findings need a separate analysis component and generated claims need source-support evaluation.

**Study / solution 3:** Isolation Forest.

**Source / citation:** Liu, F. T., Ting, K. M., & Zhou, Z.-H. (2008). *Isolation Forest*. IEEE International Conference on Data Mining.

https://research.monash.edu/en/publications/isolation-forest/

Implementation reference: https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html

**Key limitation:** An unusual pattern is not a labelled meter fault, a calibrated probability of failure, or proof of its cause. Performance depends on the reference history and features, and the model does not provide authoritative customer-service guidance.

## Engineering Gap / Limitation

**Gap / Limitation:** This project will investigate how to combine numeric pattern screening and official documentary evidence in a small, reproducible review workflow without converting anomaly scores into unsupported causal claims. The prototype will separate (1) deterministic data-quality findings, (2) learned unusual-pattern scores, (3) source-backed general explanations, and (4) questions that require authorised human review. Whether this combination improves understanding and review efficiency over simple analysis plus document search is an experimental question, not an established company capability gap.

A document-only FAQ assistant would remove the original project's analytical purpose. Conversely, attaching unrelated PDFs to a time-series model would not constitute meaningful use of documents as data sources. Both the numeric and document components are part of the minimum scope.

## Initial Project Objectives (2–3)

**O1:** To design a bounded electricity-consumption review workflow for customer-support trainees using three official public documents and a public demonstration dataset, with explicit separation of measured evidence, anomaly indications and unresolved causes.

**O2:** To develop a prototype integrating deterministic data-quality checks, one lightweight machine-learning pattern detector, and document-grounded explanations with citations and appropriate abstention and safety controls.

**O3:** To evaluate the prototype against simple analytical and document-search baselines using controlled anomaly experiments and held-out question scenarios, measuring detection performance, numerical correctness, retrieval relevance, answer groundedness, appropriate abstention, latency and safety.

## Target Users

Primary intended users: electricity customer-support trainees and energy-awareness facilitators learning to review consumption concerns using demonstration cases. Student peers may participate in an initial usability study; their feedback will not be presented as validation by Sarawak Energy staff.

Potential later users: authorised customer-support staff, subject to company review and local evaluation. The semester prototype is independent student work and is not an official Sarawak Energy service.

## Data Sources (at least 2)

**Source 1:** Sarawak Energy, *Smart Meter* — URL:

https://www.sarawakenergy.com/customers/smart-meter

Role: grounded answers about smart-meter functionality, readings and the distinction between meter replacement and consumption changes.

**Source 2:** Sarawak Energy, *Bill Management* — URL:

https://www.sarawakenergy.com/customers/bill-management

Role: grounded explanations of billing components and official review channels. Limit retrieval to the domestic-consumption review topic; omit commercial tariff calculations, penalties, legal interpretation and account adjudication from the prototype's answer scope.

**Source 3:** Sarawak Energy, *Grievance Mechanism for Customers to Address Billing Concerns* (6 September 2026) — URL:

https://www.sarawakenergy.com/media-info/media-releases/2026/grievance-mechanism-for-customers-to-address-billing-concerns

Role: explain what evidence is used in an individual review and when a question needs official assistance. Historical temporary-counter arrangements will not be presented as current.

These are three separate publicly accessible web documents used by the explanation component, not merely bibliography entries. Part C does not explicitly restrict documents to PDF. Record titles, URLs, access dates, document versions and selected sections. Public access is not permission to redistribute: retain source links in GitHub and download or cache content only as permitted.

**Supplementary numeric dataset:** UK Domestic Appliance-Level Electricity (UK-DALE), by Jack Kelly and William Knottenbelt.

Dataset and access instructions: https://jack-kelly.com/data/

Paper: https://doi.org/10.1038/sdata.2015.7

Role: a small subset of whole-house time-series data for testing consumption-pattern analysis. Use the low-frequency whole-house channels; appliance disaggregation and high-frequency waveform analysis are outside scope. Convert power to interval energy with timestamp-aware integration and explicit missing-data handling. Do not treat watts as kilowatt-hours, or missing values as zero usage.

UK-DALE describes five UK homes. It does not provide Sarawak customer records, verified meter-fault labels or billing-dispute outcomes. All cases must be labelled as demonstrations, without applying Malaysian tariffs to UK households. Dataset reuse and any derived-file sharing must follow the dataset's terms.

Minimum implementation: curated demonstration records; explicit units and coverage checks; one Isolation Forest model on daily features; a rolling same-weekday baseline; retrieval over the three documents; a pretrained language model constrained to supplied evidence; and a small interface. Do not train a large language model. Compare retrieval-augmented answers with keyword search and a full-document-context baseline because the initial corpus is small.

Evaluation design: use chronological training/development/test partitions without overlapping windows; fit preprocessing on training data only. Test controlled missing blocks, flatlines and sustained shifts with recorded injection labels, while recognising that these are simulations rather than verified physical faults. On untouched data report alert rate and reviewed examples, not an unverified false-positive rate. Use a held-out question set covering factual, numeric-plus-document, insufficient-evidence and unsafe requests. Record claim support, citation correctness, numerical errors, abstention, latency and run cost. Lock the test set before tuning prompts or thresholds.

## Similar to EduAdvisor

Both systems address a defined user group, consult a bounded set of authoritative public documents, and generate source-supported answers with limits on unsupported claims. Both require requirements, architecture, data documentation, prompts, evaluation evidence and responsible-AI records in GitHub. The engineering process includes retrieval, citations, abstention and objective testing.

## Different from EduAdvisor

MeterInsight addresses electricity-consumption review rather than course and graduation advice. It combines numeric analysis and a small anomaly detector with documentary explanations. Its data-quality checks and calculations are deterministic, while learned models identify patterns and interpret questions. It must distinguish measured kWh changes from changes in a bill's payable amount, and it cannot infer an individual account's actual cause from general documents. It has no connection to live meters, customer accounts or operational control systems.

## Responsible AI Risks (at least 2)

**Risk 1: Hallucination, unsupported causality and misleading confidence.** A generated response could claim that an unusual pattern proves a defective meter, a particular appliance, or wrongdoing. Controls: separate observations from general explanations; cite applicable documents; state unknowns; do not display anomaly scores as fault probabilities; abstain from physical diagnosis, accusations and bill adjudication. Measure unsupported-claim and inappropriate-certainty rates.

**Risk 2: Privacy and data governance.** Actual customer bills and usage records can reveal identities and household routines. Controls: use public or synthetic demonstration cases; do not collect account numbers, addresses or private bills in the semester prototype; keep credentials out of GitHub; exclude restricted documents and raw data without redistribution permission; document any external-model data flow.

**Risk 3: Safety, representativeness and stale guidance.** UK usage patterns may not generalise to Sarawak, and obsolete instructions or generated repair advice could mislead users. Controls: label domain limitations; use dated, versioned official sources; test conflicts and expired announcements; provide no wiring, meter-opening, disconnection, tariff-adjudication or autonomous operational instructions; direct unresolved cases to authorised support. Treat retrieved content as evidence, not instructions that can override the system's safety and scope rules. Evaluation success on a small test set is not deployment certification.
