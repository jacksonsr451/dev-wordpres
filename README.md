# Ambiente de desenvolvimento WordPress

Ambiente local baseado em Docker para desenvolvimento de plugins e temas.

## Requisitos

- Docker Desktop com Docker Compose

## Inicializacao

1. (Opcional) Copie `.env.example` para `.env` e altere as portas ou senhas.
2. Suba os servicos:

```powershell
docker compose up -d
```

3. Acesse `http://localhost:8080` e conclua o instalador do WordPress.

O banco fica persistido no volume Docker `db_data`, e os arquivos do WordPress no volume `wordpress_data`.

## Desenvolvimento

- Plugins: `wp-content/plugins/`
- Temas: `wp-content/themes/`
- Uploads e arquivos gerados: `wp-content/uploads/` (nao versionar)
- Banco de dados: `http://localhost:8081` (usuario `root`, senha definida em `.env`)

Os arquivos de `wp-content` sao montados diretamente no container. Alteracoes em plugins e temas ficam disponiveis imediatamente.

## Comandos uteis

```powershell
# Ver logs
docker compose logs -f wordpress

# Parar sem apagar dados
docker compose down

# Abrir um shell no WordPress
docker compose exec wordpress bash

# Recriar os servicos
docker compose pull
docker compose up -d
```

Para apagar tambem o banco e a instalacao local, use `docker compose down -v`.
