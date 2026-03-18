# GuardedRAG: Production-Grade LLM Guardrails for Safe Customer Support

## Overview
GuardedRAG is a production-oriented Retrieval-Augmented Generation (RAG) chatbot system enhanced with modular guardrails to ensure safe, reliable, and controlled LLM behavior.

The system addresses key failure modes of LLM applications such as hallucinations, sensitive data leakage, and off-topic responses by introducing validation layers across both user inputs and model outputs.

## Key Features
- Input and output validation pipelines
- Hallucination detection using Natural Language Inference (NLI)
- PII detection and redaction
- Topic restriction and domain enforcement
- Competitor mention filtering using NER + rule-based logic
- Modular guardrail design for extensibility

## Architecture
The system wraps a standard RAG pipeline with guardrails at multiple stages:

1. Input Guards
   - Detect and filter unsafe or irrelevant queries
   - Redact sensitive information (PII)

2. Retrieval Layer
   - Fetch relevant documents from knowledge base

3. Generation (LLM)
   - Generate response grounded in retrieved context

4. Output Guards
   - Validate factual consistency (NLI-based hallucination check)
   - Enforce topic constraints
   - Prevent sensitive or competitor-related content leakage

## Guardrails Implemented

### 1. Hallucination Detection (NLI)
Uses an NLI model to verify whether generated responses are entailed by retrieved documents.

### 2. PII Protection
Detects and redacts sensitive information in both user inputs and model outputs.

### 3. Topic Control
Ensures the chatbot stays within domain-specific boundaries (e.g., pizza shop context).

### 4. Competitor Filtering
Prevents mentions of competitors using:
- Named Entity Recognition (NER)
- Exact match + threshold-based similarity checks

### 5. Input/Output Validation
Applies structured validation rules before and after LLM generation to enforce consistency and safety.

## Notebooks

- `1 Failure modes in RAG applications.ipynb`  
  Identifies key failure modes in LLM and RAG systems.

- `2 Checking for hallucinations using NLI.ipynb`  
  Implements NLI-based validation for factual consistency.

- `3 Using hallucination guard in a chatbot.ipynb`  
  Integrates hallucination detection into chatbot pipeline.

- `4 Keeping chatbot on topic.ipynb`  
  Enforces domain-specific topic constraints.

- `5 Ensuring no PII is leaked.ipynb`  
  Detects and redacts sensitive user and model data.

- `6 Preventing competitor mentions.ipynb`  
  Implements NER-based competitor filtering logic.

## Tech Stack
- Python
- LLM APIs
- GuardrailsAI
- Natural Language Inference (NLI)
- Named Entity Recognition (NER)
- RAG architecture

## Use Cases
- Customer support chatbots
- Regulated AI systems (finance, healthcare)
- Enterprise-grade conversational agents
- Safety-critical LLM deployments

## Why This Matters
LLMs are inherently probabilistic and can produce inconsistent or unsafe outputs. GuardedRAG introduces deterministic control layers that make LLM systems production-ready by improving reliability, safety, and trustworthiness.

## Future Improvements
- RL-based guardrail optimization
- Real-time monitoring and feedback loops
- Adaptive guardrails based on user behavior
- Integration with evaluation pipelines (LLM-as-a-judge)
