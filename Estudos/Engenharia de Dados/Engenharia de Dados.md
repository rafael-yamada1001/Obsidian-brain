# Engenharia de Dados — Plano Estratégico

**Curso:** [Formação Engenharia de Dados: Domine Big Data 2026](https://www.udemy.com/course/engenheiro-de-dados/)
**Ritmo:** Flexível — sessões paralelas ao trabalho
**Carga sugerida:** 2–3 sessões/dia de 30–60 min cada

---

## Por que essa ordem importa

```
Fundamentos → SQL → Python → Dimensional → DW/Lake
                                              ↓
                    NoSQL ←── Spark ←── Hadoop
                                              ↓
                              ETL → Streaming → Projetos
```

Cada módulo é pré-requisito do próximo. Não pule etapas.

---

## Trilha Estratégica

### 🟦 FASE 1 — Base (Semanas 1–3)
> Sem essa base, nada à frente faz sentido.

| # | Módulo | Foco |
|---|--------|------|
| 1 | Conceitos e Fundamentos | OLTP vs OLAP, papel do DE, tipos de dados |
| 2 | Cloud + CLI AWS | Criar conta AWS, navegar no console, AWS CLI básico |
| 3 | Modelo Relacional e SQL | SELECT, JOIN, agregações, Window Functions no PostgreSQL |

**Meta da fase:** Conseguir responder queries SQL complexas e navegar na AWS sem travar.

---

### 🟨 FASE 2 — Fundação Técnica (Semanas 4–6)
> Aqui você vira produtivo com código e modelos de dados.

| # | Módulo | Foco |
|---|--------|------|
| 4 | Python para Engenharia de Dados | Pandas, conexão com DBs, automação de tarefas |
| 5 | Modelo Dimensional | Star Schema, Fato vs Dimensão, construir um DW simples |

**Meta da fase:** Escrever um script Python que lê dados, transforma e carrega em um banco.

---

### 🟧 FASE 3 — Armazenamento Moderno (Semanas 7–9)
> Onde os dados vivem em produção.

| # | Módulo | Foco |
|---|--------|------|
| 6 | Data Warehouse Moderno | Redshift, armazenamento colunar, particionamento |
| 7 | Data Lake | S3, camadas Bronze/Silver/Gold, formato Parquet |
| 8 | NoSQL | MongoDB (documentos), Redis (cache/chave-valor) |

**Meta da fase:** Ter dados fluindo do S3 para o Redshift com transformação básica.

---

### 🟥 FASE 4 — Big Data e Processamento (Semanas 10–13)
> O coração da engenharia de dados em escala.

| # | Módulo | Foco |
|---|--------|------|
| 9 | Ecossistema Hadoop | HDFS, MapReduce, Hive — entender a história |
| 10 | Apache Spark | DataFrames, Spark SQL, transformações, Databricks |
| 11 | ETL e Data Crawlers | AWS Glue, Athena, pipelines de extração e carga |
| 12 | Streaming | Kinesis, Real Time vs Near Real Time, casos de uso |

**Meta da fase:** Processar um dataset grande no Databricks com Spark e entregar no Data Lake.

---

### 🟩 FASE 5 — Projetos Finais (Semanas 14–16)
> Portfólio real para mostrar no mercado.

| # | Projeto | Descrição |
|---|---------|-----------|
| P1 | Construção de um Data Lake | Ingestão → Bronze → Silver → Gold no S3 |
| P2 | Pipeline ETL Completo | Extração → Transformação → Carga com Python + Glue |

**Meta da fase:** Dois projetos documentados no GitHub + vault prontos para portfólio.

---

## Ferramentas por Fase

| Fase | Ferramentas |
|------|-------------|
| Base | PostgreSQL, AWS Console, AWS CLI |
| Fundação | Python, Pandas, SQLAlchemy |
| Armazenamento | S3, Redshift, RDS, MongoDB, Redis |
| Big Data | Hadoop, Spark, Databricks, Glue, Athena, Kinesis |
| Projetos | Tudo acima integrado |

---

## Como estudar de forma flexível (sem horário fixo)

- **Sessão curta (30 min):** Assistir aula + anotar conceito principal
- **Sessão média (1h):** Aula + reproduzir o exemplo prático
- **Sessão longa (2h+):** Módulo completo + exercício próprio

> Dica: use o campo "Última sessão" abaixo para não perder o fio. Antes de abrir o curso, releia a última anotação.

---

## Progresso

| Fase | Status | Última sessão |
|------|--------|---------------|
| 1 — Base | ⬜ Não iniciada | — |
| 2 — Fundação Técnica | ⬜ Não iniciada | — |
| 3 — Armazenamento Moderno | ⬜ Não iniciada | — |
| 4 — Big Data | ⬜ Não iniciada | — |
| 5 — Projetos | ⬜ Não iniciada | — |

- **Horas totais:** 0h
- **Módulos concluídos:** 0 / 12

---

## Notas de Estudo
> Crie uma nota por módulo: ex. [[SQL]], [[Spark]], [[ETL]]
