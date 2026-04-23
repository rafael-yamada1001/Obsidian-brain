# 🎮 Life RPG — Sistema de Gamificação Pessoal
**Capturado em:** 2026-04-23
**Status:** 💡 Ideia → sendo elaborada em [[Projetos/Life RPG.md]]

---

## A Ideia Central

Transformar metas da vida real em um RPG:
- Cada área da vida é um **atributo do personagem**
- Completar tarefas/hábitos ganha **XP**
- XP suficiente = **Level Up**
- Metas grandes são **missões**
- Hábitos diários são **missões diárias**
- Sequências são **streaks** que dão bônus

---

## Atributos do Personagem (Rafael)

| Atributo | Representa | Cor |
|----------|-----------|-----|
| 🧠 **Intelecto** | Estudos, cursos, leitura | Azul |
| 💪 **Força** | Academia, saúde, corpo | Vermelho |
| 💼 **Ofício** | Trabalho, produtividade | Amarelo |
| 🤖 **Tech** | IA, programação, ferramentas | Verde |
| 🎯 **Disciplina** | Consistência, streaks | Roxo |

---

## Sistema de XP

| Ação | XP |
|------|----|
| Assistir aula do curso | +10 XP Intelecto |
| Sessão de estudo prática (+1h) | +20 XP Intelecto |
| Ir à academia | +15 XP Força |
| Semana perfeita academia (4x) | +50 XP Força + Bônus Disciplina |
| Usar IA produtivamente no trabalho | +10 XP Tech |
| Completar módulo do curso | +100 XP Intelecto |
| Completar projeto do portfólio | +300 XP Intelecto + Tech |
| Streak 7 dias de estudo | +50 XP Disciplina |
| Streak 30 dias academia | +200 XP Força |

---

## Tabela de Níveis

| Nível | XP necessário | Título |
|-------|--------------|--------|
| 1 | 0 | Iniciante |
| 2 | 200 | Aprendiz |
| 3 | 500 | Praticante |
| 4 | 1.000 | Especialista |
| 5 | 2.000 | Mestre |
| 6 | 4.000 | Grão-Mestre |
| 7 | 8.000 | Lenda |

---

## Conquistas (Achievements)

| Conquista | Condição | Recompensa |
|-----------|----------|-----------|
| 🎓 Primeiro Passo | Concluir Seção 1 do curso | +50 XP |
| 💪 Sem Desculpas | 4x academia em 1 semana | +50 XP |
| 🔥 Em Chamas | 7 dias seguidos de estudo | +100 XP |
| 🏗️ Construtor | Primeiro projeto no GitHub | +200 XP |
| 🤖 Prompt Master | Completar Nível 3 de IA | +150 XP |
| 🚀 Data Engineer | Concluir curso completo | +500 XP |
| 💎 Inabalável | 30 dias de academia | +300 XP |

---

## Como Implementar

### Versão 1 — Markdown no Vault (simples, já dá pra fazer)
- Arquivo `Metas/PersonagemRafael.md` com os stats
- Slash command `/xp` que soma XP e verifica level up
- Claude atualiza automaticamente ao final de cada sessão

### Versão 2 — Script Python (médio prazo)
- Script lê o vault e calcula XP automaticamente
- Detecta streaks no histórico de sessões
- Gera relatório semanal

### Versão 3 — App/Dashboard (longo prazo)
- Interface visual com gráficos de evolução
- Notificações de conquistas
- Histórico de progresso ao longo do tempo

---

## Conexão com Engenharia de Dados 🎯
> Este projeto pode ser um portfólio real!

- **Dados:** o vault é a fonte de dados (markdown → estruturado)
- **Pipeline:** script Python lê notas, extrai eventos, calcula XP
- **Armazenamento:** salva histórico em SQLite ou Parquet
- **Visualização:** dashboard com Streamlit ou Power BI
- **Automação:** agente Claude atualiza o vault em tempo real

**Isso vira um projeto de Engenharia de Dados aplicado à própria vida.**
