# Recursos

Links, artigos, ferramentas e referencias uteis.

---

## Robin - IA para Investigacao OSINT na Dark Web

**GitHub:** https://github.com/apurvsinghgautam/robin
**Foco em Sec:** https://comunidade.focoemsec.com/c/investigacao-digital/como-criar-sua-propria-ia-para-investigacao-robin-para-osint-9a3dfd1a-d915-4618-8971-de9d34822fbe

### O que e?
Ferramenta open-source com IA para investigacoes OSINT na dark web. Usa LLMs (GPT-4, Claude, Gemini, Ollama local) para refinar queries, fazer scraping de 15+ motores de busca .onion em paralelo e gerar sumarios de inteligencia automaticamente.

### Fluxo
Query do usuario - LLM refina a busca - Tor roteia o trafego - 15+ motores dark web consultados - Scraping paralelo com threading - LLM filtra e sumariza - Relatorio com IOCs extraidos

### IOCs extraidos automaticamente
- IPs e dominios .onion
- E-mails expostos
- Hashes (MD5, SHA256)
- Enderecos cripto (BTC, ETH, Monero)
- Credenciais vazadas

### Instalacao (Linux/WSL)
apt install tor
service tor start
pip install robin-osint
export OPENAI_API_KEY=sua-chave

### Exemplos de uso
Busca simples: robin cli -m gpt-4o -q ransomware payments
Com IOCs: robin cli -m gpt-4o -q leaked credentials brazil -t 16 --extract-iocs --format both
Interface web: robin ui

### Modelos suportados
OpenAI (GPT-4o/4.1), Anthropic (Claude 3.5/3.7), Google (Gemini), Local (Ollama - Llama, Mistral)

### Casos de uso legitimos
- Investigacao de vazamentos de dados corporativos
- Threat intelligence e monitoramento
- Pesquisa em seguranca ofensiva
- CTF e treinamentos de red team

---

## DeepHat - IA Sem Restricoes para Ciberseguranca

**App:** https://app.deephat.ai/
**Site:** https://www.deephat.ai/
**Ollama:** https://ollama.com/DeepHat

### O que e?
Modelo da Kindo (antigo WhiteRabbitNeo) treinado especificamente para seguranca ofensiva e defensiva, sem os guardrails dos modelos comerciais. Responde requests tecnicos que GPT-4 e Claude recusam.

### Por que existe?
Modelos como GPT-4 e Claude recusam tasks de seguranca ofensiva: escrever exploits, analisar malware, simular ataques, raciocinar sobre TTPs. DeepHat nao recusa - foi treinado com vetores de ataque reais, tarefas de red team, sinais da dark web e cenarios multi-etapa de comprometimento.

### Comparativo de capacidades
Escrever exploit:       GPT-4/Claude recusa    |  DeepHat responde
Analise de malware:     GPT-4/Claude parcial   |  DeepHat completa
Red team TTPs:          GPT-4/Claude recusa    |  DeepHat responde
CTF writeups:           GPT-4/Claude parcial   |  DeepHat completo
Chain de ataque:        GPT-4/Claude recusa    |  DeepHat raciocina

### DeepHat v2 - Benchmarks
- 30B parametros - supera modelos de 120B em tarefas de seguranca
- Performance superior ao GPT-OSS-120B em CTF profissional
- Raciocina cadeias completas: foothold - escalada - persistencia - exfiltracao
- Otimizado para execucao agêntica (age com autonomia em tarefas longas)

### Como usar
1. Interface web: criar conta em app.deephat.ai
2. Local via Ollama:
   ollama pull deephat
   ollama run deephat

---

## Fontes
- https://github.com/apurvsinghgautam/robin
- https://voodootomato.medium.com/robin-ai-dark-web-research-tool-complete-installation-and-usage-guide-5171a1d917e7
- https://www.deephat.ai/
- https://ollama.com/DeepHat
