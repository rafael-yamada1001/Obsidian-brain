---
tags: [projeto, reembolsos, frontend]
---

# Portal React (app.empresa.com.br)

Parte de [[00 - Visão Geral]]. Vite + React 18 + React Router, **mobile-first** (técnicos usam no celular em campo), instalável como **PWA** (manifest + service worker que cacheia só o shell — dados da API sempre frescos).

## Telas por papel

### Técnico
- **Dashboard** (`/`): totais do mês (pendente / aprovado / pago), lista de despesas com badge de status; rejeitada mostra o **motivo** destacado e atalho "corrigir e reenviar".
- **Lançar despesa** (`/nova`, `/editar/:id`): usina, categoria, data (máx. hoje), valor, descrição e foto. A foto é **comprimida no navegador antes do upload** (`utils/imagem.js`: canvas, máx. 1600px no maior lado, JPEG ~80%). Categoria com comprovante obrigatório bloqueia o envio sem foto; valor acima do limite mostra aviso (não bloqueia). Botões "Enviar para aprovação" e "Salvar como rascunho".
- **Minha chave PIX** (`/chave-pix`): tipos cpf/email/telefone/aleatória, com aviso de que alterações alertam os aprovadores.

### Aprovador
- **Fila** (`/aprovacao`): cartões com foto do comprovante (miniatura), **destaque vermelho para limite excedido**, **alerta amarelo de duplicidade** (mesmo técnico + data + valor). Aprovação individual e **em massa** (checkboxes + botão "Aprovar N selecionadas", erros reportados por item). Rejeição exige motivo inline.

### Financeiro
- **Fila de pagamento** (`/financeiro`): técnico, valor, **chave PIX com botão copiar**, total da fila, **Exportar CSV** (para lote PIX no banco), "Marcar como paga" com observação opcional.

### Admin
- **Administração** (`/admin`): abas Usuários / Usinas / Categorias / Configurações (prazo de lançamento). Admin também acessa a fila do financeiro.

### Todos
- **Detalhe da despesa** (`/despesa/:id`): dados, comprovantes, alertas, pagamento e **histórico de auditoria** em timeline.

## Pontos técnicos

- `src/api.js`: fetch wrapper com Bearer token (localStorage); 401 → limpa sessão e volta ao login; erros da API (`{erro}`) viram mensagens amigáveis.
- Rotas protegidas por papel em `App.jsx` (`<Protegida papeis={[...]}>`); redirecionamento pós-login por papel (`rotaInicial`).
- Caminhos de API relativos → sem CORS em produção; dev usa proxy Vite (`/api → localhost:8080`).
- Imagens de comprovante carregadas via fetch autenticado + `URL.createObjectURL` (a tag `<img>` não envia o JWT).
- Build verificado: `npm run build` → 197 kB JS (62 kB gzip).
