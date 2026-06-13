Here's a complete breakdown of all the points covered in the document:

---

## AutiGuide Literature Review — Key Points

### 1. Introduction

- ASD affects social communication and involves repetitive behaviors; the WHO estimates 1 in 100 children is diagnosed globally.
- Malaysia specifically: NASOM reported a **30% surge** in student needs in the first half of 2024 alone.
- Government therapy centres are scarce, especially for rural/lower-income families.
- Caregivers lack access to instant, reliable, and affordable support — making intelligent chatbots a viable solution.

---

### 2. Existing Chatbot & Digital Solutions for ASD Caregivers

- Most existing tools are **child-directed**, not caregiver-directed.
- LLM chatbots (e.g., studied via a Chinese consultation platform) show growing demand but also highlight misinformation risks.
- A fuzzy-classifier chatbot (Polireddi et al., 2023) was proposed to bridge the patient-parent-physician gap.
- Hong Kong Metropolitan University has **two active clinical trials** on caregiver-focused chatbots (positive psychology + problem-solving), but neither is publicly available yet.
- The global digital therapeutics market for ASD was valued at **$1.14B in 2024**, projected to hit **$4.87B by 2033**.
- Notable commercial tools: **Cognoa**, **Mightier** (behavioral modification for children), and **Floreo** (VR therapy, FDA breakthrough designation in 2023).
- **Key gap:** No publicly accessible chatbot provides real-time, evidence-based guidance specifically to caregivers — which is AutiGuide's target.

---

### 3. Chatbot Architectures: Effectiveness & Limitations

**Template-Based:**

- Uses predefined rules and pattern matching.
- Predictable but rigid — can't handle phrasing variations or emotionally nuanced queries.
- HelpBot (Jusoh et al., 2024) showed even simple architectures can be clinically effective in well-scoped domains.

**Retrieval-Based:**

- Matches user queries to a curated knowledge base.
- Fast, precise, and clinically safe — dominant architecture in healthcare chatbots.
- Limitation: can feel inflexible with open-ended or ambiguous queries.
- **Chosen for AutiGuide** because reliability outweighs linguistic rigidity, especially in crisis caregiving scenarios.

**Generative (LLM-based):**

- More flexible and natural in conversation.
- Major risk: **hallucination** — generating false or fabricated medical information.
- Also issues of bias, high compute cost, and maintenance complexity.
- Deemed **too risky** for a caregiving context where inaccurate guidance could cause harm.

---

### 4. Challenges Caregivers Face Finding Trustworthy Information

**Malaysia-specific:**

- Yaacob et al. (2021) identified 4 main challenge categories from 21 Malaysian parents: inadequate knowledge, psychological distress/stigma, lack of support, and service barriers.
- ASD centres are concentrated in urban areas → delayed diagnosis/treatment for rural families.
- Healthcare providers themselves often lack sufficient ASD knowledge.
- Government therapy centres critically insufficient; private alternatives unaffordable for lower-income families.

**Day-to-day challenges:**

- Managing meltdowns, sensory processing issues, and wandering risks.
- Heightened caregiver stress, anxiety, and social isolation.
- Behavioral therapies undermined by inconsistent implementation and resource scarcity.

**Global:**

- Scattoni et al. (2023) identified systemic failures: inadequate provider training, policy gaps, delayed screening.
- In low-to-middle-income countries: added layers of financial hardship and stigma.

---

### 5. Conclusion

- No existing public tool fills the gap AutiGuide targets.
- Retrieval-based architecture is the justified choice for safety and verifiability.
- AutiGuide combines a validated knowledge base + retrieval-based NLP + a web interface.
- Future work: empirical user testing with caregivers to evaluate accuracy, usability, and impact on caregiver confidence.