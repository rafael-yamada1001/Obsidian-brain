---
tags: [projeto, reembolsos, api]
---

# API Endpoints

Parte de [[00 - Visão Geral]]. Base: `app.empresa.com.br/api` (dev: `localhost:8080/api`). Swagger em `/swagger` (somente Development).

**Autenticação:** JWT Bearer (12 h), claims `sub`, `email`, `nome`, `role`. Senhas com BCrypt.
**Autorização:** `[Authorize(Roles = …)]` em todos os endpoints; técnico só enxerga as próprias despesas (filtro server-side — despesa alheia retorna 404).

## Auth
| Método | Rota | Papéis |
|---|---|---|
| POST | `/api/auth/login` | público |
| GET | `/api/auth/me` | autenticado |

## Despesas — ciclo de vida
| Método | Rota | Papéis | Nota |
|---|---|---|---|
| POST | `/api/despesas` | tecnico | cria RASCUNHO |
| PUT | `/api/despesas/{id}` | tecnico | só RASCUNHO/REJEITADA |
| DELETE | `/api/despesas/{id}` | tecnico | só RASCUNHO |
| POST | `/api/despesas/{id}/enviar` | tecnico | valida comprovante + prazo; reenvio zera aprovações |
| POST | `/api/despesas/{id}/aprovar` | aprovador | 2ª aprovação → FINANCEIRO automático |
| POST | `/api/despesas/aprovar-lote` | aprovador | em massa; erros reportados por item |
| POST | `/api/despesas/{id}/rejeitar` | aprovador, financeiro | motivo obrigatório |
| POST | `/api/despesas/{id}/pagar` | financeiro | congela chave PIX |

## Despesas — consultas
| Método | Rota | Papéis | Nota |
|---|---|---|---|
| GET | `/api/despesas?status=&tecnicoId=` | todos | técnico: só as suas |
| GET | `/api/despesas/{id}` | todos | inclui flag de duplicidade |
| GET | `/api/despesas/dashboard` | tecnico | totais do mês (pendente/aprovado/pago) |
| GET | `/api/despesas/fila-aprovacao` | aprovador | com alertas de limite e duplicidade |
| GET | `/api/despesas/fila-financeiro` | financeiro, admin | com chave PIX e **`pixCopiaECola` (BR Code com valor)** p/ QR |
| GET | `/api/despesas/fila-financeiro/csv` | financeiro, admin | CSV `;` com BOM UTF-8 p/ Excel + coluna `pix_copia_e_cola`; auditado |
| GET | `/api/despesas/{id}/audit` | todos (com posse) | trilha completa |

## Anexos
| Método | Rota | Papéis |
|---|---|---|
| POST | `/api/despesas/{id}/anexos` | tecnico (dono, editável) — multipart, jpeg/png/webp/pdf ≤ 10 MB |
| GET | `/api/anexos/{id}` | dono ou aprovador/financeiro/admin |
| DELETE | `/api/anexos/{id}` | tecnico (dono, editável) |

## Cadastros e configurações
| Método | Rota | Papéis |
|---|---|---|
| GET/POST/PUT | `/api/usuarios` | admin |
| **PUT** | **`/api/usuarios/me/chave-pix`** | **qualquer autenticado — dispara e-mail de alerta p/ aprovadores+admin** |
| GET | `/api/usinas`, `/api/categorias` | todos (só ativos; admin vê inativos com `?incluirInativas=true`) |
| POST/PUT | `/api/usinas`, `/api/categorias` | admin |
| GET/PUT | `/api/configuracoes` | admin (`prazo_lancamento_dias` 1–365; `aprovacoes_necessarias` 1–5, padrão 1) |

**BR Code PIX:** `Domain/PixBrCode.cs` gera o payload EMV-MPM oficial (testado contra o exemplo do manual do BCB, CRC16 `1D3D`). Recebedor = técnico (nome sem acentos, truncado em 25), valor da despesa embutido, `txid = DESPESA{id}` para conciliação.

## Notificações por e-mail (SMTP via .env)
- Despesa **enviada** → aprovadores
- **1ª aprovação** → técnico
- **Entrou no FINANCEIRO** → técnico + financeiro
- **Rejeitada** (com motivo) → técnico
- **Paga** (com chave usada) → técnico
- **Chave PIX alterada** → aprovadores + admin (anti-fraude)

`SMTP_HOST` vazio = e-mails só no log (dev). Falha de SMTP nunca derruba a requisição.
