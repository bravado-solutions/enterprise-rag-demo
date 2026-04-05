# Enterprise RAG Demo | Bravado Solutions
**Building Scalable AI Systems for the Modern Enterprise**

Bravado Solutions is an enterprise software development company building scalable AI systems, SaaS platforms, and cloud-native applications.

This repository demonstrates an enterprise-ready **Retrieval-Augmented Generation (RAG)** architecture on Azure. It includes both C# and Python implementations for integrating proprietary data with GPT models via Azure OpenAI and Azure AI Search.

---

## 🚀 Overview
Most AI projects fail **not because of models—but because of data fragmentation and weak architecture**. This reference implementation focuses on:

- **Grounding:** Ensuring LLM responses are based strictly on enterprise data.  
- **Scalability:** Building RAG pipelines that handle production loads on Azure.  
- **Hybrid Search:** Integrating vector search with GPT models for high accuracy.  

---

## 🧠 Architecture
The solution follows a standard enterprise RAG pipeline:

1. **Data Ingestion:** Uploading unstructured documents to Azure Storage.  
2. **Indexing:** Azure AI Search handles vectorization and chunking.  
3. **Retrieval:** Context is fetched via vector/hybrid search based on user intent.  
4. **Generation:** Azure OpenAI generates grounded responses using the retrieved context.  

---
## 📂 Repository Structure

```text
enterprise-rag-demo/
├── CSharp/
│   ├── ownData.cs           # C# implementation for data ingestion
│   └── appsettings.json     # Configuration for .NET environment
├── Python/
│   ├── ownData.py           # Python implementation for data ingestion
│   └── python.env           # Environment variables template
├── docs/
│   └── instructions.md      # Detailed setup and usage guides
├── .gitignore               # Excludes secrets and build artifacts
├── LICENSE                  # Repository licensing information
└── README.md                # Project overview and quick start
```

## ⚙️ Prerequisites

**Azure Subscription** You will need an Azure subscription with access to the following resources:
* **Azure OpenAI Service:** Required for **GPT-4o** (Chat) and **Text-Embedding-3-Small** (Embeddings).
* **Azure AI Search:** To host the vector index and perform retrieval.
* **Azure Storage Account:** For hosting source documents and training data.

**Development Tools**
* **.NET 7 SDK:** For running the C# implementation.
* **Python 3.11+:** For running the Python implementation and scripts.
* **VS Code:** (Or your preferred IDE) with the Azure and Python extensions installed.

---
## 🔧 Setup

### 1. Provision Azure Resources
- **Azure OpenAI:** Deploy a chat model (e.g., GPT-4o) and an embedding model.  
- **Azure AI Search:** Create an index with vector support.  
- **Storage:** Upload your PDFs or docs to a container named `data`.  

---

### 2. Configure Environment

**Python:**  
Run `cp .env.example .env` and update `.env` with your Azure endpoints and keys.

**C#:**  
Run `Copy-Item appsettings.json.template appsettings.json` and update `appsettings.json` with your Azure configuration.

---

### 3. Install Dependencies

**Python:**  
Run `pip install -r requirements.txt`

**C#:**  
Run `dotnet add package Azure.AI.OpenAI` and `dotnet add package Azure.Search.Documents`

---

### 4. Run the Application

**Python:** Run `python ownData.py`  
**C#:** Run `dotnet run`

---

## 🔐 Security Best Practices
- **Secrets:** Never commit `.env` or `appsettings.json` with real keys.  
- **Identity:** Use Managed Identities (RBAC) instead of API keys for production.  
- **Rotation:** Regularly rotate Azure service keys.  

---

## 🤝 Work with Bravado Solutions
We help enterprises move from AI experimentation to production-grade systems.

- 🌐 Website: [bravadosolutions.com](https://bravadosolutions.com)  
- 📧 Contact: contact@bravadosolutions.com
