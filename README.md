
# Zenith — E-Commerce Customer Support AI Agent

**Zenith** is an enterprise-ready, security-hardened autonomous AI Customer Support Agent built for strict data isolation and transactional compliance at scale. Moving beyond basic LLM wrappers, Zenith enforces a **Zero-Trust Architecture** paired with an automated deterministic evaluation pipeline (`openai/gpt-oss-120b`) to safely execute real-time customer support and financial workflows.

---

## 🛡️ Core Security Architecture & Safeguard Engine

### 1. Hardened Database Security (Total Data Isolation)

- **Zero Raw Table Access:** The LLM is completely isolated from raw production tables and restricted strictly to low-privilege database views.
- **Mutation Protection:** Eliminates the risk of prompt-injected `DELETE`, `UPDATE`, or unauthorized data modifications.

### 2. Ironclad Session Authentication

- **JWT Token Decoding:** Ignores user-supplied text IDs within the chat interface to block account spoofing and cross-account data leaks.
- **Dynamic Context Mapping:** Decodes the frontend JWT session token natively on the backend to resolve and map the verified Customer ID.

### 3. Split-Execution Financial Engine & Anti-Fraud Ledger

- **Autonomous Refunds:** Processes instant, real-time refunds autonomously for low-risk claims capped at **$30**.
- **HITL Escalation Key:** Claims exceeding **$30** trigger an immediate state freeze, generate a unique tracking key, and route the request to Human-In-The-Loop (HITL) review logs.
- **Immutable Ledger:** Writes every financial transaction with a unique constraint to an isolated ledger table, preventing duplicate refund exploits ("double-dipping").

---

## 📊 Automated Evaluation & Metrics Breakdown

Zenith's safety policies, RAG retrieval accuracy, and guardrails are benchmarked via an automated LLM-as-a-judge pipeline (`openai/gpt-oss-120b`) across 3 test suites (**Baseline**, **Guardrails/Smoke**, and **Edge Policies**) over a relational dataset of **100,000+ orders (1.5M+ rows)**.

### 📈 Aggregate Performance

| Evaluation Metric                           |      Score      | System Behavior Insights                                                                                    |
| :------------------------------------------ | :--------------: | :---------------------------------------------------------------------------------------------------------- |
| **Faithfulness (Anti-Hallucination)** | **98.18%** | Strictly adheres to retrieved policy bounds with near-zero hallucination.                                   |
| **Answer Relevancy**                  | **93.02%** | Delivers direct, actionable support responses without verbose filler.                                       |
| **Contextual Precision**              | **87.80%** | Accurately ranks and retrieves relevant enterprise knowledge base rules via `pgvector`.                   |
| **Contextual Recall**                 | **84.85%** | Extracts critical policy conditions across both English and Hinglish queries.                               |
| **Semantic Correctness**              | **67.50%** | Tracks edge-case performance on multi-clause conditional policies (e.g., packaging rules on return claims). |

### 🛠️ Guardrails & Validation Highlights

- **Intent Isolation:** Achieved **100% (1.00)** accuracy on the guardrail suite, isolating casual greetings (`"hi"`, `"good morning"`) from triggering transactional workflows.
- **Multilingual Robustness:** Accurately processes mixed-lingual inputs—including Roman-script Hinglish queries (e.g., *"Mere debit card ka refund kitne din me aayega?"*)—while mapping to the exact policy window.

---

## ⚡ Tech Stack & Data Sources

- **Backend Framework:** FastAPI (Asynchronous concurrent query orchestration)
- **Database Infrastructure:** AWS PostgreSQL (Transactional storage & isolated views)
- **Vector Search Engine:** `pgvector` (Semantic policy retrieval)
- **Embedding Model:** `BAAI/bge-small-en-v1.5`
- **LLM & Evaluation Judge:** `openai/gpt-oss-120b`
- **Datasets:** [Brazilian E-Commerce Public Dataset (Olist)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) · [Bitext Customer Support Dataset](https://huggingface.co/datasets/bitext/Bitext-customer-support-llm-chatbot-training-dataset)

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10+
- PostgreSQL with the `pgvector` extension enabled
- API credentials for `openai/gpt-oss-120b`

### Installation

```bash
git clone https://github.com/AyushShrivastava2808/Zenith.git
cd Zenith
pip install -r requirements.txt
```

## Author

Ayush Shrivastava

- Repository: https://github.com/AyushShrivastava2808/Zenith
