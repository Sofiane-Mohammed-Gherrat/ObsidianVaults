
## Revised Technology Stack for AutiGuide

---

### Core Language

**Python 3.11+** — remains the right choice. No change needed here. It supports every library in this stack natively.

---

### Layer 1 — User Interface

**Flask + HTML/CSS/JavaScript**

- Drop Tkinter and PySide entirely
- A web interface is more accessible, easier to build a good chat UX in, and more natural for a conversational app
- The validation step (showing reformulated questions with Yes/No buttons) is **much** easier to implement cleanly in a browser than a desktop GUI

---

### Layer 2 — LLM Reformulation Layer

This is the new addition your idea introduces. Two options depending on your privacy decision:

#### Option A — Cloud LLM (More Capable)

**Anthropic Claude API (claude-haiku-3-5)** or **OpenAI GPT-4o-mini**

- Fast, cheap, extremely capable at reformulation
- Haiku and GPT-4o-mini are specifically designed for lightweight tasks like this
- Downside — parent's raw text leaves the device

#### Option B — Local LLM (Privacy Preserving)

**Ollama running Llama 3.2 (3B) locally**

- Runs entirely on the host machine, nothing leaves the device
- Consistent with your original "no external APIs" philosophy
- Downside — requires decent hardware, slightly less capable

```PostgreSQL
Recommended for academic project → Option A (Claude Haiku or GPT-4o-mini)
Recommended for production/privacy → Option B (Ollama + Llama 3.2)
```

**Prompt is strictly constrained** — the LLM only receives the raw question and is instructed only to reformulate, never to answer.

---

### Layer 3 — NLP Preprocessing

**NLTK** — keep this, it still plays a role after the LLM reformulation for final preprocessing before matching:

- Tokenization
- Lemmatization
- Stop word removal

**Why keep NLTK if we have an LLM?** The LLM cleans the human language. NLTK then normalizes the clean output into a machine-comparable format for the retrieval engine. They serve different purposes.

---

### Layer 4 — Retrieval Engine

Replace pure keyword matching with **TF-IDF Cosine Similarity**:

**scikit-learn**

```python
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity
```

- Fully local, no external dependencies
- Significantly more accurate than keyword overlap counting
- Works perfectly on the clean, normalized question coming out of the LLM layer
- Still completely deterministic and hallucination-free

---

### Layer 5 — Knowledge Base

**JSON** — keep this, it is perfectly suitable. Structure it slightly more richly though:

```json
{
  "id": "BEH_001",
  "domain": "Behavioral Management",
  "canonical_question": "How do I handle a sensory meltdown?",
  "keywords": ["meltdown", "sensory", "overload", "tantrum"],
  "answer": "During a meltdown, reduce sensory stimulation by...",
  "source": "Autism Speaks, 2023",
  "last_verified": "2025-01"
}
```

Adding a `source` and `last_verified` field strengthens academic credibility significantly.

---

### Layer 6 — Conversation State Management

**Python dictionary / session object (Flask sessions)**

Since your architecture now has a multi-step flow (ask → reformulate → validate → answer), you need to track conversation state between steps. Flask's built-in session handling does this without any extra database.

```
session = {
  "original_input": "...",
  "reformulated_questions": [...],
  "validated_question": "...",
  "current_domain": "..."
}
```

---

### Layer 7 — Logging

**Python logging module + CSV or SQLite**

Log the following for academic analysis and system improvement:

- Original raw input
- LLM reformulated output
- Whether parent accepted or rejected reformulation
- Final matched Q&A pair
- Confidence score of the match

**SQLite** via Python's built-in `sqlite3` — no server needed, fully local, far better than plain text logs for querying patterns later.

---

## Full Revised Stack Summary

|Layer|Technology|Purpose|
|---|---|---|
|Language|Python 3.11+|Core development|
|UI|Flask + HTML/CSS/JS|Chat interface + validation buttons|
|LLM Reformulation|Claude Haiku API or Ollama + Llama 3.2|Query cleaning, intent segmentation|
|NLP Preprocessing|NLTK|Tokenization, lemmatization post-reformulation|
|Retrieval Engine|scikit-learn TF-IDF|Cosine similarity matching|
|Knowledge Base|JSON|Verified Q&A pairs with source metadata|
|State Management|Flask Sessions|Multi-step conversation flow|
|Logging|sqlite3|Query pattern analysis|

---

## How This Compares to the Original Stack

|Aspect|Original Stack|Revised Stack|
|---|---|---|
|Handles typos|❌ Poorly|✅ LLM fixes contextually|
|Handles informal language|❌ No|✅ LLM normalizes|
|Multi-intent questions|❌ No|✅ LLM segments|
|Matching accuracy|⚠️ Keyword overlap|✅ TF-IDF cosine similarity|
|Hallucination risk|✅ Zero|✅ Still zero|
|Parent trust/validation|❌ None|✅ Built-in confirmation step|
|Privacy|✅ Fully local|⚠️ Depends on LLM choice|
|Complexity|✅ Simple|⚠️ Moderate|
|Academic justifiability|✅ Strong|✅ Stronger — more sophisticated|

---

## One Important Note for Your Proposal

Since your original scope explicitly stated _"no external APIs"_, adding a cloud LLM creates a **scope contradiction** you need to address. A clean way to handle this in your proposal is to reframe it:

> _"The LLM is used exclusively as an input preprocessing layer and is never exposed to the knowledge base or response generation. All answers remain fully retrieved from the verified local knowledge base, preserving the system's hallucination-free guarantee."_

This justifies the architectural decision while staying true to your core safety philosophy.