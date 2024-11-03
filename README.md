## Q&A Pipeline for Loan and Credit Agreements using LlamaIndex

This repository hosts a full Q&A pipeline using the LlamaIndex framework. The data consists of loan and credit agreements, indexed and structured for retrieval and question-answering (Q&A) tasks. The system leverages LlamaIndex's VectorStoreIndex for efficient storage and retrieval of document chunk


## Pipeline Overview
1.Data Ingestion: Load data into the notebook.

2.Text Cleaning: Clean the text by replacing multiple consecutive spaces.

3.Node Creation: Use a sentence splitter and window parser to break down documents into smaller, manageable chunks.

4.Indexing: Use VectorStoreIndex to index chunked nodes with associated contexts for efficient retrieval.

5.Scoring: Rank results by similarity scores to find the top-k most relevant answers.

6.Evaluation: Assess relevancy and faithfulness using questions generated with the generate_question_context_pairs function.
## TECH

IDE: Visual Studio Code

Environment: Jupyter Notebook

Programming Language: Python

Libraries: LlamaIndex, SentenceTransformers, OpenAI

Version Control: Git
## SETUP


1. Indexing
In the initial project setup, the documents are loaded and transformed into LlamaIndex-compatible documents. This process allows us to index and store the text chunks into a vector store, enabling efficient retrieval.

after indexing we built basic rag pipeline 

Indexing is a critical step that organizes data into a vector store (VectorStoreIndex). This involves generating embeddings to capture the semantic meaning of text. We use Settings to apply configurations required for vector generation. These embeddings enable fast retrieval of semantically relevant document chunks.

Embedding Model: Embeddings are generated using the BAAI/bge-small-en-v1.5 model, which is optimized for retrieval-augmented generation tasks.

Query Testing
Once indexing is complete, we perform basic queries to validate the functionality and performance of the Q&A system
## USING GENERATED CONTEXT
When passing documents to a vector store for indexing, there are two main alternatives:

1. Passing the Whole Document:

Involves indexing the entire document as a single unit.
Suitable for smaller documents that fit comfortably within memory constraints.
Simpler indexing process but might lack granularity in capturing diverse content within larger documents.
2. Converting the Document into Nodes:

Breaks down the document into smaller, manageable chunks or nodes.
Ideal for larger documents to prevent memory issues and for better granularity.
Enables indexing of specific sections or segments, improving the ability to capture diverse content within the document.
## USING GENERATED CONTEXT
When passing documents to a vector store for indexing, there are two main alternatives:

1. Passing the Whole Document:

Involves indexing the entire document as a single unit.
Suitable for smaller documents that fit comfortably within memory constraints.
Simpler indexing process but might lack granularity in capturing diverse content within larger documents.
2. Converting the Document into Nodes:

Breaks down the document into smaller, manageable chunks or nodes.
Ideal for larger documents to prevent memory issues and for better granularity.
Enables indexing of specific sections or segments, improving the ability to capture diverse content within the document.
## VECTOR STORE
🎖️ Vector Store
The vector store, created with LlamaIndex, holds embeddings and metadata for each node. This structure ensures efficient data handling and enables fast and accurate retrieval for large language model (LLM) applications.
## MODEL
Once the pipeline is set up, the query can be done. To the question Which are the main characters of the book? the following output with the score and the top N node from where the information was retrieved.



The score represents the relevance or similarity measure between the query and the retrieved document. This score indicates the likelihood or degree to which the document is considered relevant to the query based on the model's understanding or learned representation of the text.

For instance:

A higher score typically suggests greater relevance or similarity between the query and the document.
Lower scores imply lesser relevance or similarity.

## MODEL EVALUATION
🚒 Model Evaluation
To evaluate the model the generate_question_context_pairs function to generate an evaluation dataset of (question, context) pairs over the text corpus was used. This uses the LLM to auto-generate questions from each context chunk.
