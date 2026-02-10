System summary: patient symptoms (including age and sex) are normalized and checked against escalation triggers.
Relevant medical reference content is retrieved using RAG and shared across both Model A and Model B.
Model A (gpt-4o-mini) performs fast initial screening, while Model B (gpt-4o) generates safety-focused,
structured guidance grounded in retrieved medical data.
Safety constraints include non-diagnostic outputs, no medication recommendations,
escalation-first logic, and mandatory clarification for missing information.
This folder documents the system design, evaluation approach, and identified failure cases.


