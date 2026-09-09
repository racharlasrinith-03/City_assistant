# 🤖 Agentic AI City Assistant

An **Agentic AI City Assistant** built with **LangChain, Groq, Tavily, and OpenWeatherMap**. The assistant can understand a user's request, decide which tool is useful, ask for human approval before calling a tool, and return the result through a conversational command-line interface.

## 🚀 Project Overview

Finding current city information often requires using multiple websites or applications. This project demonstrates how an AI agent can combine multiple tools behind a single conversational interface.

The assistant currently provides:

- 🌤️ **Current weather information** for a city
- 📰 **Latest city news**
- 🌐 **General web search** for current information
- 🤖 **Agent-based tool selection**
- 👤 **Human approval before every tool call**
- 💬 **Interactive command-line conversation**

## 🏗️ Architecture

```text
                    ┌──────────────────────┐
                    │      User Query      │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   LangChain Agent    │
                    │      + Groq LLM      │
                    └──────────┬───────────┘
                               │
                    Selects appropriate tool
                               │
                               ▼
                    ┌──────────────────────┐
                    │  Human Approval      │
                    │   yes / no           │
                    └──────────┬───────────┘
                               │
             ┌─────────────────┼─────────────────┐
             ▼                 ▼                 ▼
      ┌─────────────┐   ┌─────────────┐   ┌─────────────┐
      │   Weather   │   │    News     │   │ Web Search  │
      │ OpenWeather │   │   Tavily    │   │   Tavily    │
      └─────────────┘   └─────────────┘   └─────────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Agent Response     │
                    └──────────────────────┘
```

## 🧰 Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| LangChain | Agent and tool orchestration |
| LangChain Groq | Groq LLM integration |
| Groq | Large language model inference |
| Tavily | News and web search |
| OpenWeatherMap | Current weather data |
| Requests | Weather API requests |
| Rich | Improved terminal output |
| Google Colab | Development environment |

## 🔑 API Keys Required

The notebook uses Google Colab's `userdata` to access API keys.

Configure these secrets in your Colab environment:

```text
GROQ_API_KEY
TAVILY_API_KEY
OPENWEATHER_API_KEY
```

### How to add API keys in Google Colab

1. Open the notebook in Google Colab.
2. Open **Secrets** from the left sidebar.
3. Add the three keys listed above.
4. Give the notebook access to each secret.
5. Run the notebook.

**Never commit API keys or `.env` files containing secrets to GitHub.**

## 📦 Installation

The notebook installs the required packages using:

```bash
pip install -U langchain langchain-groq tavily-python requests rich
```

If running locally, install the same dependencies in your virtual environment.

## ▶️ How to Run

### Option 1 — Google Colab

1. Upload/open `Agentic_AI _City_Assistant.ipynb` in Google Colab.
2. Add the required API keys to Colab Secrets.
3. Run the cells from top to bottom.
4. Start chatting with the assistant in the terminal-style input.

### Option 2 — Local Python Environment

Create and activate a virtual environment:

```bash
python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

Linux/macOS:

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -U langchain langchain-groq tavily-python requests rich
```

Then configure the API keys according to your environment and run the Python implementation.

## 💬 Example Queries

Try questions such as:

```text
What is the weather in Hyderabad?
```

```text
Give me the latest news about Hyderabad.
```

```text
What are the latest developments in Hyderabad?
```

```text
Search the web for current information about Hyderabad.
```

The agent determines whether it needs the weather tool, news tool, or general web-search tool.

## 🛠️ Tools

### 1. Weather Tool

`get_weather(city)`

Uses the OpenWeatherMap API to retrieve the current weather for an Indian city.

The response includes:

- Weather description
- Temperature in Celsius

### 2. News Tool

`get_news(city)`

Uses Tavily to search for recent news related to a city and returns titles, URLs, and snippets.

### 3. Web Search Tool

`web_search(query)`

Uses Tavily's advanced search to retrieve current/general information from the internet.

## 👤 Human-in-the-Loop Safety

One of the main features of this project is **human approval before tool execution**.

Before the agent calls a tool, the program asks:

```text
Agent wants to call 'get_weather'. Approve? (yes/no):
```

If the user enters:

```text
yes
```

the tool is executed.

If the user enters:

```text
no
```

the tool call is denied.

This demonstrates a simple **human-in-the-loop agent architecture**, where the AI does not automatically execute external actions without user approval.

## 🧠 Agent Workflow

The workflow is:

1. User enters a question.
2. The LangChain agent receives the question.
3. Groq provides the reasoning/model response.
4. The agent determines whether a tool is required.
5. The human-approval middleware asks for permission.
6. If approved, the selected tool is executed.
7. The tool returns information.
8. The agent generates the final response.
9. The response is displayed to the user.

## 📁 Project Structure

A recommended GitHub structure is:

```text
Agentic-AI-City-Assistant/
│
├── Agentic_AI_City_Assistant.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

Example `requirements.txt`:

```text
langchain
langchain-groq
tavily-python
requests
rich
```

Example `.gitignore`:

```text
.env
__pycache__/
*.pyc
venv/
.ipynb_checkpoints/
```

## 🔮 Future Improvements

This project can be extended with:

- 🗺️ Maps and location search
- 🚦 Traffic information
- 🍽️ Restaurant recommendations
- 🏨 Hotel search
- 🎬 Local events and entertainment
- ✈️ Flight information
- 🚆 Public transportation information
- 💰 Local cost-of-living information
- 🌦️ Multi-day weather forecasts
- 🧠 Conversation memory
- 🔧 More specialized agents/tools
- 🌐 Web or mobile interface
- 🔐 More granular tool permissions

## 🎯 Learning Outcomes

This project demonstrates practical concepts in **Generative AI and Agentic AI**, including:

- LLM integration
- LangChain agents
- Tool calling
- API integration
- Web search
- Agent middleware
- Human-in-the-loop approval
- Interactive AI applications
- Real-time information retrieval

## ⚠️ Notes

- Weather information depends on the OpenWeatherMap API.
- News and web-search results depend on Tavily.
- Internet connectivity is required for external API calls.
- API usage may be subject to the providers' rate limits and terms.
- The current implementation is designed primarily as a learning/demo project.

## 👨‍💻 Project

**Agentic AI City Assistant**

Built as a practical demonstration of how LLM-powered agents can interact with external tools and APIs to provide useful, real-time city information.

⭐ If you find this project useful, consider starring the repository!
