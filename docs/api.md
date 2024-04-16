# API

- [API](#api)
  - [Endpoints](#endpoints)
  - [Generate a completion](#generate-a-completion)
    - [Parameters](#parameters)
    - [Response](#response)

## Endpoints

## Generate a completion

```shell
POST /question
```

### Parameters

- `question`: (required) user message
- `system`: (optional) system message, if not provided project's system message will be used
- `stream`: (optional) boolean to specify if this completion is streamed
  
Advanced parameters (optional):

- `score`: (optional) cutoff score, if not provided project's cutoff score will be used [RAG]
- `k`: (optional) k value, if not provided project's k value will be used [RAG]
- `colbert_rerank`: (optional) boolean to specify if colbert reranking is enabled [RAG]
- `llm_rerank`: (optional) boolean to specify if llm reranking is enabled [RAG]
- `eval`: (optional) rag evaluation [RAG]
- `tables`: (optional) tables to be used in the question [RAGSQL]
- `negative`: (optional) negative prompt [VISION]
- `image`: (optional) image [VISION]
- `boost`: (optional) enrich user prompt via LLM [VISION]

### Response

- `question`: user question
- `answer`: answer
- `sources`: array with sources used to generate the answer
- `type`: type (inference, rag, vision, ragsql, etc)
- `tokens.input`: number of tokens used in the question
- `tokens.output`: number of tokens used in the answer
- `image`: image [VISION] [ROUTER]
- `evaluation.reason`: if eval was provided, the reason for the score [RAG]
- `evaluation.score`: if eval was provided, the score [RAG]