<!doctype html>
    </section>

    <section class="grid">
      <div>
        <h3>Installation</h3>
        <p class="pill">Prerequisites: Python 3.10+</p>
        <pre><code># Core
pip install shaheenai

# Provider / UI extras (install only what you need)
# Examples
pip install "shaheenai[openai]"
pip install "shaheenai[chainlit]"
pip install "shaheenai[streamlit]"
pip install "shaheenai[cohere]"
# Everything
pip install "shaheenai[all]"
</code></pre>
      </div>

      <div>
        <h3>Environment variables</h3>
        <pre><code># Windows (PowerShell)
$env:OPENAI_API_KEY = "your-openai-key"
$env:GOOGLE_API_KEY = "your-gemini-key"   # or $env:GEMINI_API_KEY
$env:OPENROUTER_API_KEY = "your-openrouter-key"
$env:COHERE_API_KEY = "your-cohere-key"
# Built-in tools
$env:OPENWEATHER_API_KEY = "your-openweathermap-key"
$env:BRAVE_API_KEY = "your-brave-search-key"
$env:SERPAPI_KEY = "your-serpapi-key"

# macOS / Linux
export OPENAI_API_KEY="your-openai-key"
export GOOGLE_API_KEY="your-gemini-key"
export OPENROUTER_API_KEY="your-openrouter-key"
export COHERE_API_KEY="your-cohere-key"
export OPENWEATHER_API_KEY="your-openweathermap-api-key"
export BRAVE_API_KEY="your-brave-search-key"
export SERPAPI_KEY="your-serpapi-key"
</code></pre>
      </div>

      <div class="full">
        <h3>Quickstart</h3>
        <p><strong>Minimal agent</strong></p>
        <pre><code>from shaheenai import Agent

agent = Agent(
    instructions="You are a helpful AI assistant specializing in Python.",
    llm="openai/gpt-3.5-turbo"
)

print(agent.start("Explain list comprehensions in Python"))
</code></pre>

        <p><strong>Async usage</strong></p>
        <pre><code>import asyncio
from shaheenai import Agent

async def main():
    agent = Agent(instructions="You are helpful.", llm="openai/gpt-3.5-turbo")
    resp = await agent.astart("What are the benefits of async programming?")
    print(resp)

asyncio.run(main())
</code></pre>

        <p><strong>Memory & self‑reflection</strong></p>
        <pre><code>from shaheenai import Agent

agent = Agent(
    instructions="You are a knowledgeable tutor.",
    llm="openai/gpt-4o-mini",
    memory=True,
    self_reflection=True,
    max_iterations=2,
)

print(agent.start("What is machine learning?"))
print(agent.start("Give me a simple example."))
</code></pre>

        <p><strong>Identity awareness</strong></p>
        <pre><code>from shaheenai import Agent

agent = Agent()
print(agent.start("Who are you?"))
# => "I am Shaheen AI developed by Engr. Hamza, an enthusiastic AI engineer."
</code></pre>
      </div>

      <div>
        <h3>Using Tools (MCP-style registry)</h3>
        <p>Register your own tools using the <code>@tool</code> decorator. Built-ins include <code>get_weather</code>, <code>web_search</code>, and <code>calculate</code>.</p>
        <pre><code>from shaheenai import Agent, tool

@tool(description="Calculate the area of a rectangle")
def area(width: float, height: float) -> str:
    return str(width * height)

agent = Agent(
    instructions="You can use tools to help with tasks.",
    llm="openai/gpt-3.5-turbo",
    tools=["area", "get_weather", "web_search", "calculate"],
)

print(agent.start("Calculate area for width=5 and height=3"))
</code></pre>
      </div>

      <div>
        <h3>Choosing providers</h3>
        <p>Provider strings follow <code>provider/model</code>. The factory looks up API keys from environment variables.</p>
        <pre><code># Examples
openai/gpt-4o-mini
openai/gpt-3.5-turbo
google/gemini-1.5-flash
cohere/command-r-plus
openrouter/openai/gpt-4o
# Optional / experimental: anthropic/claude-3-5-sonnet, groq/llama-3.1-8b-instant, ollama/llama2
</code></pre>
      </div>

      <div>
        <h3>CLI</h3>
        <pre><code># Run a YAML playbook
shaheenai run agents.yaml
shaheenai run agents.yaml --llm openai/gpt-4o-mini --temperature 0.8

# Auto mode
shaheenai auto "Write a summary about AI" --llm openai/gpt-3.5-turbo

# List providers
shaheenai providers

# Start a UI
shaheenai ui --chainlit --port 8000
shaheenai ui --streamlit --port 8501

# Bootstrap
shaheenai init
</code></pre>
      </div>

      <div class="full">
        <h3>Built-in Tool Configuration</h3>
        <p>Weather (OpenWeatherMap) and web search use environment keys. If no keys are set, web search falls back to DuckDuckGo Instant Answers.</p>
        <pre><code># OpenWeatherMap
$env:OPENWEATHER_API_KEY = "your-openweathermap-api-key"

# Web search (recommended)
$env:BRAVE_API_KEY = "your-brave-search-api-key"
# Alternative
$env:SERPAPI_KEY = "your-serpapi-key"
