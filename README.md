# RAG_Engine
## Motivation
Found myself setting up the same retrieval process over and over again for different projects. Decided to spend an extra hour to set up a system that can be reused. 

## What it does
Contextual Retrieval (https://www.anthropic.com/news/contextual-retrieval) with prefix-caching in a fully parallelized way (both for indexing and querying)

## Initialization
Setup the environment variables by creating a `.env` file in your project directory with the following variables:

- `OPENAI_API_KEY`: Your OpenAI API key.
- `PINECONE_API_KEY`: Your Pinecone API key.
- `PINECONE_REGION`: The region where your Pinecone index is located (e.g., `us-east-1`).
- `PINECONE_INDEX_NAME`: The name of the Pinecone index to use for storing and querying documents.

Install the relevant packagse by running the installs in `setup.sh`

## Usage

To use the `contextual_retriever` module, you can initialize it with the following code:

```python
from contextual_retriever import ContextualRetriever

cr = ContextualRetriever()
```

### Indexing Documents
```python 
documents = [
"What is the capital of France?",
"What is the capital of Germany?"
]
cr.index_documents(documents)
```

### Retrieving most similar chunks
```python
query = "What is the capital of France?"
results = cr.query_pinecone_index(query)
```

### Retrieving the most similar documents
```python
document_names = closest_matching_documents(query, top_k=3)
```


### Credits
Implementation is adapted from https://www.youtube.com/watch?v=6efwN_US-zk and https://github.com/akshgarg7/Specter. 