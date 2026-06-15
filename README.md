# Text2SQL — Natural Language to SQL Agent
 
> Transform plain-English questions into robust SQL queries and get instant answers from your database.
 
---
 
## Overview
 
**text2sql-project** is an AI-powered database assistant that lets users query a database using natural language. Under the hood, a **LangGraph** agent orchestrates a multi-step pipeline — understanding the user's intent, resolving the relevant table, generating syntactically correct SQL, and returning the query result — all without the user writing a single line of SQL.
 
The project ships with two interfaces:
 
- **`main.py`** — an interactive CLI session for terminal-based usage.
- **`app.py`** — a Streamlit web UI with a chat-style interface and live node-execution feedback.
---
## Project Structure
 
```
text2sql-project/
├── agent/                      # Core LangGraph agent definition
│   └── graph.py                # Compiled LangGraph application (state machine)
├── functions/                  # Utility functions used by agent nodes
├── knowledge_graph_builder/    # Schema relationship graph construction
├── lib/                        # Shared library code / helpers
├── LLM_prompts/                # Prompt templates used across agent nodes
├── metadata_builder/           # Database schema metadata extraction
├── vector_db_builder/          # Embeds schema metadata into a vector store
├── assets/                     # Static assets (images, etc.)
├── app.py                      # Streamlit web UI entry point
├── main.py                     # CLI entry point
└── requirements.txt            # Python dependencies
```
 
---
 
## Architecture
 
The agent follows a node-based execution model managed by **LangGraph**:
 
```
User Query
    │
    ▼
[Intent / Table Resolution Node]
    │   Uses vector similarity search to identify the relevant table
    ▼
[Metadata Retrieval Node]
    │   Fetches schema details (columns, types, relationships)
    ▼
[SQL Generation Node]
    │   Constructs the SQL query via an LLM using schema context
    ▼
[SQL Execution Node]
    │   Runs the query against the database
    ▼
[Response Formatting Node]
    └─► Returns result + generated SQL to user
