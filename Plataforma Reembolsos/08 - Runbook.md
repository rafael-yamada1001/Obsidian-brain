---
tags: [projeto, reembolsos, runbook]
---

# Runbook — Dev local e Operação

Parte de [[00 - Visão Geral]].

## Desenvolvimento local (Windows, sem Docker para o app)

```powershell
# 1. Banco
docker compose up -d postgres        # porta 5432 publicada no host

# 2. API (Development usa a JWT key do appsettings.Development.json)
cd api\src\Empresa.Api
$env:ASPNETCORE_ENVIRONMENT='Development'; dotnet run   # http://localhost:8080, Swagger em /swagger

# 3. Portal
cd portal
npm install; npm run dev             # http://localhost:5173 (proxy /api → 8080)

# 4. Testes
cd api; dotnet test                  # 69 testes
```

## Credenciais do seed (senha de todos: `Senha@123`)

| Papel | E-mail |
|---|---|
| Admin | admin@empresa.com.br |
| Aprovadores | aprovador1@ / aprovador2@empresa.com.br |
| Financeiro | financeiro@empresa.com.br |
| Técnicos | tecnico1@ / tecnico2@empresa.com.br |

⚠️ **Trocar as senhas em produção** (Admin → Usuários) e gerar `JWT_KEY` forte no `.env`.

## Roteiro de teste manual (validado em 2026-06-12 via HTTP)

1. Técnico cria despesa → `Rascunho`
2. Enviar sem foto (categoria exige) → **422 bloqueado** ✓
3. Anexar foto → enviar → `Enviada` ✓
4. Aprovador 1 aprova → `AprovadaParcial`; tentar de novo → bloqueado ✓
5. Aprovador 2 aprova (em lote) → **`Financeiro` automático** ✓
6. Financeiro exporta CSV (BOM UTF-8, `;`, valores `45,90`) ✓
7. Financeiro paga → `Paga`, chave PIX **congelada** (trocar a chave depois não altera o registro) ✓
8. Audit: `criou → anexou → enviou → aprovou → aprovou → transicao_automatica_financeiro → marcou_paga` ✓
9. Técnico 2 acessa despesa do técnico 1 → 404 ✓
10. Chave PIX: CPF válido aceito, inválido → 422 ✓

## Problemas conhecidos / pegadinhas

- **`dotnet run --no-build` após gerar migration**: a migration nova não está no binário antigo → `Migrate()` não cria as tabelas (`42P01 relation does not exist`). Rodar sem `--no-build`.
- **PowerShell 5.1 + JSON com acentos**: `Invoke-RestMethod` envia body como ISO-8859-1 → API devolve 400. Para testes manuais use strings ASCII ou PowerShell 7 / curl.
- **Porta do Postgres**: o compose publica `5432:5432` para dev local; em produção pode-se remover o mapeamento (containers falam pela rede interna).
- Claude Code/Electron: ver memória `ELECTRON_RUN_AS_NODE` se for lançar apps Electron a partir desta máquina.

## Onde mexer para…

| Quero… | Onde |
|---|---|
| Mudar prazo de lançamento | Portal Admin → Configurações (ou `PUT /api/configuracoes/prazo_lancamento_dias`) |
| Mudar limites/comprovante por categoria | Portal Admin → Categorias |
| Adicionar regra de negócio do fluxo | `Domain/DespesaWorkflow.cs` + teste em `DespesaWorkflowTests.cs` |
| Trocar template de e-mail | `Services/NotificacaoService.cs` |
| Migrar anexos p/ S3 | Implementar `IArquivoStorage` — ver [[07 - Infra e Deploy]] |
