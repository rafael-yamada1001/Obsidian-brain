---
tags: [projeto, reembolsos, infra, deploy]
---

# Infra e Deploy

Parte de [[00 - Visão Geral]]. Arquivos: `docker-compose.yml` (raiz) e `infra/nginx/nginx.conf`.

## Subir em produção

```bash
cp .env.example .env   # editar: POSTGRES_PASSWORD, JWT_KEY (32+ chars), SMTP_*
docker compose up -d --build
```

A API roda `Database.Migrate()` + seed na subida (idempotente). O healthcheck do Postgres segura a API até o banco aceitar conexões.

## Variáveis (.env)

| Variável | Uso |
|---|---|
| `POSTGRES_DB/USER/PASSWORD` | Banco |
| `JWT_KEY` | Assinatura HMAC dos tokens — `openssl rand -base64 48` |
| `SMTP_HOST/PORT/USER/PASSWORD/FROM/FROM_NAME` | Notificações (host vazio = só log) |

## nginx (reverse proxy)

- `www.empresa.com.br` (+ redirect do domínio nu) → container `site`
- `app.empresa.com.br` → container `portal`; **`/api/` → container `api:8080`**
- `client_max_body_size 12m` (uploads de comprovante; API limita em 10 MB)
- `location /.well-known/acme-challenge/` → webroot do certbot em todos os server blocks

## HTTPS — Let's Encrypt (passos)

1. DNS dos 3 hosts apontando para o servidor; stack HTTP no ar.
2. Emitir:
   ```bash
   docker compose run --rm certbot certonly --webroot -w /var/www/certbot \
     -d www.empresa.com.br -d empresa.com.br --email contato@empresa.com.br --agree-tos --no-eff-email
   docker compose run --rm certbot certonly --webroot -w /var/www/certbot \
     -d app.empresa.com.br --email contato@empresa.com.br --agree-tos --no-eff-email
   ```
3. Descomentar os blocos `listen 443 ssl` no `nginx.conf`, trocar os blocos `:80` por `return 301 https://$host$request_uri;` (mantendo o location do ACME).
4. `docker compose exec nginx nginx -s reload`
5. Renovação (cron ~60 dias): `docker compose run --rm certbot renew && docker compose exec nginx nginx -s reload`

O serviço `certbot` usa **profile** no compose — não sobe junto com `up -d`, só sob demanda.

## Migração futura de anexos para S3

`IArquivoStorage` é a única fronteira: implementar `S3ArquivoStorage` (mesmos caminhos relativos viram object keys), registrar no DI no lugar de `LocalArquivoStorage`, copiar o conteúdo do volume `anexos` para o bucket. Nada no banco muda.

## Backup

- Banco: `docker compose exec postgres pg_dump -U empresa empresa > backup.sql`
- Anexos: volume `anexos` (ex.: `docker run --rm -v empresa_anexos:/d -v $PWD:/b alpine tar czf /b/anexos.tgz /d`)
