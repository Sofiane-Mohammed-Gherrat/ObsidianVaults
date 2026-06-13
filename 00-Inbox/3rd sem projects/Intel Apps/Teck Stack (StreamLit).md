
## Streamlit — Is It the Right Choice?

**Honestly, for this project, yes.** Here is why:

Streamlit is specifically designed for Python developers who want to build functional interfaces without investing heavily in frontend work. Since your team's focus is clearly on the backend AI pipeline, Streamlit lets you build a working chat interface in literally dozens of lines of Python rather than hundreds.

```python
import streamlit as st

st.title("AutiGuide")

if "messages" not in st.session_state:
    st.session_state.messages = []

for message in st.session_state.messages:
    with st.chat_message(message["role"]):
        st.write(message["content"])

if prompt := st.chat_input("Type your question here..."):
    # your entire pipeline runs here
```

Streamlit has a native `st.chat_input` and `st.chat_message` component built specifically for chatbot UIs. It handles the chat layout out of the box.

---

## Streamlit vs Alternatives for Your Case

| Feature | Streamlit | Flask | Tkinter / PySide |
|---|---|---|---|
| Setup speed | ✅ Minutes | ⚠️ Hours | ⚠️ Hours |
| Chat UI built-in | ✅ Yes | ❌ Build yourself | ❌ Build yourself |
| Python only | ✅ Yes | ⚠️ Needs HTML/JS/CSS | ✅ Yes |
| Backend focus friendly | ✅ Yes | ⚠️ Splits attention | ✅ Yes |
| Validation buttons | ✅ `st.button()` | ⚠️ Needs JS | ⚠️ Manageable |
| Deployment | ✅ Streamlit Cloud free | ⚠️ Needs server setup | ❌ Desktop only |
| Flexibility | ⚠️ Limited custom UI | ✅ Full control | ✅ Full control |
| Professional look | ⚠️ Generic by default | ✅ Fully customizable | ❌ Outdated look |

**The one real weakness of Streamlit** is that it reruns the entire script on every interaction, which makes conversation state management slightly unconventional. But this is very manageable — which leads to your next question.

---

## Conversation State Management in Streamlit

This is the most important technical question for your architecture because your pipeline has **multiple steps** per question:

```
Raw input → LLM reformulation → Parent validation → Retrieval → Answer
```

Streamlit handles state through `st.session_state`, which is a dictionary that **persists across reruns within the same session**. Here is how you would manage your specific multi-step flow:

### The State Object

```python
# Initialize on first load
if "pipeline_stage" not in st.session_state:
    st.session_state.pipeline_stage = "awaiting_input"
    st.session_state.original_input = None
    st.session_state.reformulated_questions = []
    st.session_state.validated_question = None
    st.session_state.chat_history = []
```

### The Stage-Based Flow

```PostgreSQL
pipeline_stage = "awaiting_input"
        ↓ parent types question
pipeline_stage = "awaiting_validation"
        ↓ parent clicks Yes/No/Edit
pipeline_stage = "retrieving_answer"
        ↓ answer returned
pipeline_stage = "awaiting_input"  ← resets for next question
```

Each stage renders a different UI and triggers different logic. This is clean, readable, and fully manageable in Streamlit.

---

## The LLM Choice — Local First, API Optional

Your approach of defaulting to local with an optional paid upgrade is smart. Here is how to structure it cleanly:

### Recommended Local LLM

**Ollama + Llama 3.2 (3B)**

- Free, runs locally, good enough for reformulation only
- One command to install: `ollama pull llama3.2`
- Python integration is simple

```python
import ollama

response = ollama.chat(
    model="llama3.2",
    messages=[{"role": "user", "content": your_strict_prompt}]
)
```

### Optional API Upgrade

**Claude Haiku (claude-haiku-4-5)** at roughly $0.001 per query — the $3 estimate is reasonable for moderate usage.

The user toggle in Streamlit is simple:

```python
st.sidebar.toggle("Use Claude API for better accuracy ($)", 
                   key="use_api")

if st.session_state.use_api:
    # call Claude API
else:
    # call local Ollama
```

---

## Revised Final Stack

|Layer|Technology|
|---|---|
|Language|Python 3.11+|
|UI + State|Streamlit + st.session_state|
|LLM (default)|Ollama + Llama 3.2 3B|
|LLM (optional)|Claude Haiku API|
|NLP|NLTK|
|Retrieval|scikit-learn TF-IDF|
|Knowledge Base|JSON|
|Logging|Not in scope for now|

This is a clean, focused, academically justifiable stack that keeps your team's energy where it matters — the AI pipeline — while delivering a functional and presentable interface.

---
