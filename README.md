# CineData Analytics — Pipeline de Engenharia de Dados

Projeto desenvolvido no contexto do **Rocket Lab 2026.2 — Engenharia de Dados**, com o objetivo de construir um pipeline de dados end-to-end utilizando o Databricks.

A solução organiza dados de filmes provenientes de bases TMDB/IMDb utilizando a **Arquitetura Medalhão**, passando pelas camadas **Bronze, Silver e Gold**.

Além da preparação dos dados para análises de negócio, o projeto também gera uma tabela de contexto destinada ao uso em aplicações de **Inteligência Artificial / RAG (Retrieval-Augmented Generation)**.

---

## Arquitetura

O pipeline segue a Arquitetura Medalhão:

```text
               CSVs + API Banco Central
                         │
                         ▼
                  ┌─────────────┐
                  │   LANDING   │
                  └──────┬──────┘
                         │
                         ▼
                  ┌─────────────┐
                  │   BRONZE    │
                  │ Dados Brutos│
                  └──────┬──────┘
                         │
                         ▼
                  ┌─────────────┐
                  │   SILVER    │
                  │Dados Tratados│
                  └──────┬──────┘
                         │
                         ▼
                  ┌─────────────┐
                  │    GOLD     │
                  │Star Schema +│
                  │GenAI Context│
                  └─────────────┘
```
## Estrutura do projeto

├── Landing_to_Bronze.ipynb

├── Bronze_to_Silver.ipynb

├── Silver_to_Gold.ipynb

├── job.yaml

├── job_success.png

└── README.md

### Landing_to_Bronze.ipynb

- Responsável pela ingestão dos dados brutos para a camada Bronze.

### Bronze_to_Silver.ipynb

- Responsável pela limpeza, padronização, tipagem, deduplicação e aplicação das regras de negócio.

### Silver_to_Gold.ipynb

- Responsável pela construção do modelo dimensional, tabelas-ponte, tabela fato, contexto para GenAI e consultas analíticas.

### job.yaml

- Definição exportada do Databricks Workflow utilizado para orquestrar o pipeline.
