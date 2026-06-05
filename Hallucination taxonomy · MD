# Hallucination Taxonomy in Medical AI

A structured classification of the hallucination types I have encountered while evaluating AI-generated clinical content. Each type is defined, illustrated with an anonymized example, and paired with a detection tip.

---

## Type 1: Phantom Drug Hallucination

**Definition:** The AI invents a drug name that does not exist, or attributes real drug properties to a non-existent agent.

**Example (Flagged Output):**
> "The patient was commenced on *Cardivazol 50mg* daily for rate control."

*Cardivazol* does not exist. The AI likely conflated carvedilol and metoprolol.

**Detection tip:** Cross-reference all drug names against a standard formulary (e.g., BNF, WHO Model List). Any unfamiliar name should be verified before accepting.

---

## Type 2: Fabricated Laboratory Values

**Definition:** The AI generates specific lab values that were not in the source input, presenting them as if they were documented findings.

**Example (Flagged Output):**
> "Results showed a serum potassium of 3.1 mmol/L and a creatinine of 112 µmol/L."

If no labs were provided in the input prompt, these values are hallucinated — the model is generating plausible-sounding numbers with no grounding in the patient's actual data.

**Detection tip:** Always check whether the source input contained lab values. If it did not, any specific numeric findings in the AI output are fabricated.

---

## Type 3: Wrong Organ System Attribution

**Definition:** The AI correctly identifies a condition but attributes it to the wrong organ system or anatomical location.

**Example (Flagged Output):**
> "The patient's shortness of breath is likely secondary to *hepatic congestion causing pulmonary oedema*."

While hepatic congestion can contribute to fluid overload, framing it as the primary driver without right heart failure context reflects faulty reasoning and potential organ system confusion.

**Detection tip:** Trace the pathophysiological chain. If the stated mechanism doesn't follow standard anatomical or physiological logic, flag it.

---

## Type 4: Non-Existent Guideline Citation

**Definition:** The AI references a clinical guideline, protocol, or recommendation that does not exist or misattributes real guidance.

**Example (Flagged Output):**
> "Per the 2022 WHO Sepsis Management Protocol Section 4.3, empirical antibiotics should be delayed until two blood cultures are obtained."

The 2022 WHO guidance on sepsis does not include this specific provision, and delaying antibiotics in sepsis contradicts the Surviving Sepsis Campaign guidelines.

**Detection tip:** Never accept guideline citations at face value. Verify the document name, year, and specific recommendation independently.

---

## Type 5: Contraindication Omission Hallucination

**Definition:** The AI recommends a drug or procedure while omitting a clearly documented contraindication present in the input.

**Example (Flagged Output):**
> "Ibuprofen 400mg TDS was prescribed for pain relief."

If the input documented CKD Stage 3 or active peptic ulcer disease, recommending NSAIDs without flagging the contraindication constitutes a safety-critical omission hallucination.

**Detection tip:** For every drug recommendation, mentally run through NSAID, anticoagulant, and nephrotoxic drug checklists against patient comorbidities stated in the input.

---

## Type 6: Temporal Confusion

**Definition:** The AI conflates past history with the current presentation, or reverses the timeline of events.

**Example (Flagged Output):**
> "The patient presented with chest pain. He had a myocardial infarction 3 years ago and is currently being managed for the same."

If the source input described a resolved MI with no current ischaemia, framing the current presentation as the "same" event is a temporal hallucination that could lead to inappropriate investigation or treatment.

**Detection tip:** Construct a mental timeline from the input. Flag any AI output that collapses past and present events into a single ongoing episode.

---

## Summary Table

| Type | Risk Level | Frequency in My Reviews |
|------|------------|------------------------|
| Phantom Drug | Critical | Common |
| Fabricated Lab Values | High | Very Common |
| Wrong Organ Attribution | Medium–High | Occasional |
| Non-Existent Guideline | Medium | Occasional |
| Contraindication Omission | Critical | Common |
| Temporal Confusion | Medium | Occasional |

---

*This taxonomy is updated as new hallucination patterns are identified through ongoing evaluation work.*
