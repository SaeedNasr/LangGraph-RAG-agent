# 📈 LangGraph PDF RAG Agent

An intelligent Retrieval-Augmented Generation (RAG) agent built using **LangGraph** and **LangChain**. This agent acts as a smart document assistant that allows users to chat with local PDF files (currently configured for a Stock Market Performance report). 

Instead of relying on standard, linear scripts, this project uses a state-based graph architecture. The LLM evaluates the user's question, decides if it needs to search the document, triggers a custom retrieval tool to query a local **ChromaDB** vector database, and synthesizes the final answer with context.

## 🚀 Key Features
* **Graph-Based Reasoning:** Uses LangGraph's `StateGraph` to manage agent memory, conversational loops, and conditional tool routing.
* **Local Vector Storage:** Automatically chunks PDFs and saves OpenAI embeddings locally using ChromaDB to save on API costs and processing time.
* **Tool-Calling Architecture:** The LLM is bound to a custom Python retriever tool, allowing it to autonomously decide when and how to search the knowledge base.
* **Deterministic Outputs:** Configured with `temperature=0` to minimize hallucinations and ensure answers are strictly based on the provided document.

## 🛠️ Prerequisites

Before running this project, ensure you have:
* Python 3.8 or higher installed.
* An active [OpenAI API Key](https://platform.openai.com/).

---

## 📦 Installation

Follow these steps to set up the project on your local machine:

**1. Clone the repository:**
```bash
git clone [https://github.com/SaeedNasr/LangGraph-RAG-agent.git](https://github.com/SaeedNasr/LangGraph-RAG-agent.git)
cd LangGraph-RAG-agent
```
## Create and activate a virtual environment (Recommended):

```bash
# On Windows:
python -m venv .venv
.venv\Scripts\activate

# On Mac/Linux:
python3 -m venv .venv
source .venv/bin/activate

```
**3. Install the required dependencies:**

```bash
pip install langchain langgraph langchain-openai langchain-chroma langchain-community langchain-text-splitters pypdf python-dotenv
```
OR  pip install list to this beautifully simple command:

```bash
pip install -r requirements.txt
```

**4. Set up your environment variables:**
Create a file named exactly .env in the root folder of the project and add your OpenAI API key:

Plaintext
OPENAI_API_KEY="sk-your-actual-api-key-goes-here"
(Note: The .env file is included in .gitignore to keep your API key secure and out of version control.)

## 💻 Usage
Ensure you have your target PDF (e.g., Stock_Market_Performance_2024.pdf) in the same folder as your script.

Run the agent:

```bash
python Rag_Agent.py
```

## What happens next?

The script will load and chunk the PDF using RecursiveCharacterTextSplitter.

It will generate embeddings using text-embedding-3-small and save them locally to a chroma_db_storage folder.

An interactive terminal chat will open where you can ask questions.

The AI will query the database, retrieve the exact paragraphs needed, and answer your question!

Type exit or quit to end the session.
