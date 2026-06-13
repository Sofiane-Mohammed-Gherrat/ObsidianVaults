

AutiGuide will be developed using:

- **Python 3.11+** as the main language 

- **Streamlit** for the web chat interface.
	we will `st.chat_input`, `st.chat_message`, and `st.session_state` to create the conversation flow
```
Raw input → LLM reformulation → Parent validation → Retrieval → Answer
```

- **Ollama running Llama 3.2 (3B)** as a local LLM to reformulate query, fix typos, segment intent ( if the question covers more than one domain ex: behavioural and dietary );  we could include **Claude Haiku API** upgrade available to premium user ( but will introduce privacy concerns )
> PS: after the LLM reformulates the question, the parent is prompted to validate the reformulation, saying: is it what you meant? or did you mean: ...

- **NLTK** for processing the reformulated query by doing: tokenization, lemmatization, and stop word removal before the retrieval stage.

- **scikit-learn** for TF-IDF vectorization and cosine similarity matching between the question and the knowledge base.
```python
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity
```

- **JSON**: knowledge base to store verified Q&A pairs by a medical practitioner: falling under 5 categories, each entry includes: a question, answer, domain label, and source reference


- The discussion and its treatment remain local to reduce any privacy concern, so data would maybe shared with third parties after the agreement of the user and it would be to unlock specific features 

---

>AutiGuide will be developed using Python as the primary programming language. The Natural Language Toolkit (NLTK) library will handle local text preprocessing including tokenization, lemmatization, and part-of-speech tagging. The knowledge base will be structured in JSON format for efficient pattern matching and response retrieval. The user interface will be built using Flask for web deployment or Tkinter for desktop deployment.

>The system will operate entirely without external APIs, cloud-based AI services, or third-party chatbot platforms. All processing runs locally on the host machine, mirroring the template-based local NLP architecture validated by Jusoh et al. (2024) in HelpBot. This ensures full transparency, reproducibility, and academic integrity throughout development.


