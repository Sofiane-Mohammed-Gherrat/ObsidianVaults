---
type: fleeting
created: 2025-08-08
tags: [fleeting, inbox]
---


Gotcha—here are **Templater-ready** Obsidian templates (they use `<% … %>` syntax, not `{{…}}`). I’ll give you compact, useful defaults you can drop into your `Templates/` folder and wire up with the Templater plugin.

# Fleeting note (quick capture)

```markdown
---
type: fleeting
created: <% tp.date.now("YYYY-MM-DD") %>
tags: [fleeting, inbox]
---

# <% tp.file.title %>

**Context / source**:  
**Idea / snippet**:  
**Next step**:  

- [ ] Promote to permanent note? → [[ ]]
```

# Permanent note — Programming concept (Python-friendly)

````markdown
---
type: permanent
created: <% tp.date.now("YYYY-MM-DD") %>
updated: <% tp.date.now("YYYY-MM-DD HH:mm") %>
topic: programming
language: python
tags: [permanent, concept, python]
aliases: []
---

# <% tp.file.title %>

**Definition (in your own words)**  
…

**Why it matters**  
…

**Minimal example**
```python
# keep it runnable
````

**Common pitfalls / gotchas**

- …
    

**See also**

- [[Related concept 1]]
    
- [[Related concept 2]]
    

**Sources**

- …
    

````

# Patterned “How-to / Recipe” note (great for libraries, CLI, or APIs)
```markdown
---
type: permanent
created: <% tp.date.now("YYYY-MM-DD") %>
topic: programming
tags: [permanent, recipe]
tooling: []
---

# <% tp.file.title %> — Quick Recipe

**Goal**  
…

**Steps**
1. …
2. …

**Code**
```python
# demo
````

**Verification / test**  
…

**Troubleshooting**

- Symptom → Fix
    

**References**

- …
    

````

# Cybersecurity technique / finding
```markdown
---
type: permanent
created: <% tp.date.now("YYYY-MM-DD") %>
topic: cybersecurity
tags: [permanent, security, technique]
tactic:  # e.g. "Privilege Escalation"
technique_id:  # e.g. "T1068"
severity:  # e.g. Low/Med/High
---

# <% tp.file.title %>

**What it is**  
…

**How it works (TTPs)**  
- …

**Detection ideas**  
- …

**Mitigations**  
- …

**Artifacts / IOCs**  
- …

**References**  
- …
````

# Software engineering — Design pattern / architecture note

````markdown
---
type: permanent
created: <% tp.date.now("YYYY-MM-DD") %>
topic: software-dev
tags: [permanent, design-pattern]
pattern:  # e.g. "Strategy"
context:  # where it fits
---

# <% tp.file.title %>

**Intent**  
…

**When to use**  
- …

**Structure / roles**  
- …

**Pros**  
- …
**Cons**  
- …

**Code sketch (optional)**
```python
# tiny example showing roles
````

**Related patterns**

- …
    

**References**

- …
    

```

# Tips so they actually render correctly
- Templater uses functions like `tp.date.now("YYYY-MM-DD")`; it **won’t** replace `{{date}}`. :contentReference[oaicite:0]{index=0}  
- Date helpers you can swap in: `tp.date.tomorrow()` or `tp.date.weekday(...)` if you want “next Monday” etc. :contentReference[oaicite:1]{index=1}  
- You can read/set frontmatter values with `tp.frontmatter[...]` if you need them later in the note. (Be aware frontmatter timing quirks on creation.) :contentReference[oaicite:2]{index=2}  
- If you plan to query these notes with **Dataview**, the frontmatter fields above are already friendly to that. :contentReference[oaicite:3]{index=3}

