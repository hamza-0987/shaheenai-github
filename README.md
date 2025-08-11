<div align="center">
  <h1>🦅 ShaheenAI</h1>
  <p><i>Multi-Agent AI Framework with Multi-LLM Support</i></p>
</div>

---

## 📖 Overview
ShaheenAI is a powerful, flexible Python framework designed for creating advanced **multi-agent AI systems** with **multi-LLM support**. It allows developers to easily integrate models like **OpenAI, Groq, Gemini**, and more, while also supporting interactive UIs via **Streamlit** and **Chainlit**.

With ShaheenAI, you can:
- Build collaborative AI agents.
- Orchestrate workflows across multiple LLMs.
- Deploy interactive AI apps quickly.

---

## 🚀 Installation
```bash
pip install shaheenai
```

---

## ⚡ Quick Start
```python
from shaheenai import Agent, AgentSystem

# Create Agents
agent1 = Agent(name="Researcher", model="gpt-4")
agent2 = Agent(name="Summarizer", model="gemini-pro")

# Create Multi-Agent System
system = AgentSystem([agent1, agent2])

# Run Task
response = system.run("Find latest AI trends and summarize")
print(response)
```

---

## 📂 Features
- **Multi-LLM Support** – OpenAI, Groq, Gemini, and more.
- **Multi-Agent Collaboration** – Define multiple agents with specific roles.
- **UI Integration** – Supports Streamlit and Chainlit.
- **Extensible Architecture** – Add custom models or agents.
- **Workflow Orchestration** – Sequential and parallel task execution.

---

## 🛠 Configuration
You can set API keys as environment variables:
```bash
export OPENAI_API_KEY="your_openai_key"
export GROQ_API_KEY="your_groq_key"
export GEMINI_API_KEY="your_gemini_key"
```

---

## 📜 License
MIT © 2025 Engr. Hamza

