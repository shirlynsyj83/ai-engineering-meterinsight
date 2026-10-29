# Week 1 — EduAdvisor Observation Sheet (MeterInsight Adaptation)
**Selected project:** MeterInsight  
**Status:** Notes based on the **printed EduAdvisor reference in the attached Part C handout**. Not a claim that EduAdvisor has been tested live. Add personal test evidence if the instructor requires a completed live observation report.

## A. Observation from the printed lab reference
| Item | EduAdvisor reference | Adaptation to MeterInsight |
| --- | --- | --- |
| Problem | Academic advice scattered across official university PDFs | Consumption data can show changes, while official utility documents explain general meter and billing concepts |
| Users | Undergraduate students | Customer-support trainees / energy-awareness facilitators |
| Data sources | Course catalogue, handbook, programme guide | Smart Meter, Bill Management, 2026 grievance mechanism; UK-DALE sample for numeric tests |
| AI capability | Document-grounded Q&A with retrieval | Document-grounded Q&A **plus** learned unusual-pattern screening |
| Evaluation | Answer quality, groundedness, latency, safety | Detection, numerical correctness, groundedness, citations, abstention, latency |
| Risks | Hallucination, fairness, inappropriate responses | Incorrect causal diagnosis, private consumption data, unsafe or stale guidance |

## B. Engineering considerations observed
1. Clearly identify the problem, users and bounded sources.
2. Separate deterministic data checks from machine-learning scores and document-grounded explanations.
3. Track evidence and limitations rather than presenting a model output as a verified meter fault.
4. Maintain an engineering record: scope, architecture, prompts, data documentation, testing and responsible AI.

## C. Hypothesis — not a test result
A combined model + source-grounded explanation may help trainees distinguish unusual usage patterns from unsupported billing conclusions better than a stand-alone anomaly score or general-purpose chatbot. This **must be tested**.

## D. Live observation log to complete personally if required
| Check | Actual result | Evidence |
| --- | --- | --- |
| Try an in-scope EduAdvisor question | Not performed | Add screenshot and notes |
| Try a question outside the covered documents | Not performed | Add screenshot and notes |
| Inspect citation quality and explanation | Not performed | Add screenshot and notes |
| Inspect its response to uncertainty | Not performed | Add screenshot and notes |

## E. Reflection
The EduAdvisor example demonstrates that the lab expects a meaningful user problem, source-grounded AI, an engineering design and objective evaluation. MeterInsight uses that same engineering pattern, with an additional small numeric model. The live observation rows are deliberately blank until actually performed.
