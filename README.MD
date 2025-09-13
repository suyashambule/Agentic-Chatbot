# Agentic Chatbot with LangGraph

An intelligent, multi-agent conversational AI system built with LangGraph and LangChain that can perform complex reasoning, tool usage, and autonomous task execution. This chatbot leverages the power of agentic AI to provide dynamic, context-aware responses and can interact with various external services and APIs.

## 🤖 About the Project

This project implements an agentic chatbot using LangGraph's state machine capabilities to create sophisticated AI agents that can:
- Reason through complex problems step-by-step
- Use external tools and APIs dynamically
- Maintain conversation context and state
- Execute multi-step workflows autonomously
- Provide accurate, real-time information through web search

## ✨ Key Features

- **🧠 Agentic AI**: Self-directed agents that can plan and execute complex tasks
- **🔗 Tool Integration**: Seamless integration with external APIs and services
- **🌐 Web Search**: Real-time information retrieval via Tavily search
- **💬 Multi-Modal Support**: Support for various LLM providers (OpenAI, Groq)
- **📈 State Management**: Advanced conversation state tracking with LangGraph
- **🚀 Streamlit UI**: Interactive web interface for easy interaction
- **📊 Vector Search**: FAISS-powered semantic search capabilities
- **🔄 Workflow Orchestration**: Complex multi-agent workflows
- **📝 Context Retention**: Persistent conversation memory

## 🛠️ Architecture

```
┌───────────────┐
│  Streamlit UI   │
│  (Frontend)     │
└───────┬────────┘
        │
        │
┌───────┴────────┐
│   LangGraph      │      ┌────────────────┐
│   (Agent Core)   │──────│  External APIs  │
│                 │      │  - Tavily       │
│  ┌────────────┐ │      │  - OpenAI       │
│  │   Agent 1   │ │      │  - Groq         │
│  │ (Reasoning) │ │      └────────────────┘
│  └────────────┘ │
│                 │
│  ┌────────────┐ │      ┌────────────────┐
│  │   Agent 2   │ │──────│   FAISS DB      │
│  │  (Tools)    │ │      │  (Vector Store)  │
│  └────────────┘ │      └────────────────┘
└─────────────────┘
```

## 🛠️ Project Structure

```
Agentic-Chatbot/
│
├── src/
│   ├── __init__.py
│   └── langgraph/
│       ├── __init__.py
│       └── main.py              # Core LangGraph implementation
│
├── app.py                       # Streamlit application
├── requirements.txt             # Python dependencies
├── README.MD                    # Project documentation
└── .gitignore                   # Git ignore file
```

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- Git
- API keys for:
  - OpenAI (optional)
  - Groq (optional)
  - Tavily (for web search)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/suyashambule/Agentic-Chatbot.git
   cd Agentic-Chatbot
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   Create a `.env` file in the root directory:
   ```bash
   # OpenAI (optional)
   OPENAI_API_KEY=your_openai_api_key
   
   # Groq (optional)
   GROQ_API_KEY=your_groq_api_key
   
   # Tavily (for web search)
   TAVILY_API_KEY=your_tavily_api_key
   ```

5. **Run the application**
   ```bash
   streamlit run app.py
   ```

   The application will be available at `http://localhost:8501`

## 💻 Usage

### Basic Conversation

1. Launch the Streamlit app
2. Type your message in the chat input
3. The agentic chatbot will:
   - Analyze your request
   - Determine if external tools are needed
   - Execute the appropriate workflow
   - Provide a comprehensive response

### Example Interactions

**Information Retrieval:**
```
User: "What are the latest developments in AI?"
Agent: *Uses web search tool* → *Analyzes results* → *Provides summary*
```

**Complex Reasoning:**
```
User: "Plan a 3-day itinerary for Tokyo with a budget of $500"
Agent: *Searches for attractions* → *Calculates costs* → *Creates detailed plan*
```

**Multi-step Problem Solving:**
```
User: "Help me understand quantum computing and its applications"
Agent: *Searches for current info* → *Explains concepts* → *Provides examples*
```

## 🧑‍💻 Agent Capabilities

### Core Agents

1. **Reasoning Agent**
   - Analyzes complex queries
   - Plans multi-step solutions
   - Maintains logical consistency

2. **Tool Agent**
   - Web search via Tavily
   - API interactions
   - Data processing

3. **Memory Agent**
   - Conversation history
   - Context retention
   - Semantic search

### Available Tools

- **🔍 Web Search**: Real-time information via Tavily
- **🧠 LLM Providers**: OpenAI GPT, Groq Llama
- **📋 Vector Storage**: FAISS for semantic search
- **📊 Analytics**: Conversation analysis

## 🔧 Configuration

### LLM Provider Setup

**OpenAI Configuration:**
```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(
    model="gpt-4",
    temperature=0.7,
    api_key="your-api-key"
)
```

