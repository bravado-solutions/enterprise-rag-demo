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

enterprise-rag-demo/  
├── CSharp/  
│   ├── ownData.cs  
│   └── appsettings.json  
├── Python/  
│   ├── ownData.py  
│   └── python.env  
├── docs/  
│   └── instructions.md  
├── .gitignore  
├── LICENSE  
└── README.md  

---

## ⚙️ Prerequisites

**Azure Subscription** with access to:

- **Azure OpenAI Service** (GPT-4o & Text-Embedding-3-Small)  
- **Azure AI Search**  
- **Azure Storage Account**  

**Development Tools:**

- .NET 7 SDK  
- Python 3.11+  
- VS Code (or equivalent IDE)  

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
