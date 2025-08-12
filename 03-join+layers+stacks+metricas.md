## **Caso 1 – Assistente Virtual Multicanal (LLM + RAG)**

**Layers + Stacks + Métricas**

```
[ Canais & UI ]
- Web chat, App, WhatsApp (Twilio/Meta), e-mail
↓
[ API Gateway / BFF ]
- FastAPI, NGINX, Redis
↓
[ Orquestração Conversacional ]
- LangChain, LangGraph
↓
[ Tools/Agents ]
- CRM, Core Banking, OCR (AWS Textract, Tesseract)
↓
[ LLM & Guardrails ]
- OpenAI GPT-4, pydantic guards, PII check
↓
[ RAG ]
- Azure Cognitive Search, Weaviate, BERT/Sentence-Transformers
↓
[ Dados & Integrações ]
- PostgreSQL, S3/Blob, RabbitMQ
↓
[ Observabilidade | Segurança | DevOps | Testes/MLOps ]
- OpenTelemetry, Prometheus/Grafana, OAuth2/OIDC, Key Vault
- Docker, Kubernetes (AKS), Terraform, GitHub Actions
- Pytest, Locust, ragas, MLflow
```

**Métricas-Chave**

* Negócio: **–65% TMA**, **>90% acurácia**, **10k+ conexões simultâneas**
* Técnico: **p95 < 800ms**, **99,98% uptime**

---

## **Caso 2 – Agente Autônomo para Documentos Jurídicos**

**Layers + Stacks + Métricas**

```
[ Ingestão & OCR ]
- Azure Cognitive Services, Tesseract
↓
[ Pipeline NLP ]
- spaCy, HuggingFace Transformers, PyTorch
↓
[ API & Backoffice ]
- FastAPI, React/FastAPI-admin, JWT
↓
[ Busca Semântica / Indexação ]
- ElasticSearch, Sentence-BERT
↓
[ Armazenamento & Eventos ]
- PostgreSQL, S3/Blob, RabbitMQ/Celery
↓
[ Observabilidade | Segurança | DevOps | Testes/MLOps ]
- OpenTelemetry, Prometheus/Grafana, Vault/Key Vault
- Docker, Kubernetes, Terraform, GitHub Actions
- Pytest, Great Expectations, Locust, MLflow, DVC
```

**Métricas-Chave**

* Negócio: **92% precisão**, **3 dias → 6h** de processamento, **erro humano < 5%**
* Técnico: **+1.200 docs/dia**, **FP < 5%**

---

## **Caso 3 – Chat Operacional IoT (Diagnóstico + Predição)**

**Layers + Stacks + Métricas**

```
[ Canais & UI (Chat) ]
- Chat web/app, notificações
↓
[ BFF / API ]
- FastAPI, NGINX, Redis
↓
[ Orquestração ]
- LangChain Tools
↓
[ Modelos de Predição / Anomalias ]
- scikit-learn, PyTorch, Feast
↓
[ Streams & Timeseries ]
- Kafka, Flink, TimescaleDB, pgvector
↓
[ RAG técnico + Catálogos ]
- Sentence-BERT, Weaviate
↓
[ Observabilidade | Segurança | DevOps | Testes/MLOps ]
- Prometheus/Grafana, Loki, mTLS, RBAC, Vault
- Kubernetes (EKS), Helm, Terraform, Jenkins
- Pytest, Locust, MLflow
```

**Métricas-Chave**

* Negócio: **48h de antecedência na detecção**, **–30% paradas não planejadas**
* Técnico: **20k eventos/s**, **87% acurácia preditiva**
