# UdaPlay - AI Game Research Agent Project

## Project Overview

UdaPlay is an AI-powered research agent for the video game industry. This project implements a sophisticated AI agent capable of answering questions about video games using both local knowledge (RAG) and web searches.

## Project Structure

### Part 1: Offline RAG (Retrieval-Augmented Generation)

**Status: Implemented in `Udaplay_01_starter_project.ipynb`**

We have built a Vector Database using ChromaDB to store and retrieve video game information efficiently.

**Implementation Details:**

- **Database:** ChromaDB (Persistent Client)
- **Embeddings:** OpenAI Embedding Function
- **Data Source:** JSON files in `games/` directory
- **Schema:** Each game document indexes Name, Platform, Genre, Publisher, Description, and Year of Release.

### Part 2: AI Agent Development

**Status: Implemented in `Udaplay_02_starter_project.ipynb`**

We have built an intelligent agent that combines local knowledge with web search capabilities using a State Machine architecture.

**Agent Capabilities:**

1.  **Internal Retrieval:** Answers questions using the ChromaDB vector store.
2.  **Self-Evaluation:** Evaluates if the retrieved documents are sufficient to answer the user's query.
3.  **Web Search Fallback:** Uses Tavily API to search the web if internal data is insufficient.
4.  **State Management:** Maintains conversation state and context.
5.  **Long-Term Memory:** (Advanced) Learns from web searches and updates the vector database.

**Implemented Tools:**

1.  `retrieve_game`: Semantic search in the vector database.
2.  `evaluate_retrieval`: LLM-based evaluator to assess document relevance.
3.  `game_web_search`: Tavily-based web search tool.

**Agent Workflow (State Machine):**
`Entry` -> `Retrieve` -> `Evaluate` -> (if good) `Generate` -> `End`
-> (if bad) `Web Search` -> `Generate` -> `End`

## Advanced Features

- **LearningResearchAgent:** An extension of the base agent that implements long-term memory. When the agent is forced to use Web Search, it automatically indexes the new findings back into ChromaDB, allowing it to answer from memory in future queries.

## Requirements

### Environment Setup

Create a `.env` file with the following API keys:

```
OPENAI_API_KEY="YOUR_KEY"
CHROMA_OPENAI_API_KEY="YOUR_KEY" (Optional, if using specific Chroma service)
TAVILY_API_KEY="YOUR_KEY"
```

### Project Dependencies

- Python 3.11+
- ChromaDB
- OpenAI SDK
- Tavily Python SDK
- python-dotenv

## How to Run

1.  **Initialize Database:** Run all cells in `Udaplay_01_starter_project.ipynb` to ingest the game data.
2.  **Run Agent:** Run `Udaplay_02_starter_project.ipynb` to initialize the agent and test it with queries.

### Directory Structure

```
project/
├── starter/
│   ├── games/           # JSON files with game data
│   ├── lib/             # Custom library implementations
│   │   ├── llm.py       # LLM abstractions
│   │   ├── messages.py  # Message handling
│   │   ├── ...
│   │   └── tooling.py   # Tool implementations
│   ├── Udaplay_01_starter_project.ipynb  # Part 1 implementation
│   └── Udaplay_02_starter_project.ipynb  # Part 2 implementation
```

## Testing Your Implementation

After completing both parts, test your agent with questions like:

- "When was Pokémon Gold and Silver released?"
- "Which one was the first 3D platformer Mario game?"
- "Was Mortal Kombat X released for PlayStation 5?"

## Notes

- Make sure to implement proper error handling
- Follow best practices for API key management
- Document your code thoroughly
- Test your implementation with various types of queries
