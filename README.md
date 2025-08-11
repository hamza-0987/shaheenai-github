

<div align="center">
<img src="https://github.com/hamza-0987/shaheenai-github/blob/main/shaheenai.png" alt="ShaheenAI Logo" width="300" />
</div>

<div align="center">
<a href="https://pypi.org/project/shaheenai" target="_blank">
<img src="https://img.shields.io/pypi/v/shaheenai" alt="PyPI version" />
</a>
</div>
# ShaheenAI: The Flexible, Multi-LLM Agent-Oriented Library 🦅



ShaheenAI is a powerful and flexible Python library for building intelligent, agent-oriented applications. It provides a robust framework to easily create agents that can leverage multiple Large Language Models (LLMs), perform self-reflection, use external tools, and manage complex tasks like research planning.

-----

## 🌟 Key Features

  - 🧠 **Multi-LLM Support:** Seamlessly integrate with various LLM providers like **OpenAI, Anthropic, Ollama, and Google Gemini** via a modular plugin architecture.
  - 🔄 **Self-Reflection & Memory:** Agents can track conversation history and reflect on their own responses to improve accuracy and relevance.
  - 🛠️ **Tool Invocation:** Effortlessly enable your agents to interact with the real world using built-in tools for **web search, weather, calculations**, and more.
  - 📋 **Research Planning:** Advanced features for managing research projects, including milestones, bibliography, and task planning.
  - 💻 **Advanced Coding Assistant:** Specialized support for Python and multi-language programming tasks.
  - 🚀 **Asynchronous & Synchronous Operations:** Choose the best approach for your application with both sync and async methods.
  - 🌐 **UI Integrations:** Easily build interactive UIs for your agents with optional integrations for **Streamlit** and **Chainlit**.
  - ⚙️ **Configurable:** Define agents and their behaviors programmatically or through simple **YAML playbooks**.

-----

## ⚡️ Getting Started

### Prerequisites

  - **Python 3.10** or higher

### Installation

Install ShaheenAI and its core dependencies with `pip`:

```bash
pip install shaheenai
```

To enable specific LLM providers or tools, use the optional extras. For example, to use the OpenAI and Anthropic providers:

```bash
pip install "shaheenai[openai,anthropic]"
```

For a comprehensive installation with all supported extras, you can use:

```bash
pip install "shaheenai[all]"
```

-----

## 🚀 Usage Examples

### 1\. Basic Agent Creation

Create a simple agent with a specific role.

```python
from shaheenai import Agent

# Create a simple agent specialized in Python
agent = Agent(
    instructions="You are a helpful AI assistant specializing in Python programming.",
    llm="openai/gpt-3.5-turbo"
)

# Ask a question and get a response
response = agent.start("Explain list comprehensions in Python")
print(response)
```

### 2\. Agent with Conversation Memory

Give your agent the ability to remember previous turns in a conversation.

```python
from shaheenai import Agent

# Create an agent with memory enabled
agent = Agent(
    instructions="You are a knowledgeable tutor.",
    llm="openai/gpt-4",
    memory=True
)

# The agent will remember the context of the previous questions
print(agent.start("What is machine learning?"))
print(agent.start("Can you give me an example?"))  # Remembers the previous topic
print(agent.start("How does it relate to AI?"))    # Continues the conversation
```

### 3\. Agent with Self-Reflection

Enable the agent to critique and refine its own output for better quality.

```python
from shaheenai import Agent

# Create an agent with self-reflection capabilities
agent = Agent(
    instructions="You are a research assistant that provides accurate information.",
    llm="anthropic/claude-3-sonnet",
    self_reflection=True,
    max_iterations=2  # The agent will try to improve its response up to 2 times
)

# The agent will reflect on and improve its initial response
response = agent.start("Explain quantum computing and its potential applications")
print(response)
```

### 4\. Multi-LLM Provider Support

Easily switch between different LLM providers and models.

```python
from shaheenai import Agent

# Create agents for different providers
openai_agent = Agent(llm="openai/gpt-4")
anthropic_agent = Agent(llm="anthropic/claude-3-opus")
ollama_agent = Agent(llm="ollama/llama2")
google_agent = Agent(llm="google/gemini-1.5-pro")

# Use any agent you've created
response = openai_agent.start("Hello, how are you?")
print(response)
```

-----

## ⚙️ Real API Tool Integration (MCP)

ShaheenAI uses the **Model Context Protocol (MCP)** to allow agents to interact with external tools and APIs. Several powerful tools are built-in and ready to use.

### Built-in Tools

  - 🌤️ **Weather Tool (`get_weather`)**: Fetches real-time weather information using the OpenWeatherMap API.
  - 🔍 **Web Search Tool (`web_search`)**: Conducts real-time web searches using Brave Search, SerpAPI, or DuckDuckGo as a fallback.
  - 🧮 **Calculator Tool (`calculate`)**: Evaluates mathematical expressions.

### Using Tools in an Agent

To use these tools, you need to configure the relevant API keys as environment variables.

```bash
# Windows PowerShell
$env:OPENWEATHER_API_KEY='your-openweathermap-key'
$env:BRAVE_API_KEY='your-brave-search-key'

# Linux/Mac
export OPENWEATHER_API_KEY='your-openweathermap-key'
export BRAVE_API_KEY='your-brave-search-key'
```

Once configured, you can include the tool names when creating an `Agent`.

```python
import os
from shaheenai import Agent

# Set up API keys
os.environ['OPENWEATHER_API_KEY'] = 'your-openweathermap-key'
os.environ['BRAVE_API_KEY'] = 'your-brave-search-key'

# Create agent with real API tools
agent = Agent(
    instructions="I can help with weather, web searches, and calculations using real APIs.",
    llm="openai/gpt-3.5-turbo",
    tools=["get_weather", "web_search", "calculate"]
)

# Get real weather data
weather_report = agent.start("What's the weather in New York?")
print(weather_report)

# Perform a real web search
search_results = agent.start("Search for latest AI developments")
print(search_results)

# Use the built-in calculator
math_result = agent.start("Calculate 25 * 4 + 18")
print(math_result)
```

-----

## 📈 Research Planning & Management

ShaheenAI offers a dedicated suite of tools for managing research projects.

### Research Project Management

```python
from shaheenai.research import ResearchProject
from datetime import datetime

project = ResearchProject(
    name="AI Code Generation Study",
    description="Research on automatic code generation using LLMs",
    start_date=datetime(2024, 2, 1)
)

# Add and manage project milestones
project.add_milestone("Literature Review", "Comprehensive review of existing techniques", datetime(2024, 3, 15))
project.complete_milestone("Literature Review")

print(f"Progress: {project.get_progress():.1f}%")

# Generate a detailed project report
report = project.generate_report()
print(report)
```

### Bibliography Management

```python
from shaheenai.research import BibliographyManager

bib_manager = BibliographyManager()

# Add a research paper entry
bib_manager.add_entry({
    "type": "article",
    "key": "chen2021evaluating",
    "title": "Evaluating Large Language Models Trained on Code",
    "author": "Chen, Mark and others",
    "year": "2021"
})

# Export the bibliography to a BibTeX file
bib_manager.export_bibtex("references.bib")
```

-----

## 🤝 Contributing

Contributions are highly encouraged\! If you're interested in improving ShaheenAI, please read the [contribution guidelines](https://www.google.com/search?q=CONTRIBUTING.md) and feel free to open a pull request or issue.

-----

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](https://www.google.com/search?q=LICENSE) file for details.

```
```


