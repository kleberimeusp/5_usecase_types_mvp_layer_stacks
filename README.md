# Arquitetura – C4 (Structurizr)

Este repositório contém três diagramas do **C4 Model** (System Context → Container → Component) e suas respectivas **legendas (keys)**, gerados via **Structurizr DSL**.
A sequência das imagens foi pensada para contar a arquitetura de ponta a ponta, do macro ao micro.

## Sumário

* [Como ler os diagramas](#como-ler-os-diagramas)
* [1) System Context (SYS-CTX)](#1-system-context-sys-ctx)
* [2) Container View (CNT-AI)](#2-container-view-cnt-ai)
* [3) Component View (CMP-LLM)](#3-component-view-cmp-llm)
* [Boas práticas e próximos passos](#boas-práticas-e-próximos-passos)

---

## Como ler os diagramas

1. **Abra na ordem**: System Context → Container → Component.
2. Em cada nível, **verifique a legenda** (imagem `*-key.png`) para entender as cores, formas e significados.
3. **Setas** indicam relações (chamadas, dependências, fluxos).
4. **Caixas pontilhadas** costumam indicar limites (ex.: boundary de um sistema).

---

## 1) System Context (SYS-CTX)

**Arquivos**

* `structurizr-SYS-CTX.png`
* `structurizr-SYS-CTX-key.png` (legenda)

**Imagens**
![System Context](./structurizr-SYS-CTX.png)
![System Context – Key](./structurizr-SYS-CTX-key.png)

**Objetivo do diagrama**
Mostrar **quem** interage com a plataforma e **quais sistemas externos** ela toca. É a visão “satélite” do ecossistema.

**Elementos principais**

* **End User**: pessoa que usa o chat, envia documentos ou consome insights IoT.
* **AI Multi-Case Platform**: sistema central (o que estamos desenhando).
* **Sistemas externos** (exemplos):

  * **CRM System** (contexto do cliente)
  * **Core Banking** (operações seguras)
  * **Legal Docs DB** (metadados contratuais)
  * **IoT Sensor Network** (eventos/sensores em streaming)
  * **Notification Service** (alertas para times de campo)

**O que observar**

* **Escopo**: a plataforma AI está no centro; tudo ao redor é ator ou sistema externo.
* **Relações**: setas indicam direção do uso/integração (ex.: plataforma lê do CRM; envia alertas via Notification).

---

## 2) Container View (CNT-AI)

**Arquivos**

* `structurizr-CNT-AI.png`
* `structurizr-CNT-AI-key.png` (legenda)

**Imagens**
![Container View](./structurizr-CNT-AI.png)
![Container View – Key](./structurizr-CNT-AI-key.png)

**Objetivo do diagrama**
Exibir os **principais containers** (aplicativos e armazenamentos) que compõem a plataforma, e como se comunicam.

**Containers (resumo)**

* **BFF/API Gateway**: recebe requisições do usuário e expõe endpoints (ex.: FastAPI).
* **Orchestration Engine**: orquestra fluxos (LLM, NLP, OCR, IoT) – ex.: LangChain/LangGraph.
* **Vector Store**: guarda embeddings para busca semântica (Weaviate/Elastic/pgvector).
* **LLM Service**: raciocínio conversacional e ferramentas (Azure OpenAI/Bedrock/Vertex/watsonx).
* **OCR Service**: extração de texto de PDFs/imagens (Form Recognizer/Textract/Document AI).
* **ML Models**: classificação, anomalia, predição (PyTorch/Scikit-learn).
* **Messaging/Streaming**: assíncrono e streams (RabbitMQ/Kafka).
* **Storage**: objetos e relacional (Blob/S3/GCS/IBM COS + PostgreSQL/Db2).
* **Observability**: métricas, traços e logs (Prometheus/Grafana/OTel).
* **Secrets Management**: cofres e KMS.

**Fluxos típicos (exemplos)**

* **Assistente (LLM+RAG)**: `BFF → Orchestration → LLM Service` (consulta) + `Vector Store` (recuperação semântica) + `Storage` (histórico).
* **Documentos Jurídicos**: `BFF → Orchestration → OCR Service → ML Models` e indexação no `Vector Store`.
* **IoT**: `IoT Sensor Network → Messaging/Streaming → ML Models` (detecção/predição) → `Notification Service`.

**O que observar**

* **Acoplamento fraco** via mensageria.
* **Separação de responsabilidades** por container.
* **Observabilidade e segredos** como **first-class citizens**.

---

## 3) Component View (CMP-LLM)

**Arquivos**

* `structurizr-CMP-LLM.png`
* `structurizr-CMP-LLM-key.png` (legenda)

**Imagens**
![Component View – LLM](./structurizr-CMP-LLM.png)
![Component View – LLM – Key](./structurizr-CMP-LLM-key.png)

**Objetivo do diagrama**
Entrar no **container “LLM Service”** e mostrar seus **principais componentes internos**.

**Componentes (exemplo)**

* **Prompt Handler**: construção de prompts, injeção de contexto, guardrails (PII/políticas).
* **Embedding Generator**: geração de embeddings para documentos e queries.
* **Reranker**: reordena resultados da busca por relevância (Cross-Encoder).

**Fluxo típico**

1. A **Orchestration** envia a consulta e o contexto ao **Prompt Handler**.
2. Se necessário, o **Embedding Generator** é chamado para vetorizar.
3. Resultados recuperados do **Vector Store** são refinados pelo **Reranker**.
4. O **LLM** produz a resposta final com segurança e rastreabilidade (observabilidade ativa).

**O que observar**

* **Guardrails** aplicados cedo (no Prompt Handler).
* **RAG** explícito (Embedding + Reranker + Vector Store).
* Componentes **substituíveis** (multi-cloud / multi-model).

---

## Boas práticas e próximos passos

**Boas práticas**

* **Multi-cloud ready**: isolar integrações (LLM, OCR, busca) atrás de interfaces.
* **Reuso**: padronizar embeddings e API de vector store para trocar provedores sem refatorar.
* **Observabilidade total**: OTel em todas as rotas; SLOs por cenário (p95, custo/token, acurácia).
* **Segurança**: segredos em KMS/Key Vault; políticas de PII/PCI/PHI centralizadas (policy-as-code).
* **Infra como código**: Terraform + módulos reutilizáveis por cloud e região.
* **Pipelines imutáveis**: versionar prompts/modelos/datasets (MLflow/DVC).

**Próximos passos**

1. Publicar o **DSL** no repositório para rastreabilidade dos diagramas.
2. Anexar **KPIs de cada caso** (Assistente, Jurídico, IoT) como *properties* no Structurizr.
3. Adicionar **camadas de implantação (Deployment View)** por região (EUA/Canadá/EU).
4. Conectar este README ao **roadmap de rollout** (datas e gates de Go/No-Go).
