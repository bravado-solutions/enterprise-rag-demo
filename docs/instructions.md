# Enterprise RAG Demo – Bravado Solutions

Enterprise-grade Retrieval-Augmented Generation (RAG) using Azure OpenAI and Azure Cognitive Search.

This repository demonstrates how to implement a secure, scalable RAG system that leverages enterprise data to enhance AI-driven applications. It uses Azure OpenAI for generative AI and Azure Cognitive Search for indexing and vectorizing internal data, providing responses grounded in your proprietary knowledge base.

---

## 🚀 Core Capabilities

- **RAG with Enterprise Data:** Integrate organizational documents, PDFs, or knowledge bases into generative AI workflows.  
- **Azure OpenAI Models:** Deploy GPT models (e.g., GPT-4o) and text embeddings to provide context-aware completions.  
- **Vector Search:** Use Azure Cognitive Search to index and vectorize content, making AI responses data-grounded.  
- **Multi-Language Support:** Sample implementations for C# and Python.  
- **Scalable & Secure:** Enterprise-ready deployment patterns with secure API keys and compliance-ready architecture.

---

## 🏗️ Provision Azure Resources

Required Azure resources:

1. **Azure OpenAI** – deploy GPT models and text embeddings.  
2. **Azure Cognitive Search** – index and vectorize enterprise documents.  
3. **Azure Storage Account** – store PDFs, documents, and other data sources.  

**Recommended Steps:**

1. **Create Azure OpenAI Resource**  
   - Subscription: Your approved Azure subscription  
   - Resource group: Choose or create a dedicated resource group  
   - Region: Select a region supporting Azure OpenAI quotas  
   - Name: Unique resource name  
   - Pricing tier: Standard S0  

2. **Create Azure Cognitive Search Resource**  
   - Resource group: Same as Azure OpenAI  
   - Service name: Unique name  
   - Region: Same as Azure OpenAI  
   - Pricing tier: Basic  

3. **Create Storage Account**  
   - Resource group: Same as Azure OpenAI  
   - Account name: Unique name  
   - Primary service: Azure Blob Storage or Data Lake Storage Gen2  
   - Performance: Standard  
   - Redundancy: Locally redundant storage (LRS)  

> Tip: Keep all resources in the same region for optimal performance.

---

## 📂 Upload Enterprise Data

1. Navigate to your Storage Account → **Blob Containers** → create a container (e.g., `enterprise-data`).  
2. Upload PDFs, documents, or structured data relevant to your business domain.  
3. Ensure data files are named clearly to aid indexing.

---

## 🔧 Deploy Models

### Text Embedding Model

```bash
az cognitiveservices account deployment create \
  -g <resource_group> \
  -n <OpenAI_resource> \
  --deployment-name text-embedding-ada-002 \
  --model-name text-embedding-ada-002 \
  --model-version "2" \
  --model-format OpenAI \
  --sku-name "Standard" \
  --sku-capacity 5

  GPT Model Deployment
az cognitiveservices account deployment create \
  -g <resource_group> \
  -n <OpenAI_resource> \
  --deployment-name gpt-4o \
  --model-name gpt-4o \
  --model-version "2024-05-13" \
  --model-format OpenAI \
  --sku-name "Standard" \
  --sku-capacity 5

  🗂️ Index Enterprise Data with Azure Cognitive Search
Navigate to your Cognitive Search resource → Import and vectorize data
Select Azure Blob Storage as the data source
Configure:
Subscription, Blob account, and container
Leave blob folder blank
Disable deletion tracking
API Key authentication for Azure OpenAI service
Enable semantic ranking and schedule a one-time indexer
Name the index: enterprise-rag-index

💻 Develop Your Application
Clone this repository locally using Visual Studio Code
Install required SDK packages:

C#

dotnet add package Azure.AI.OpenAI --version 2.1.0
dotnet add package Azure.Search.Documents --version 11.6.0

Python

pip install openai==1.65.2
pip install azure-search-documents==11.6.0
Update configuration files with your Azure endpoints, keys, and deployment names:
Azure OpenAI endpoint & key
GPT deployment: gpt-4o
Azure Search endpoint & key
Index name: enterprise-rag-index

🧩 Use Azure OpenAI with Your Index
C# Example
ChatCompletionOptions chatCompletionsOptions = new ChatCompletionOptions()
{
    MaxOutputTokenCount = 600,
    Temperature = 0.9f,
};

chatCompletionsOptions.AddDataSource(new AzureSearchChatDataSource()
{
    Endpoint = new Uri(azureSearchEndpoint),
    IndexName = azureSearchIndex,
    Authentication = DataSourceAuthentication.FromApiKey(azureSearchKey),
});
Python Example

completion = client.chat.completions.create(
    model=deployment,
    messages=[{"role": "user", "content": input("Enter question: ")}],
    extra_body={
        "data_sources":[
            {
                "type": "azure_search",
                "parameters": {
                    "endpoint": os.environ["AZURE_SEARCH_ENDPOINT"],
                    "index_name": os.environ["AZURE_SEARCH_INDEX"],
                    "authentication": {"type": "api_key", "key": os.environ["AZURE_SEARCH_KEY"]}
                }
            }
        ],
    }
)

▶️ Run Your Application
C#: dotnet run
Python: python ownData.py

Test queries against your indexed enterprise data to generate context-aware AI responses.

⚙️ Cleanup

After testing, delete Azure resources to avoid unnecessary costs:

Azure OpenAI resource
Azure Cognitive Search service
Storage account and data containers