# Human-in-the-Loop Research Agent

A sophisticated research agent built with LangGraph that incorporates human feedback into the research process. This agent can pause execution to ask for clarification, adapt its research strategy based on human input, and provide comprehensive research results.

## 🚀 Features

- **Interactive Research**: The agent can pause and ask for human feedback during the research process
- **Web Search Integration**: Uses Tavily API for comprehensive web searches
- **Structured Output**: Provides well-organized research results with analysis, strategy, findings, and next steps
- **State Management**: Maintains conversation state and research context across interactions
- **Flexible Query Handling**: Can handle complex research questions and adapt its approach based on user needs

## 🏗️ Architecture

The project is built using:
- **LangGraph**: For orchestrating the research workflow
- **LangChain**: For agent creation and tool integration
- **OpenAI GPT-4o-mini**: As the reasoning engine
- **Tavily**: For web search capabilities
- **Poetry**: For dependency management

### Project Structure

```
human_feedback/
├── config.py              # API key configuration
├── graph.py               # LangGraph workflow definition
├── main.ipynb            # Example usage notebook
├── researcher_state.py    # State management for the research agent
├── researcher_agent/
│   ├── agent.py          # Main research agent implementation
│   ├── prompt.py         # System prompt for the agent
│   ├── tools.py          # Tool definitions (web search, human feedback)
│   └── output_parser.py  # Response parsing and structuring
└── pyproject.toml        # Project dependencies and metadata
```

## 🛠️ Setup

### Prerequisites

- Python 3.12 or higher
- Poetry (for dependency management)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd human_feedback
   ```

2. **Install dependencies**
   ```bash
   poetry install
   ```

3. **Set up environment variables**
   
   Create a `.env` file in the project root with:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   TAVILY_API_KEY=your_tavily_api_key_here
   ```

4. **Activate the virtual environment**
   ```bash
   poetry shell
   ```

## 🔧 Configuration

### API Keys Required

- **OpenAI API Key**: For GPT-4o-mini model access
- **Tavily API Key**: For web search functionality

You can get these keys from:
- OpenAI: https://platform.openai.com/api-keys
- Tavily: https://tavily.com/

## 📖 Usage

### Basic Usage

```python
from graph import graph

# Start a research session
query = "What is Agentic AI?"
config = {"configurable": {"thread_id": "123"}}
result = graph.invoke({"messages": query}, config)
```

### Interactive Research with Human Feedback

```python
from langgraph.types import Command

# Provide human feedback to guide the research
feedback = """
Context: I'm interested in using Agentic AI for building systems that can interact with humans.
Definition: I need a clear technical definition.
Examples: Practical system examples using LangGraph.
Ethics: I'm also thinking about ethical concerns around safe behavior.
"""

# Resume the research with the feedback
graph.invoke(Command(resume={"messages": "definition"}), config)
```

### Running the Example Notebook

1. Start Jupyter with the poetry environment:
   ```bash
   poetry run jupyter notebook
   ```

2. Open `main.ipynb` and run the cells to see the agent in action.

## 🔄 How It Works

1. **Query Analysis**: The agent first analyzes the research query to understand what information is needed
2. **Human Feedback Request**: Before starting research, the agent asks for human input to clarify:
   - User's specific needs or context
   - Research scope or direction
   - Interpretation of ambiguous terms
3. **Research Strategy**: Based on human feedback, the agent plans its research approach
4. **Web Search**: Executes multiple targeted searches using Tavily
5. **Synthesis**: Combines information from multiple sources
6. **Structured Output**: Presents findings in a clear, organized format

## 🎯 Research Process

The agent follows a systematic approach:

1. **Analyze the Query**: Understand the main topic and specific information needed
2. **Ask for Human Feedback**: Use `get_human_input` to clarify user needs
3. **Plan Research Strategy**: Determine search queries and research angles
4. **Execute and Synthesize**: Perform searches and combine information
5. **Present Results**: Provide structured findings with analysis and next steps

## 📊 Output Structure

The agent provides research results in a structured format:

- **Analysis**: Brief breakdown of the query
- **Strategy**: Research approach taken
- **Findings**: Synthesized information from multiple sources
- **Next Steps**: Additional research suggestions if needed

## 🤝 Human-in-the-Loop Features

- **Clarification Requests**: Agent can ask for clarification when queries are ambiguous
- **Adaptive Research**: Research strategy adapts based on human feedback
- **Context Preservation**: Maintains conversation state across interactions
- **Iterative Refinement**: Can refine research based on ongoing feedback

## 🧪 Example Research Session

The included `main.ipynb` demonstrates a complete research session:

1. Initial query about "Agentic AI"
2. Human feedback providing context and specific interests
3. Resumed research with focused direction
4. Structured output with comprehensive findings

## 🔧 Development

### Adding New Tools

To add new research tools, modify `researcher_agent/tools.py`:

```python
@tool
def your_new_tool(param: str) -> str:
    """Description of what your tool does."""
    # Your tool implementation
    return result
```

### Modifying the Agent Behavior

Edit `researcher_agent/prompt.py` to change the agent's behavior and research approach.

### State Management

The `ResearcherState` class in `researcher_state.py` defines the state structure. Modify as needed for additional state tracking.

## 📝 License

[Add your license information here]

## 🤝 Contributing

[Add contribution guidelines here]

## 📞 Support

[Add support contact information here] 