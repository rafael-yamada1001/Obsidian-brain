# Engenharia de Dados — Plano Estratégico

**Curso:** [Formação Engenharia de Dados: Domine Big Data 2026](https://www.udemy.com/course/engenheiro-de-dados/)
**Total de vídeo:** ~22h | **Com prática estimada:** ~50–60h
**Ritmo:** Flexível — sessões paralelas ao trabalho

---

## Visão Geral do Curso

| # | Seção | Aulas | Duração | Fase |
|---|-------|-------|---------|------|
| 1 | Introdução | 13 | 1h 42min | 🟦 1 |
| 2 | Aspectos Gerais sobre Engenharia de Dados | 20 | 2h 52min | 🟦 1 |
| 3 | Criando conta e Ambiente no AWS | 5 | 29min | 🟦 1 |
| 4 | Armazenamentos de dados distribuídos - S3 | 6 | 49min | 🟦 1 |
| 5 | Modelo Relacional e SQL - Postgres e EC2 | 23 | 2h 33min | 🟨 2 |
| 6 | Modelo Dimensional - Postgres e EC2 | 24 | 2h 21min | 🟨 2 |
| 7 | Data Warehouse Moderno e Data Lake - Redshift | 13 | 1h 15min | 🟨 2 |
| 8 | Fundamentos de NoSQL | 5 | 19min | 🟧 3 |
| 9 | NoSQL Orientado a Documento - MongoDB e EC2 | 9 | 1h 6min | 🟧 3 |
| 10 | NoSQL Chave-Valor - Redis e EC2 | 13 | 1h 28min | 🟧 3 |
| 11 | Introdução ao Ecossistema Hadoop | 4 | 32min | 🟥 4 |
| 12 | Spark com Databricks | 8 | 1h 7min | 🟥 4 |
| 13 | Engenharia de Dados com Python | 8 | 1h 1min | 🟥 4 |
| 14 | Aplicações em Streaming - Kinesis | 6 | 57min | 🟪 5 |
| 15 | ETL e Data Crawler - Glue e Athena | 8 | 1h 8min | 🟪 5 |
| 16 | Gerenciando Serviços pela CLI | 6 | 44min | 🟪 5 |
| 17 | Projeto Final I | 11 | 45min | 🟩 6 |
| 18 | Projeto Final II | 8 | 48min | 🟩 6 |

---

## Fases Estratégicas

### 🟦 FASE 1 — Fundação (~6h de vídeo)
> Contexto + ambiente configurado. Não avance sem ter a AWS funcionando.

- [x] **Seção 1 — Introdução** *(1h 42min)* ✅ 2026-04-23 → [[Seção 1 - Introdução]] · 🗺️ [[Seção 1 - Introdução.canvas|Canvas]]
  - O que faz um Engenheiro de Dados
  - Diferença DE vs DS vs DBA
- [ ] **Seção 2 — Aspectos Gerais** *(2h 52min)*
  - OLTP vs OLAP
  - Tipos de dados e arquiteturas
  - Panorama do mercado
- [ ] **Seção 3 — AWS: Conta e Ambiente** *(29min)*
  - Criar conta AWS Free Tier
  - Configurar IAM, regiões
- [ ] **Seção 4 — S3** *(49min)*
  - Criar buckets, upload, permissões
  - S3 como base do Data Lake

**✅ Meta:** AWS configurada + entender onde cada ferramenta se encaixa

---

### 🟨 FASE 2 — Dados Relacionais (~6h de vídeo)
> Base de tudo. SQL ruim = pipeline ruim.

- [ ] **Seção 5 — SQL + PostgreSQL no EC2** *(2h 33min)*
  - DDL, DML, SELECT completo
  - JOINs, subqueries, agregações
  - Window Functions
- [ ] **Seção 6 — Modelo Dimensional** *(2h 21min)*
  - Star Schema e Snowflake
  - Tabelas Fato e Dimensão
  - Construir um DW simples
- [ ] **Seção 7 — Data Warehouse + Data Lake no Redshift** *(1h 15min)*
  - Armazenamento colunar
  - Particionamento e compressão
  - Redshift na prática

**✅ Meta:** Escrever queries SQL complexas e modelar um DW no Redshift

---

### 🟧 FASE 3 — NoSQL (~3h de vídeo)
> Complemento ao relacional. Dados que não cabem em tabelas.

- [ ] **Seção 8 — Fundamentos de NoSQL** *(19min)*
  - Quando usar NoSQL vs SQL
  - Tipos: documento, chave-valor, grafo, colunar
- [ ] **Seção 9 — MongoDB no EC2** *(1h 6min)*
  - CRUD em documentos JSON
  - Queries e índices
- [ ] **Seção 10 — Redis no EC2** *(1h 28min)*
  - Estruturas de dados in-memory
  - Casos de uso: cache, filas, sessões

**✅ Meta:** Saber escolher entre SQL/MongoDB/Redis para cada cenário

---

### 🟥 FASE 4 — Big Data e Processamento (~3h de vídeo)
> O coração da engenharia de dados em escala.

- [ ] **Seção 11 — Hadoop** *(32min)*
  - HDFS e MapReduce (contexto histórico)
  - Por que o Spark dominou
- [ ] **Seção 12 — Spark com Databricks** *(1h 7min)*
  - RDDs e DataFrames
  - Spark SQL e transformações
  - Rodar jobs no Databricks
- [ ] **Seção 13 — Engenharia de Dados com Python** *(1h 1min)*
  - Pandas na engenharia de dados
  - Conexão com DBs (SQLAlchemy, pymongo)
  - Automatizar pipelines com scripts

**✅ Meta:** Processar um dataset grande com Spark no Databricks + script Python do pipeline

---

### 🟪 FASE 5 — Pipelines e Automação (~3h de vídeo)
> Junta tudo em fluxos de produção.

- [ ] **Seção 14 — Streaming com Kinesis** *(57min)*
  - Real Time vs Near Real Time
  - Produtores e consumidores no Kinesis
  - Casos de uso reais
- [ ] **Seção 15 — ETL: Glue e Athena** *(1h 8min)*
  - AWS Glue para transformação
  - Athena para consultas no S3
  - Data Crawlers automáticos
- [ ] **Seção 16 — CLI AWS** *(44min)*
  - Gerenciar todos os serviços via terminal
  - Scripts de automação

**✅ Meta:** Pipeline ETL rodando de ponta a ponta com Glue + Athena + S3

---

### 🟩 FASE 6 — Projetos Finais (~1h 30min de vídeo)
> Portfólio real para o mercado.

- [ ] **Projeto Final I** *(45min)* — Construção de um Data Lake
  - Arquitetura completa no S3
  - Camadas Bronze → Silver → Gold
  - Documentar no vault + GitHub
- [ ] **Projeto Final II** *(48min)* — Pipeline de Extração e Transformação
  - Extração de fonte real
  - Transformação com Python/Glue
  - Carga no Redshift/S3
  - Documentar no vault + GitHub

**✅ Meta:** 2 projetos no GitHub prontos para mostrar em entrevistas

---

## Como usar o vault durante os estudos

Após cada seção, crie uma nota filha com o que aprendeu:

| Seção | Nota |
|-------|------|
| SQL | [[SQL]] |
| Spark | [[Spark]] |
| ETL | [[ETL]] |
| Python | [[Python para Dados]] |

> Me mande a nota e eu reviso, completo e sugiro exercícios.

---

## Progresso

| Fase | Seções | Status | Última sessão |
|------|--------|--------|---------------|
| 🟦 1 — Fundação | 1, 2, 3, 4 | 🔄 Em andamento | 2026-04-23 |
| 🟨 2 — Dados Relacionais | 5, 6, 7 | ⬜ Não iniciada | — |
| 🟧 3 — NoSQL | 8, 9, 10 | ⬜ Não iniciada | — |
| 🟥 4 — Big Data | 11, 12, 13 | ⬜ Não iniciada | — |
| 🟪 5 — Pipelines | 14, 15, 16 | ⬜ Não iniciada | — |
| 🟩 6 — Projetos | 17, 18 | ⬜ Não iniciada | — |

**Horas de vídeo assistidas:** 0 / ~22h
**Seções concluídas:** 0 / 18
