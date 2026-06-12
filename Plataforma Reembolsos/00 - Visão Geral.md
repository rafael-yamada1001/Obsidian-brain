---
tags: [projeto, reembolsos]
criado: 2026-06-12
---

# Plataforma de Reembolsos + Site Institucional

Solução para empresa de serviços técnicos em usinas, construída em **2026-06-12**.
Repositório: `C:\Repositories\empresa` (git, commit inicial `47fd026`).

## O problema

Técnicos que prestam serviço em usinas geram despesas de campo (alimentação, combustível, hospedagem, pedágio). **Houve abuso no passado**, então o fluxo tem separação de funções e trilha de auditoria completa.

## Fluxo vigente (desde 2026-06-12)

**Administrativo lança → dono assina → financeiro paga.**
Os técnicos **não usam o sistema**: entregam os extratos ao administrativo, que digita tudo. Técnico é só um cadastro (nome + chave PIX de destino). O nº de assinaturas de dono é configurável (padrão **1**). Papéis: `administrativo`, `aprovador` (dono), `financeiro`, `admin` (faz tudo).

## Os dois produtos

| Produto | Subdomínio | Stack | Pasta |
|---|---|---|---|
| Sistema de reembolsos | `app.empresa.com.br` | .NET 8 + React PWA + PostgreSQL | `/api` + `/portal` |
| Site institucional | `www.empresa.com.br` | HTML/CSS estático | `/site` |

## Mapa da documentação

- [[01 - Arquitetura]] — subdomínios, containers, estrutura do repositório
- [[02 - Modelo de Dados]] — tabelas, tipos, índices
- [[03 - Máquina de Estados]] — o coração do sistema; regras e testes
- [[04 - API Endpoints]] — rotas, papéis e autorização
- [[05 - Portal React]] — telas por papel, PWA, compressão de imagem
- [[06 - Site Institucional]] — páginas, SEO local, schema.org
- [[07 - Infra e Deploy]] — docker-compose, nginx, Let's Encrypt
- [[08 - Runbook]] — como subir, credenciais seed, problemas conhecidos

## Status de verificação (2026-06-12)

- ✅ `dotnet build` sem erros/warnings
- ✅ **69 testes xUnit passando** (máquina de estados + validador PIX)
- ✅ Migration EF Core `Initial` gerada e aplicada num Postgres real
- ✅ Fluxo completo testado via HTTP: criar → bloquear envio sem comprovante (422) → anexar → enviar → 1ª aprovação → bloqueio de dupla aprovação do mesmo aprovador → 2ª aprovação em lote → transição automática p/ FINANCEIRO → exportar CSV → pagar (chave PIX congelada) → audit log completo
- ✅ Isolamento entre técnicos (404 para despesa alheia)
- ✅ Validação de chave PIX (CPF com dígito verificador)
- ✅ `npm run build` do portal OK (197 kB JS / 62 kB gzip)
