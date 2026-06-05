# Annotation Best Practices for Clinical AI Evaluation

A practical guide for clinicians working on AI evaluation, data annotation, and human-in-the-loop review workflows.

---

## 1. Read the Full Output Before Annotating

Resist the urge to flag the first error you see and move on. Read the entire output first. Errors often compound — a wrong diagnosis in paragraph one may make a correct treatment recommendation in paragraph three appear sound when it is not.

---

## 2. Always Return to the Source Input

Every annotation decision must be grounded in what the input actually said — not what you think it probably meant. If the input did not mention a lab value, any specific numeric finding in the output is a hallucination regardless of how clinically plausible it seems.

---

## 3. Separate "Clinically Wrong" from "Stylistically Different"

AI outputs may use phrasing or documentation styles that differ from your personal practice but are still clinically acceptable. Reserve flags for genuine errors, omissions, or safety concerns — not stylistic preferences. Ask yourself: *"Would a reasonable senior clinician accept this?"* If yes, note it but do not flag.

---

## 4. Document Errors with Direct Evidence

When flagging an error, always quote the specific text from the AI output. Vague feedback like *"dosage is wrong"* is not actionable. Specific feedback like *"Metformin 2000mg OD prescribed — standard maximum daily dose is 2000mg but should be divided into BD or TDS doses, not given as a single dose"* gives the model team something to work with.

---

## 5. Classify Error Severity Consistently

Use a consistent severity scale for every evaluation:

| Level | Definition | Action |
|-------|------------|--------|
| **Low** | Minor stylistic or completeness issue; no clinical impact | Note in feedback; accept output |
| **Medium** | Clinical inaccuracy with low immediate risk; output needs revision | Return for correction |
| **High** | Significant error with potential patient impact | Reject; detailed feedback required |
| **Critical** | Error that could directly cause patient harm | Immediate rejection; escalate to QA lead |

---

## 6. Flag Hallucinations Separately from Reasoning Errors

A hallucination is a fabrication — something the model invented with no basis in reality (e.g., a non-existent drug, a made-up lab value). A reasoning error is when the model uses real information incorrectly (e.g., recommending a real drug that is contraindicated). Both are serious, but they require different model corrections and should be documented separately.

---

## 7. Maintain Annotation Consistency Across Sessions

Your annotations are training signal. If you flag a phantom drug on Monday but accept the same drug name on Friday because you are tired, you are introducing noise into the model's learning. When in doubt, flag — it is easier for a QA reviewer to dismiss an over-flagged output than to catch an under-flagged safety issue.

---

## 8. Do Not Over-Annotate

More annotations are not always better. Flag what matters clinically. Annotating every minor preposition choice or preferred phrasing variant dilutes the signal and makes your feedback harder to act on. Prioritise factual accuracy, completeness, safety, and reasoning quality.

---

## 9. Consider the End User When Scoring

A clinical note written for a specialist audience may omit basics that would be essential in a general ward note. Always score an output relative to its stated purpose and intended audience. Ask: *"For whom was this written, and does it serve that reader well?"*

---

## 10. Track Your Own Patterns

Over time, note which error types you encounter most frequently. If you are seeing the same hallucination type repeatedly across different outputs, that is systematic — document it as a pattern and flag it to the project lead. Pattern recognition at the evaluator level is one of the most valuable contributions a human reviewer can make.

---

*Maintained by Isaac Ochekwu, MBBS | Updated continuously based on active evaluation work.*
