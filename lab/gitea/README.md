# gitea

[Gitea](https://about.gitea.com/) is a code hosting and devOps platform.

## Getting Started

### .env

First, copy `.env.example`.

```bash
cp .env.example .env
```

Then fill out the values appropriately.
- `CADDY_NETWORK`: Docker network used by Caddy and other services that use it as a proxy. See [Caddy](../../prod/caddy#networking).
- `POSTGRES_USER`: Username for Postgres
- `POSTGRES_DB`: Database for Postgres
- `POSTGRES_PASSWORD`: Password for Postgress. Generate with `openssl rand 36 | base64`

### Running the Service

```bash
docker compose up -d
```

### Stopping the Service

```bash
docker compose down
```
