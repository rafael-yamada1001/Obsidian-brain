# Seção 2 — Aspectos Gerais sobre Engenharia de Dados

**Concluído em:** —
**Duração:** 2h 52min · 20 aulas · Fase 🟦 1

![[Mapa - Seção 2 - Aspectos Gerais.canvas]]

---

## Pipeline de Dados — Visão Geral

O fluxo padrão de qualquer pipeline de dados segue estas etapas:

```
Fonte → Ingestão → Processamento → Armazenamento → Servir → Consumo
```

| Etapa | O que faz | Ferramentas |
|-------|-----------|-------------|
| **Ingestão** | Captura dados da fonte (API, DB, evento) | Kafka, Kinesis, Airbyte |
| **Processamento** | Limpa, transforma, agrega | Spark, Glue, dbt |
| **Armazenamento** | Persiste dados processados | S3, Redshift, MongoDB |
| **Servir** | Disponibiliza para consumo | Athena, APIs, BI tools |
| **Consumo** | Usa os dados | Analistas, modelos ML, dashboards |

---

## Batch vs Streaming

| | Batch | Streaming |
|---|-------|-----------|
| **Quando processa** | Intervalos fixos (horário, diário) | Contínuo, evento a evento |
| **Latência** | Alta (minutos a horas) | Baixa (ms a segundos) |
| **Complexidade** | Baixa | Alta |
| **Custo** | Baixo | Alto |
| **Ferramentas** | Spark, Glue, cron | Kafka, Kinesis, Flink |
| **Caso de uso** | Relatórios diários, DW | Fraude em tempo real, IoT |

> Maioria dos sistemas usa os dois: streaming para captura, batch para processamento histórico.

---

## Arquitetura Lambda vs Kappa

**Lambda Architecture** — duas camadas paralelas:
- **Batch layer** → processa tudo, resultado preciso mas lento
- **Speed layer** → processa stream em tempo real, aproximado
- **Serving layer** → combina os dois para responder queries

**Kappa Architecture** — tudo como stream:
- Elimina a batch layer
- Reprocessa histórico repetindo o stream
- Mais simples, mas exige infra de stream madura

> Lambda = mais confiável, mais complexo. Kappa = mais simples, requer Kafka/Kinesis rodando bem.

---

## Papéis e Responsabilidades do DE

### O que o DE entrega?
- Pipelines confiáveis e escaláveis
- Dados disponíveis no prazo (SLA)
- Qualidade garantida (schema, nulos, duplicatas)
- Infraestrutura de dados na nuvem

### Com quem o DE trabalha?
```
Fonte de dados → [DE] → Cientista de Dados
                 [DE] → Analista de Dados
                 [DE] → Produto / negócio
```

---

## Panorama do Mercado

### Ferramentas por categoria

| Categoria | Open Source | Cloud AWS | Cloud outros |
|-----------|-------------|-----------|--------------|
| **Ingestão** | Kafka, Debezium | Kinesis, DMS | Pub/Sub (GCP) |
| **Processamento** | Spark, Flink | Glue, EMR | Dataflow (GCP) |
| **Armazenamento** | PostgreSQL, MongoDB | S3, Redshift | BigQuery (GCP) |
| **Orquestração** | Airflow, Prefect | Step Functions | Cloud Composer |
| **Transformação** | dbt | Glue | dbt cloud |
| **Observabilidade** | Great Expectations | CloudWatch | — |

### Salários e demanda (Brasil 2025)
- DE Junior: R$ 4k–8k
- DE Pleno: R$ 8k–15k
- DE Senior: R$ 15k–25k
- Demanda: crescendo, especialmente em fintechs, e-commerce, saúde

---

## Conceitos de Arquitetura Moderna

**Data Mesh** — dados descentralizados por domínio:
- Cada time de negócio é dono dos seus dados
- DE vira platform engineer, não centraliza tudo
- Requer cultura de dados madura

**Data Fabric** — camada de integração unificada:
- Automatiza movimento e acesso entre sistemas
- Usa metadados e ML para descoberta de dados

**Modern Data Stack:**
```
Fivetran/Airbyte → Snowflake/BigQuery → dbt → Metabase/Looker
(ingestão)          (armazenamento)    (transform)  (consumo)
```

---

## Dúvidas para revisar

- [ ] 

---

[[Engenharia de Dados]] · 🗺️ [[Mapa - Seção 2 - Aspectos Gerais.canvas|Mapa]]
