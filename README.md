![image](https://user-images.githubusercontent.com/113465005/226238596-cc76039e-67c2-46b6-b0bb-35d037ae66e1.png)

Your organization requires a Multi-Channel Smart Chatbot and a search engine capable of comprehending diverse types of data scattered across various locations. Additionally, the conversational chatbot should be able to provide answers to inquiries, along with the source and an explanation of how and where the answer was obtained. In other words, you want **private and secured ChatGPT for your organization that can interpret, comprehend, and answer questions about your business data**.

The goal of the POC is to show/prove the value of a GPT Virtual Assistant built with Azure Services, with your own data in your own environment. The deliverables are:

1. Backend Bot API built with Bot Framework and exposed to multiple channels (Web Chat, MS Teams, SMS, Email, Slack, etc)
2. Frontend web application with a Search and a Bot UI.

---
# Architecture 
![Architecture](./images/GPT-Smart-Search-Architecture.jpg "Architecture")

## Flow
1. The user asks a question.
2. In the app, an OpenAI GPT-4 LLM uses a clever prompt to determine which source to use based on the user input
3. Four types of sources are available:
   * 3a. Azure SQL Database - contains COVID-related statistics in the US.
   * 3b. Azure Bing Search API - provides access to the internet allowing scenerios like: QnA on public websites .
   * 3c. Azure Cognitive Search - contains AI-enriched documents from Blob Storage (10k PDFs and 90k articles).
      * 3c.1. Uses OpenAI to vectorize the top K document chunks
      * 3c.2. Fills up the vector-based indexes on-demand.
      * 3c.3. Gets the Top N Chunks by doing a vector search on vector-based indexes.
   * 3d. CSV Tabular File - contains COVID-related statistics in the US.
4. The app retrieves the result from the source and crafts the answer.
5. The tuple (Question and Answer) is saved to CosmosDB to keep a record of the interaction and further analysis.
6. The answer is delivered to the user.

---
## Demo

https://gptsmartsearch.azurewebsites.net/

To open the Bot in MS Teams, click [HERE](https://teams.microsoft.com/l/chat/0/0?users=28:5d583679-8196-4673-9d77-c294c010bca5)

---

## 🔧**Features**

   - Uses [Bot Framework](https://dev.botframework.com/) and [Bot Service](https://azure.microsoft.com/en-us/products/bot-services/) to Host the Bot API Backend and to expose it to multiple channels including MS Teams.
   - 100% Python.
   - Uses [Azure Cognitive Services](https://azure.microsoft.com/en-us/products/cognitive-services/) to index and enrich unstructured documents: Detect Language, OCR images, Key-phrases extraction, entity recognition (persons, emails, addresses, organizations, urls).
   - Uses Vector Search Capabilities of Azure Cognitive Search to provide the best semantic answer.
   - Creates vectors on-demand as users interact with the system. (versus vectorizing the whole datalake at the beginning)
   - Uses [LangChain](https://langchain.readthedocs.io/en/latest/) as a wrapper for interacting with Azure OpenAI , vector stores, constructing prompts and creating agents.
   - Multi-Lingual (ingests, indexes and understand any language)
   - Multi-Index -> multiple search indexes
   - Tabular Data Q&A with CSV files and SQL flavor Databases
   - Uses [Azure AI Document Intelligence SDK (former Form Recognizer)](https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/overview?view=doc-intel-3.0.0) to parse complex/large PDF documents
   - Uses [Bing Search API](https://www.microsoft.com/en-us/bing/apis) to power internet searches and Q&A over public websites.
   - Uses CosmosDB as persistent memory to save user's conversations.
   - Uses [Streamlit](https://streamlit.io/) to build the Frontend web application in python.
---

### 场景1. 使用bingsearch 获取最新事实消息，通过gpt加工简化变成易读易懂的简答咨询

@bing，今天上海天气

<img width="1300" alt="Public-Domain-information-BingSearch" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/45226a51-4765-423b-b872-b31d7d880880">

### 场景2. 使用chatgpt原始创作能力，做一些文字方面AIGC

@chatgpt,开学了，以小学生的口吻，写一首打油诗，抒发自己愉快的心情。

<img width="1300" alt="chatgpt-KB" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/0a064a29-cbc3-4803-929a-37cae466cf07">

### 场景3. 关系型数据作为知识库，对数据进行问答

@sqlsearch， 总共有多少本书？

<img width="1300" alt="Database-MySQL" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/c82908ec-97dd-4a9f-b698-5b0a2db962d8">

### 场景4. 使用搜索引擎作为非关系知识库，对文档进行问答

@docsearch, 科大讯飞的主营业务是什么？

<img width="1300" alt="Non-Relation-database-CongnitiveSearch" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/aaab30c5-5081-4d30-8342-7133bef3de84">








