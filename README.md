# DecodeLabs AI Internship - Project 1: Rule-Based AI Chatbot

## 📌 Project Overview

The goal is to build a rule-based AI chatbot from scratch using Python - no machine learning, no frameworks. Just pure control flow, logic, and dictionary-based decision making. This project demonstrates the **foundation of all AI systems**: before a machine can learn on its own, it must first be taught through explicit, deterministic rules.

---

## 🧠 What is a Rule-Based Chatbot?

A rule-based chatbot is a **white box system** — every decision is traceable, every response is hard-coded, and there is zero hallucination risk. It works by mapping user inputs to predefined responses using an exact-match lookup.

This is the same logic that powers **AI guardrails** in production systems like NVIDIA NeMo and Llama Guard — the deterministic control layer that sits on top of probabilistic LLMs.

---

## ⚙️ Architecture: The IPO Model

```
USER INPUT  →  SANITIZATION  →  DICTIONARY LOOKUP  →  OUTPUT
   (raw)         (clean)            (O(1) match)       (reply)
```

| Phase | What happens |
|-------|-------------|
| **Input** | Raw text from the user |
| **Sanitization** | `.lower().strip()` - removes case & whitespace issues |
| **Process** | Dictionary `.get()` lookup - O(1) constant time |
| **Output** | Matched response or fallback message |

---

## 🏗️ Key Concepts Used

| Concept | Implementation |
|---------|---------------|
| Continuous loop | `while True:` - the chatbot heartbeat |
| Input sanitization | `.lower().strip()` |
| Knowledge base | Python dictionary (hash map) |
| O(1) lookup | `dict.get(key, fallback)` |
| Exit strategy | `break` on kill command |
| Fallback response | Default value in `.get()` |

### Why dictionary over if-elif?

| Approach | Time Complexity | Scalability |
|----------|----------------|-------------|
| if-elif ladder | O(n) - slower as rules grow | Low - messy to maintain |
| Dictionary `.get()` | O(1) - instant regardless of size | High - just add a new line |

---

## 📋 Project Requirements Checklist

- [x] Continuous `while` loop (input heartbeat)
- [x] Input sanitization (case + whitespace)
- [x] Knowledge base with 5+ intents (20+ included)
- [x] Fallback response for unknown inputs
- [x] Clean exit with `break` command

---

## 🚀 How to Run

1. Open [Google Colab](https://colab.research.google.com)
2. Upload the contents of `chatbot.ipynub`
3. Press `Shift + Enter`
4. Type in the input box that appears below the cell

---

## 💬 Sample Conversation

```
===================================================
  DBot : Rule-Based AI Chatbot
===================================================
Bot: Hello! I'm DBot 
Bot: Type 'help' to see what I can do, or 'exit' to quit.
---------------------------------------------------
You: hello
Bot: Hey there! I'm DBot. How can I help you today?

You: what is ai
Bot: AI (Artificial Intelligence) is the simulation of human intelligence by machines.

You: what is machine learning
Bot: Machine Learning is a subset of AI where systems learn from data instead of explicit rules.

You: xyz random stuff
Bot: I don't understand that yet. Type 'help' to see what I know!

You: exit
Bot: Goodbye! See you! 🚀
===================================================
```

---
