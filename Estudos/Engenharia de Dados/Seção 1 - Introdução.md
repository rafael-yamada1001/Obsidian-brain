# Seção 1 — Introdução
**Concluída em:** 2026-04-23
**Duração:** 1h 42min | 15 aulas

---

## O que é Engenharia de Dados?

O Engenheiro de Dados (DE) é o profissional que **constrói e mantém a infraestrutura** que permite que os dados fluam, sejam armazenados e estejam disponíveis para análise.

**Diferença entre os perfis:**
| Perfil | Foco |
|--------|------|
| Engenheiro de Dados | Pipelines, armazenamento, infraestrutura |
| Cientista de Dados | Modelos, estatística, ML |
| Analista de Dados | Relatórios, visualização, BI |
| DBA | Administração e performance de bancos |

---

## O que é Big Data?

Definido pelos **5 Vs:**
- **Volume** — quantidade massiva de dados
- **Velocidade** — dados gerados e processados em alta velocidade
- **Variedade** — estruturados, semi-estruturados e não-estruturados
- **Veracidade** — qualidade e confiabilidade dos dados
- **Valor** — utilidade real dos dados para o negócio

---

## Estruturas de Dados

| Tipo | Exemplos | Onde fica |
|------|----------|-----------|
| Estruturado | Tabelas SQL, planilhas | Banco relacional |
| Semi-estruturado | JSON, XML, CSV | MongoDB, S3 |
| Não-estruturado | Imagens, vídeos, logs | Data Lake, S3 |

---

## Clássico VS Big Data

| Aspecto | Clássico (OLTP) | Big Data |
|---------|-----------------|----------|
| Volume | GB / TB | TB / PB |
| Processamento | Vertical (+ RAM, + CPU) | Horizontal (+ máquinas) |
| Tecnologia | Oracle, SQL Server, PostgreSQL | Hadoop, Spark, S3 |
| Latência | Tempo real | Batch ou Near Real Time |

---

## Operacional VS Analítico

| | Operacional (OLTP) | Analítico (OLAP) |
|--|-------------------|-----------------|
| Objetivo | Registrar transações | Apoiar decisões |
| Exemplos | ERP, e-commerce, banco | DW, Data Lake, BI |
| Queries | Simples e frequentes | Complexas e pesadas |
| Modelo | Normalizado (3FN) | Dimensional (Star Schema) |

---

## Teorema de CAP

Em sistemas distribuídos, só é possível garantir **2 dos 3** ao mesmo tempo:

- **C**onsistency — todos os nós veem os mesmos dados ao mesmo tempo
- **A**vailability — o sistema sempre responde
- **P**artition Tolerance — o sistema funciona mesmo com falha de rede

**Exemplos:**
- MongoDB → AP (disponibilidade + tolerância a partição)
- PostgreSQL → CP (consistência + tolerância a partição)

---

## Conceitos Importantes

- **Data Lake** — repositório bruto de dados em qualquer formato (S3)
- **Data Warehouse** — dados organizados e otimizados para análise (Redshift)
- **Orquestração** — gerenciamento do fluxo de pipelines (Airflow, Glue)
- **Linhagem de dados** — rastrear origem e transformações dos dados
- **Data Quality** — garantir que os dados são corretos, completos e consistentes
- **Data Contracts** — acordos formais sobre formato e qualidade entre times
- **SLA / SLO** — acordos de nível de serviço para entrega e qualidade de dados

---

## Dúvidas para revisar
> Anote aqui qualquer dúvida que surgir ao estudar esta seção
