# Clinical Symptom Screening Assistant for Nurses

## Overview
This project presents a Clinical Symptom Screening Assistant designed to support nurses during early patient screening in high-pressure clinical environments where time constraints and cognitive load are significant. The system functions as a **decision-support tool**, not a diagnostic system. Its goal is to organize patient symptoms, highlight potential risk patterns, and flag cases that require escalation to licensed healthcare professionals.  
The project emphasizes safety, clarity, and responsible use of generative AI in healthcare contexts.

## Target Users
- Nurses
- Clinical assistants
- Triage support staff

## Key Constraints
- English text input only
- No storage of personal or identifiable patient data
- Outputs are non-diagnostic and non-prescriptive
- High-risk cases are always escalated to human professionals

## System Workflow
1. Nurse enters patient symptoms in free text
2. Symptoms are normalized using fuzzy matching
3. Escalation triggers are checked (e.g., red-flag symptoms)
4. Model A generates initial screening guidance
5. Relevant medical information is retrieved using RAG
6. Model B generates structured, safety-aware guidance
7. Output is displayed with a disclaimer and logged for evaluation

**Edge Case:**  
If red-flag symptoms are detected, the system bypasses generation and immediately escalates the case.

## Architecture Summary
The system follows a modular architecture separating input handling, reasoning, retrieval, and safety layers. Escalation logic can override model outputs at multiple stages to ensure safe and responsible behavior.  
See `architecture/diagram.png`.

## Prompt Engineering Strategies
- **Role-Based Prompting:** Restricts the model to a nurse-support role
- **Structured Output Prompting:** Enforces a fixed output format
- **Few-Shot Prompting:** Uses examples to improve consistency and safety

Prompt refinement combined with RAG significantly reduced hallucinated outputs.

## Model Selection
| Aspect | Model A (gpt-4o-mini) | Model B (gpt-4o) |
|------|------------------------|------------------|
| Accuracy | Moderate–High | High |
| Latency | Low | Higher |
| Cost | Low | Higher |
| Safety | Moderate | Strong |

Model A supports fast screening, while Model B provides safer guidance for ambiguous or high-risk cases.

## Evaluation
- 15 predefined test cases covering common, ambiguous, and high-risk scenarios
- Accuracy measured based on correct escalation decisions, safety compliance, and structured output adherence

**Observed improvement:**  
Accuracy increased from approximately 70% to 85% after prompt refinement and RAG grounding.

## Ethical Considerations
- No diagnosis or treatment recommendations
- Mandatory escalation for high-risk cases
- No personal patient data collected
- Clear communication of system limitations

## Reproducibility
The project is fully reproducible using Google Colab.  
Open and run `clinical_symptom_screening_assistant_DEMO.ipynb`.

## Future Work
- Expand datasets to cover rare and complex conditions
- Ongoing prompt refinement
- Additional bias analysis and advanced evaluation metrics

## References
- Disease Symptom Prediction Dataset (Kaggle)
- Disease Symptoms and Patient Profile Dataset (Kaggle)
- The Gale Encyclopedia of Medicine, 2nd Edition
