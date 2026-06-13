
## AutiGuide – How the Project Works

AutiGuide is a **chatbot application** designed to help parents and caregivers of children with Autism Spectrum Disorder (ASD) get quick, reliable information. Here's a breakdown of how it all fits together:

---

### What It Does

When a user types a question — like _"How do I handle my child's meltdowns?"_ — the chatbot processes that question and retrieves the best matching answer from its pre-built knowledge base. It doesn't generate new answers on the fly; it finds the most relevant pre-written response.

---

### The Core Components

**1. The Knowledge Base** The heart of the system is a structured database of at least 100 Q&A pairs, organized into 5 topics:

- Behavioral management (meltdowns, sensory overload)
- Therapy & interventions (ABA, speech therapy)
- Dietary guidance (food sensitivities, nutrition)
- School & social support (inclusive education in Malaysia)
- Malaysian resources (local NGOs, clinics, government programs)

This is stored in **JSON format**, essentially a structured list the system can quickly search through.

**2. Natural Language Processing (NLP)** Since users won't type questions in exactly the way they're stored in the database, the system uses NLP techniques to bridge that gap:

- **Tokenization** — breaks the user's sentence into individual words
- **Lemmatization** — reduces words to their root form (e.g. "running" → "run")
- **Keyword extraction & pattern matching** — identifies the key intent of the question and finds the closest matching answer in the knowledge base

All of this is handled locally using the **NLTK** Python library — no internet connection or external AI needed.

**3. The Interface** The user interacts through either a web browser (built with **Flask**) or a desktop window (built with **Tkinter**). It's designed to look and feel like a simple chat window.

**4. Fallback Mechanism** If a question falls outside the knowledge base entirely, the system doesn't guess — it responds with a responsible message directing the user to consult a qualified professional.

**5. Conversation Logging** The system logs common query patterns so developers can improve the knowledge base over time.

---

### What It Deliberately Does NOT Do

- It won't diagnose or replace medical advice
- It won't use generative AI (like ChatGPT) — all answers come from verified, curated content
- It won't support other languages (English only)
- It won't store any personal user data

---

### The Simple Flow

```
User types a question
        ↓
NLP processes the text (tokenize → lemmatize → extract keywords)
        ↓
System matches keywords to the knowledge base
        ↓
Best matching answer is returned
        ↓
If no match → fallback response (consult a professional)
```

In short, AutiGuide is a **specialized, offline, rule-based chatbot** — reliable and transparent by design, targeted specifically at an underserved community in Malaysia.

