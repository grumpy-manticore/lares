# authentik

[Authentik](https://goauthentik.io/) is an identity provider.

## Getting Started

### .env

First, copy `.env.example`.

```bash
cp .env.example .env
```

Then fill out the values appropriately.
- `CADDY_NETWORK`: Docker network used by Caddy and other services that use it as a proxy. See [Caddy](../caddy#networking).
- `AUTHENTIK_SECRET_KEY`: Generate with `openssl rand 60 | base64` and keep it secure.
- `AUTHENTIK_ERROR_REPORTING__ENABLED`: Error reporting
- `AUTHENTIK_EMAIL__` variables: Set up for email notifications
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
