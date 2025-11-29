# RAG (Retrieval-Augmented Generation)

## Architecture Diagram

```mermaid
flowchart TD
    Start([User Question]) --> Embed[Vectorize Question<br/>Convert to Embeddings]

    Embed --> Search[Search Vector Database<br/>Find Similar Documents]

    KnowledgeBase[(Vector Database<br/>Document Embeddings)] -.Retrieve.-> Search

    Search --> Retrieve[Retrieved Relevant<br/>Context/Documents]

    Retrieve --> Augment[Augment Prompt<br/>Question + Context]

    Start -.Original Question.-> Augment

    Augment --> LLM[LLM Generator<br/>Process Augmented Prompt]

    LLM --> Generate[Generate Enhanced Answer<br/>Based on Context]

    Generate --> End([Return Answer to User])

    style Start fill:#e1f5ff
    style End fill:#e1f5ff
    style Embed fill:#fff4e1
    style Search fill:#fff4e1
    style Augment fill:#ffe1f5
    style LLM fill:#f5e1ff
    style Generate fill:#e1ffe1
    style KnowledgeBase fill:#f0f0f0
```

## How RAG Works

RAG (Retrieval-Augmented Generation) enhances LLM responses by retrieving relevant information from a knowledge base before generating answers.

**Pipeline Steps:**
1. **User Question** - The user submits a query
2. **Vectorization** - Question is converted to embeddings
3. **Retrieval** - System searches vector database for similar documents
4. **Augmentation** - Retrieved context is combined with the original question
5. **Generation** - LLM generates answer using both question and context
6. **Output** - Enhanced answer is returned to user
