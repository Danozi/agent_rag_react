Agentic RAG System with ReAct Pattern
An intelligent multi-tool agent that autonomously gathers information from multiple sources to answer complex queries about company financials and leadership.
Overview
Built a ReAct (Reasoning + Acting) agent using LangChain and GPT-4o that orchestrates three custom tools to answer multi-part questions by intelligently chaining information retrieval operations.
Key Features

Multi-Tool Orchestration: Agent autonomously selects and uses 3 custom tools based on query requirements
FAISS Vector Search: Semantic search over 2,027 document chunks from SEC 10-K filings using OpenAI embeddings
Flashrank Reranking: Improves retrieval accuracy by reranking top 12 results to 5 most relevant documents
Web Search Integration: Real-time information retrieval via SerpAPI for current events and data
Automated LinkedIn Lookup: Extracts director names from filings and finds LinkedIn profiles
LangSmith Tracing: Complete visibility into agent reasoning, tool selection, and execution flow

Architecture

Gmail Trigger → Receives incoming emails
Document Processing → Loads and chunks SEC 10-K filings (Tesla, General Motors)
Vector Store → FAISS with OpenAI text-embedding-3-small (1536 dimensions)
ReAct Agent → GPT-4o orchestrating tool selection and execution
Custom Tools:

Company Directors Tool (name extraction + LinkedIn lookup)
Web Search Tool (SerpAPI integration)
Vector Reranker Search Tool (FAISS + Flashrank)



Tech Stack

LLM: OpenAI GPT-4o
Framework: LangChain, LangSmith
Vector DB: FAISS
Embeddings: OpenAI text-embedding-3-small
Reranking: Flashrank (ms-marco-TinyBERT-L-2-v2)
Web Search: SerpAPI
Document Processing: RecursiveCharacterTextSplitter

Results
Successfully answers complex multi-part queries like:

"Who are the directors of Tesla? What are their LinkedIn handles? What are Tesla's financial goals this year? What is the next auto show Tesla will participate in?"

The agent autonomously:

Extracts 8 director names from filings
Retrieves 7 LinkedIn profiles
Searches vector DB for financial information
Performs web searches for current events
Synthesizes information into coherent answers

Performance Metrics

Documents Processed: 2,027 chunks from 2 companies
Vector Dimension: 1,536
Retrieval: 12 → 5 documents (after reranking)
Tools Available: 3 custom tools
Tracing: Full LangSmith integration
