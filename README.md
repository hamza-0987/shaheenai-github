![ShaheenAI Logo](https://github.com/hamza-0987/shaheenai-github/blob/main/shaheenai.png)

# ShaheenAI

ShaheenAI is a Python framework for creating multi-agent systems with multi-LLM support. It simplifies AI development by integrating popular LLMs and providing flexible APIs for building, orchestrating, and deploying intelligent agents.

---

## 🚀 Features
- **Multi-LLM Support** – OpenAI, Groq, Gemini, Claude, etc.
- **Agent Orchestration** – Create, connect, and manage multiple AI agents.
- **CLI Tool** – Quick setup and execution from the command line.
- **Streaming Support** – Real-time response streaming.
- **Customizable Pipelines** – Easily integrate your own logic.
- **Built-in Tools** – Search, math, scraping, file handling, etc.
- **Chainlit & Streamlit Support** – For fast prototyping and UI building.

---

## 📦 Installation
```bash
pip install shaheenai
```

---

## 🛠️ Usage Example
```python
from shaheenai import Agent, Orchestrator

agent1 = Agent(model="gpt-4", role="Researcher")
agent2 = Agent(model="gemini-pro", role="Writer")

orchestrator = Orchestrator([agent1, agent2])
response = orchestrator.run("Write a blog post on AI trends in 2025")
print(response)
```

---

## 🗂️ Project Structure
```
shaheenai/
│   __init__.py
│   agents.py
│   orchestrator.py
│   tools/
│   └── __init__.py
```

---

## 🖥️ CLI Usage
```bash
shaheenai run --prompt "Explain quantum computing"
```

---

## 🤝 Contributing
1. Fork the repo
2. Create a branch: `git checkout -b feature-name`
3. Commit changes: `git commit -m 'Added new feature'`
4. Push and submit PR

---

## 📜 License
MIT License © 2025 Engr. Hamza