**Groq Configuration:**
```python
from langchain_groq import ChatGroq

llm = ChatGroq(
    model="llama2-70b-4096",
    temperature=0.7,
    api_key="your-api-key"
)
```

### Agent Customization

```python
# Customize agent behavior
from langgraph import StateGraph

# Define custom states and transitions
def create_agent_workflow():
    workflow = StateGraph(state_schema)
    workflow.add_node("reasoning", reasoning_agent)
    workflow.add_node("tools", tool_agent)
    workflow.add_edge("reasoning", "tools")
    return workflow
```

## 📊 Advanced Features

### Custom Tool Integration

```python
from langchain.tools import tool

@tool
def custom_calculator(expression: str) -> str:
    """Evaluate mathematical expressions"""
    try:
        result = eval(expression)
        return f"Result: {result}"
    except Exception as e:
        return f"Error: {e}"
```

### State Management

```python
from typing import TypedDict
from langgraph import StateGraph

class AgentState(TypedDict):
    messages: list
    current_tool: str
    search_results: list
    reasoning_step: int
```

### Memory Integration

```python
# Vector store setup for long-term memory
from langchain_community.vectorstores import FAISS
from langchain.embeddings import OpenAIEmbeddings

vectorstore = FAISS.from_texts(
    texts=conversation_history,
    embedding=OpenAIEmbeddings()
)
```

## 📊 Dependencies

The project uses these key libraries:

- **🤖 LangChain**: AI application framework
- **🔗 LangGraph**: Agent workflow orchestration
- **🌐 Tavily**: Web search and information retrieval
- **📈 FAISS**: Vector similarity search
- **🚀 Streamlit**: Web application framework
- **🧠 Multiple LLMs**: OpenAI, Groq support

## 📝 API Reference

### Core Methods

```python
# Initialize agent
agent = create_agentic_chatbot(
    llm_provider="openai",  # or "groq"
    search_tool="tavily",
    vector_store="faiss"
)

# Process user input
response = agent.invoke({
    "messages": ["user_message"],
    "config": {"temperature": 0.7}
})

# Get conversation history
history = agent.get_conversation_history()
```

## 🌐 Deployment

### Local Development

```bash
streamlit run app.py --server.port 8501
```

### Docker Deployment

```dockerfile
FROM python:3.9-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 8501
CMD ["streamlit", "run", "app.py", "--server.headless", "true"]
```

### Cloud Deployment

**Streamlit Cloud:**
1. Push to GitHub
2. Connect to Streamlit Cloud
3. Set environment variables
4. Deploy automatically

## 📊 Monitoring & Logging

```python
import logging
from langchain.callbacks import get_openai_callback

# Set up logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

# Track API usage
with get_openai_callback() as cb:
    response = agent.invoke(message)
    logger.info(f"Tokens used: {cb.total_tokens}")
```

## 🐛 Troubleshooting

### Common Issues

**API Key Errors:**
```bash
Error: Incorrect API key provided
```
- Verify API keys in `.env` file
- Check key permissions and quotas

**Dependency Issues:**
```bash
ModuleNotFoundError: No module named 'langgraph'
```
- Update pip: `pip install --upgrade pip`
- Reinstall requirements: `pip install -r requirements.txt`

**Streamlit Issues:**
```bash
StreamlitAPIException
```
- Clear Streamlit cache: `streamlit cache clear`
- Restart the application

## 🚀 Future Enhancements

- [ ] **Multi-Agent Collaboration**: Advanced agent-to-agent communication
- [ ] **Plugin System**: Easy integration of custom tools
- [ ] **Voice Interface**: Speech-to-text and text-to-speech
- [ ] **Document Analysis**: PDF and document processing
- [ ] **API Endpoints**: RESTful API for external integrations
- [ ] **Database Integration**: Persistent data storage
- [ ] **Real-time Collaboration**: Multi-user chat sessions
- [ ] **Advanced Analytics**: Conversation insights and metrics

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines

- Follow PEP 8 style guidelines
- Add unit tests for new features
- Update documentation
- Test with multiple LLM providers

## 📚 Technologies Used

- **🐍 Python**: Core programming language
- **🤖 LangChain**: AI framework
- **🔗 LangGraph**: Agent orchestration
- **🚀 Streamlit**: Web interface
- **🌐 Tavily**: Web search API
- **📈 FAISS**: Vector database
- **🧠 OpenAI/Groq**: LLM providers

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **LangChain Team**: For the excellent framework
- **LangGraph**: For agent workflow capabilities
- **Streamlit**: For the amazing web framework
- **OpenAI & Groq**: For powerful language models
- **Tavily**: For real-time search capabilities

## 📞 Contact

- **GitHub**: [suyashambule](https://github.com/suyashambule)
- **Project Link**: [Agentic-Chatbot](https://github.com/suyashambule/Agentic-Chatbot)

For questions, issues, or contributions, please open an issue in the repository.

---

*Experience the future of conversational AI with intelligent agents! 🤖✨*
