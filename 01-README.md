# **Layers e Stacks – 3 Casos Reais MVP**

---

## **Caso 1 – Assistente Virtual Multicanal (LLM + RAG)**

**Layers**

```
[ Canais & UI ]
        ↓
[ API Gateway / BFF (FastAPI) ]
        ↓
[ Orquestração Conversacional (LangChain/LangGraph) ]
        ↓
[ Tools/Agents (CRM, Core Banking, OCR, Billing) ]
        ↓
[ LLM & Guardrails ]
        ↓
[ RAG: Indexação/Busca Semântica ]
        ↓
[ Dados & Integrações ]
        ↓
[ Observabilidade | Segurança | DevOps | Testes/MLOps ]
```

**Stacks**

* Canais & UI: Web chat, App, WhatsApp (Twilio/Meta), e-mail.
* API Gateway / BFF: **FastAPI**, **NGINX**, cache **Redis**.
* Orquestração: **LangChain**, **LangGraph**.
* Tools/Agents: CRM, Core Banking, OCR (**AWS Textract**, **Tesseract**).
* LLM & Guardrails: **OpenAI GPT-4**, PII check, pydantic guards.
* RAG: **Azure Cognitive Search**, **Weaviate**, embeddings **BERT/Sentence-Transformers**.
* Dados & Integrações: **PostgreSQL**, **S3/Blob**, **RabbitMQ**.
* Observabilidade: **OpenTelemetry**, **Prometheus/Grafana**.
* Segurança: **OAuth2/OIDC**, **Key Vault**.
* DevOps: **Docker**, **Kubernetes (AKS)**, **Terraform**, **GitHub Actions**.
* Testes/MLOps: **Pytest**, **Locust**, **ragas**, **MLflow**.

---

## **Caso 2 – Agente Autônomo para Documentos Jurídicos**

**Layers**

```
[ Ingestão & OCR ]
        ↓
[ Pipeline NLP ]
        ↓
[ API & Backoffice ]
        ↓
[ Busca Semântica / Indexação ]
        ↓
[ Armazenamento & Eventos ]
        ↓
[ Observabilidade | Segurança | DevOps | Testes/MLOps ]
```

**Stacks**

* Ingestão & OCR: **Azure Cognitive Services**, **Tesseract**.
* Pipeline NLP: **spaCy**, **HuggingFace Transformers**, **PyTorch**.
* API & Backoffice: **FastAPI**, **React** ou FastAPI-admin, **JWT**.
* Busca Semântica: **ElasticSearch**, embeddings **Sentence-BERT**.
* Armazenamento & Eventos: **PostgreSQL**, **S3/Blob**, **RabbitMQ/Celery**.
* Observabilidade: **OpenTelemetry**, **Prometheus/Grafana**.
* Segurança: **Vault/Key Vault**, PII masking.
* DevOps: **Docker**, **K8s**, **Terraform**, **GitHub Actions**.
* Testes/MLOps: **Pytest**, **Great Expectations**, **Locust**, **MLflow**, **DVC**.

---

## **Caso 3 – Chat Operacional IoT (Diagnóstico + Predição)**

**Layers**

```
[ Canais & UI (Chat) ]
        ↓
[ BFF / API (FastAPI) ]
        ↓
[ Orquestração (LangChain Tools) ]
        ↓
[ Modelos de Predição / Anomalias ]
        ↓
[ Streams & Timeseries ]
        ↓
[ RAG técnico + Catálogos ]
        ↓
[ Observabilidade | Segurança | DevOps | Testes/MLOps ]
```

**Stacks**

* Canais & UI: Chat web/app, notificações.
* BFF / API: **FastAPI**, **NGINX**, **Redis**.
* Orquestração: **LangChain Tools**.
* Modelos: **scikit-learn**, **PyTorch**, **Feast**.
* Streams & Timeseries: **Kafka**, **Flink**, **TimescaleDB**, **pgvector**.
* RAG técnico: embeddings **Sentence-BERT**, **Weaviate**.
* Observabilidade: **Prometheus/Grafana**, **Loki**.
* Segurança: **mTLS**, **RBAC**, **Vault**.
* DevOps: **Kubernetes (EKS)**, **Helm**, **Terraform**, **Jenkins**.
* Testes/MLOps: **Pytest**, **Locust**, **MLflow**.

---

# **README Completo (Bilingue)**

## **Português**

Este material apresenta **três casos reais** de projetos com IA e agentes inteligentes, cada um documentado com:

1. **Arquitetura em camadas (layers)** – mostrando o fluxo do front-end até dados, modelos e infraestrutura.
2. **Stacks tecnológicas** – ferramentas, frameworks e serviços usados em cada camada.
3. **Resultados** – métricas técnicas e impacto de negócio.

**Objetivo:** servir como base para apresentações técnicas e discussões arquiteturais, permitindo demonstrar:

* Profundidade técnica.
* Decisões de arquitetura.
* Resultados mensuráveis.

**Como usar:**

* Leia cada caso antes de apresentar para dominar o storytelling.
* Use as layers como guia visual enquanto explica.
* Destaque resultados em **negócio** (ex.: redução de tempo, aumento de precisão) e **técnicos** (ex.: latência, escalabilidade).

---

## **English**

This material presents **three real-world** AI and intelligent agent projects, each documented with:

1. **Layered architecture** – showing the flow from UI to data, models, and infrastructure.
2. **Technology stacks** – tools, frameworks, and services used in each layer.
3. **Results** – technical metrics and business impact.

**Purpose:** to serve as a base for technical presentations and architectural discussions, enabling you to showcase:

* Technical depth.
* Architectural decisions.
* Measurable outcomes.

**How to use:**

* Review each case beforehand to master the storytelling.
* Use the layers as a visual guide while explaining.
* Highlight **business results** (e.g., time reduction, accuracy gains) and **technical results** (e.g., latency, scalability).