Want me to tailor the fields/tags to your exact vault (e.g., your Dataview queries or your Python course structure)?
::contentReference[oaicite:4]{index=4}
```


Absolutely! Here are **Obsidian templates** tailored for **fleeting notes** and **permanent notes**—perfect for learning Python, programming in general, as well as broader fields like cybersecurity and software development—based on Zettelkasten-inspired best practices.

---

## Foundations from Zettelkasten in Obsidian

- **Fleeting vs. Permanent Notes**  
    Fleeting notes are quick captures—ideas or reminders without deep context—while permanent notes are refined, atomic insights intended for long-term reference, connected via links ([Medium](https://medium.com/%40petermilovcik/note-taking-strategies-in-obsidian-permanent-vs-fleeting-notes-dd5be202d381?utm_source=chatgpt.com "Note-Taking Strategies in Obsidian: Permanent vs Fleeting ...")).
    
- **Suggested Vault Structure**  
    Common folders might include:
    
    - `Fleeting Notes`
        
    - `Literature Notes` (optional, for source material)
        
    - `Permanent Notes`
        
    - `Templates` ([Medium](https://medium.com/%40petermilovcik/note-taking-strategies-in-obsidian-permanent-vs-fleeting-notes-dd5be202d381?utm_source=chatgpt.com "Note-Taking Strategies in Obsidian: Permanent vs Fleeting ..."), [Reddit](https://www.reddit.com/r/Zettelkasten/comments/zoagdc/zettelkasten_for_coders_how_using_zettelkasten/?utm_source=chatgpt.com "How Using Zettelkasten Can Help You Level Up")).
        

---

## Example Templates

### 1. Fleeting Note Template

**Purpose**: Capture fleeting thoughts or things to explore later—minimal friction.

```markdown
---
tags: [#fleeting, programming]
date: {{date}}
---

- **Context / Source**: (e.g., “Python async tutorial” / link)
- **Snippet / Idea**: (quick jot)
- **Capture Time**: {{time}}
```

### 2. Permanent Note Template

**Purpose**: Capture atomic, self-contained knowledge—ready to connect later.

```markdown
---
tags: [#permanent, python, programming-concept]
created: {{date}}
---

# {{title}}

**Definition / explanation:**  
(Write in your own words)

**Key points:**  
- Point 1  
- Point 2

**Example / analogy:**  
(Describe example or intuition)

**Related concepts / links:**  
- [[Another Note]]
- [[Related Concept]]

**References / Sources:**  
- Source A  
- Source B
```

This leverages the idea of making each note independent yet richly connected ([Reddit](https://www.reddit.com/r/Zettelkasten/comments/zoagdc/zettelkasten_for_coders_how_using_zettelkasten/?utm_source=chatgpt.com "How Using Zettelkasten Can Help You Level Up")).

---

## Templates for Specialized Fields

#### Python & General Programming

- **Permanent Note**: Concepts like “List Comprehension”, “Decorators”, “Metaclasses”.
    
- **Example Fields**: tag with `#python`, include code snippet in **Example** section.
    

#### Cybersecurity

- **Fleeting Note**: “Log4j vulnerability” — quick capture of what sparked the thought.
    
- **Permanent Note**: Atomic topics like “SQL Injection”, “Buffer Overflow”, each with a clear definition, mitigation techniques, and related links.
    

#### Software Development (General)

- **Permanent Note**: Architectural patterns like “Singleton Pattern”, “Event Loop”, with sections for _Use Cases_, _Drawbacks_, and _Related Patterns_.
    

---

## Example Workflow Adaptation (Inspired by a coder’s journey)

A developer learning concepts like Observables might:

1. Capture a fleeting note: _“Observables vs Promises – difference? Why use Observables?”_
    
2. Later refine into a permanent note titled **"How are Observables different from Promises?"**, with definitions, comparisons, and links to other related notes (e.g., “data producers”) ([Reddit](https://www.reddit.com/r/Zettelkasten/comments/zoagdc/zettelkasten_for_coders_how_using_zettelkasten/?utm_source=chatgpt.com "How Using Zettelkasten Can Help You Level Up")).
    

---

## Setting Up in Obsidian

1. Create a `Templates` folder in your vault and enable Obsidian’s core **Templates** plugin.
    
2. Add the above templates as files: e.g., `Fleeting Note Template.md`, `Permanent Note Template.md`.
    
3. Optionally, install the **Templater** plugin for dynamic insertion (dates, time, etc.) ([Obsidian Forum](https://forum.obsidian.md/t/16-obsidian-templates-for-zettelkasten-to-start-with/49098?page=3&utm_source=chatgpt.com "16 Obsidian Templates For Zettelkasten To Start With"), [Obsidian Forum](https://forum.obsidian.md/t/16-obsidian-templates-for-zettelkasten-to-start-with/49098?page=2&utm_source=chatgpt.com "16 Obsidian Templates For Zettelkasten To Start With"), [Reddit](https://www.reddit.com/r/ObsidianMD/comments/18s5tsv/beginning_with_obsidian_general_template_for_notes/?utm_source=chatgpt.com "Beginning with Obsidian - General Template for Notes?")).
    

---

Would you like help customizing these for a specific topic or setting up the YAML tags, folder defaults, or plugin setup in Obsidian?