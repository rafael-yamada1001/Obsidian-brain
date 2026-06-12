---
tags: [projeto, reembolsos, site]
---

# Site Institucional (www.empresa.com.br)

Parte de [[00 - Visão Geral]]. Pasta `/site` — **HTML/CSS estático puro** (sem build), mobile-friendly, identidade provisória sóbria (azul petróleo `#0f4c81` + cinza).

## Páginas

| Página | Conteúdo |
|---|---|
| `index.html` | Hero com proposta de valor, "O que fazemos" (3 cartões), diferenciais, faixa CTA WhatsApp |
| `servicos.html` | 6 serviços em cartões + "Como trabalhamos" (3 passos) |
| `sobre.html` | História/missão (placeholders) + compromissos + foto placeholder |
| `contato.html` | WhatsApp (`wa.me` com mensagem pré-preenchida), telefone `tel:`, e-mail `mailto:`, endereço, horário |

## Elementos transversais

- Header fixo com menu e botão **"Área do Técnico"** → `https://app.empresa.com.br`
- Botão WhatsApp **flutuante** em todas as páginas
- Footer com endereço/CNPJ placeholder

## SEO local

- `<title>`/`<meta description>` com `[Cidade]/[Região]` em todas as páginas
- `canonical`, Open Graph (`og:locale pt_BR`)
- **JSON-LD `schema.org/LocalBusiness`** na home: nome, endereço, telefone, e-mail, `areaServed`, horário
- Domínio nu `empresa.com.br` → 301 para `www` (no nginx)

## Conteúdo placeholder (substituir depois)

Tudo entre colchetes: `[Nome da Empresa]`, `[Cidade]`, `[CNPJ]`, telefones `+5500000000000` nos links `wa.me`, logo `[L]` e blocos `placeholder-img` para fotos. Buscar por `[` nos HTML para encontrar todos os pontos.
