
## Overall Verdict: Solid foundation, but surface-level in places

The document is well-structured and covers the right territory. The three research questions are genuinely coherent and they do build on each other logically. But in several sections it reads more like a literature summary than a literature _review_ — meaning it lists what papers say without critically engaging with them.

---

## Does it reflect the real challenges in ASD caregiving?

**Yes, the core problems are real and well-chosen:**

- The Malaysia-specific angle (NASOM 30% surge, rural access gap, underfunded government centres) is highly relevant and grounded in actual data.
- The caregiver stress + misinformation problem is genuinely underaddressed in existing tools.
- The gap between child-directed tools vs. caregiver-directed tools is a legitimate and important distinction.

**Where it falls short of reality:**

- **Language barrier is completely missing.** In Malaysia, caregivers span Malay, Chinese, Tamil, and English speakers. A chatbot that only works well in English already excludes a significant portion of the target population. This is a real-world challenge the review never mentions.
    
- **Trust and credibility aren't deeply explored.** The review mentions misinformation but doesn't dig into _why_ caregivers distrust online sources, or what makes them trust a tool. For a caregiving context this is critical — a parent in crisis won't use a tool they don't trust, no matter how technically sound it is.
    
- **Emotional dimension is thin.** Section 4 lists caregiver stress as a challenge but Section 3 treats it almost as an afterthought when comparing architectures. The review doesn't seriously ask: can a retrieval-based system handle emotionally charged queries (e.g., "my child just had a severe meltdown and I don't know what to do")? That's a real limitation worth confronting directly.
    
- **The hallucination risk argument is valid but one-sided.** The review dismisses generative models entirely, but doesn't acknowledge the hybrid approach your team actually implemented — using an LLM only for query reformulation, not for answer generation. That's a nuanced design decision that deserves to be theoretically justified here, and it isn't.
    

---

## Concrete Improvements

**Structurally:**

- Section 2 and Section 4 overlap significantly. Both discuss the access gap and caregiver needs. They should be more clearly differentiated — Section 2 stays focused on what tools exist, Section 4 stays focused on what caregivers actually experience day-to-day.

**Content gaps to add:**

- A paragraph on **multilingual needs** in the Malaysian context.
- A more honest discussion of **retrieval-based limitations in emotional scenarios** — and how AutiGuide mitigates this (e.g., empathetic response templates, escalation prompts).
- Explicit justification for the **hybrid architecture** (retrieval + LLM for query reformulation) — right now the review argues purely for retrieval-based, but your actual system isn't purely that.

**Tone and depth:**

- Some sections (particularly 3.3 on generative chatbots) read like they were written quickly. The argument against generative AI is correct but needs one more strong citation and a sentence acknowledging where it _could_ complement retrieval systems safely.
- The conclusion is good but generic. It would be stronger if it explicitly mapped each research finding to a specific design decision in AutiGuide.

---

## Bottom line

It's a competent literature review for a first-year group project — the research is real, the sources are recent, and the argument for AutiGuide's existence is well-made. The main weakness is that it argues _for_ the project more than it genuinely interrogates it. A stronger review would acknowledge what AutiGuide _can't_ do yet, and frame those as future work rather than ignoring them.