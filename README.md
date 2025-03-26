# Intelligent QA System Using CRAG 🎯

# 📜Overview

This project implements a Corrective Retrieval-Augmented Generation (CRAG) that combines document retrieval, dynamic query rephrasing, and web search integration to provide high-quality, contextually relevant answers to user queries. The system leverages OpenAI GPT-4 for query refinement and answer generation, LanceDB for vector-based document retrieval, LangChain for orchestration, and Tavily API for supplementing information with web search results.

# 🌟Key Features

**Document Retrieval:** The system starts by retrieving documents related to the user’s query. It uses LanceDB, a vector database, to perform semantic search. This allows the system to fetch documents that are contextually relevant, even if they don’t exactly match the query terms. The retrieved documents serve as the foundational context for answering the question.

**Document Grading and Filtering:** To ensure high-quality results, GPT-4 is employed to assess the relevance of the retrieved documents. The documents are graded based on their relevance to the query, and irrelevant content is filtered out. This step ensures that only the most valuable information is passed on to the next stages.

**Dynamic Query Refinement:** In cases where the retrieved documents are insufficient or lack depth, the system dynamically rephrases or refines the original query. This query transformation process is powered by GPT-4, which reformulates the question in a way that makes it easier to retrieve more relevant or detailed information, optimizing it for retrieval accuracy and ensuring better context matching.

**Web Search Integration:** If the retrieved documents are still lacking, the system integrates Tavily API to conduct a web search. This external knowledge source supplements the context with real-time, up-to-date information from the web, ensuring that the answer generation step has all the necessary data.

**Answer Generation:** Once relevant documents have been retrieved and the query refined (if needed), the system uses GPT-4 to generate a well-rounded, accurate answer. By synthesizing the best information from the documents and the refined query, the system produces a response that accurately addresses the user’s question.


# 🧰Tech Stack

**Python:** The primary programming language used to implement the system.

**LangChain:** For orchestrating the multi-step pipeline, handling prompts, and managing interactions between models and tools.

**OpenAI GPT-4:** For dynamic query refinement, document grading, and answer generation.

**LanceDB:** A vector database for storing and querying document embeddings for semantic retrieval.

**Pydantic:** For data validation and schema enforcement within the pipeline.

**Tavily API:** For web search integration to fetch real-time information and supplement document context.

# ⚙️How It Works

**1. Retrieve Documents:**
The system begins by retrieving documents based on the user's query. It uses LanceDB to perform a semantic search using vector embeddings.


**2. Grade Documents:**
Retrieved documents are assessed for relevance using GPT-4. Irrelevant documents are filtered out based on a binary "yes/no" relevance score.

**3. Query Refinement:**
If relevant documents are not found or more context is needed, the query is rephrased using GPT-4 to optimize it for retrieval, which helps improve accuracy in subsequent steps.

**4. Web Search:**
If additional information is needed, a web search is conducted using Tavily API to fetch up-to-date external content, which is then added to the context for final answer generation.

**5. Answer Generation:**
The system generates an answer by combining relevant documents and the refined query using GPT-4, delivering a contextually accurate and complete response.


# 🔄Processing Flow
The system processes the query through a series of steps:

**Document retrieval -> Document grading -> Query transformation (if necessary) -> Web search (if needed) -> Answer generation**

# 🚀Future Improvements

**Real-time Feedback:** Adding a feedback mechanism to fine-tune query transformations and improve relevance grading.

**Enhanced Query Expansion:** Implementing more sophisticated methods for generating alternative queries and handling ambiguous inputs.

**Scalability:** Optimize the pipeline to handle large-scale document repositories and queries.
