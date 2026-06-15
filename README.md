# Text2SQL — Natural Language to SQL Agent
 
> Transform plain-English questions into robust SQL queries and get instant answers from your database.
 
---
 
## Overview
 
**text2sql-project** is an AI-powered database assistant that lets users query a database using natural language. Under the hood, a **LangGraph** agent orchestrates a multi-step pipeline — understanding the user's intent, resolving the relevant table, generating syntactically correct SQL, and returning the query result — all without the user writing a single line of SQL.
 
The project ships with two interfaces:
 
- **`main.py`** — an interactive CLI session for terminal-based usage.
- **`app.py`** — a Streamlit web UI with a chat-style interface and live node-execution feedback.
---
