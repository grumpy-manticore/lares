# outline

[Outline](https://www.getoutline.com/) is a collaborative document editor similar to [Notion](https://notion.so)

## Getting Started

### .env

First, copy `.env.example`.

```bash
cp .env.example .env
```

Then fill out the values appropriately.
- `CADDY_NETWORK`: Docker network used by Caddy and other services that use it as a proxy. See [Caddy](../../prod/caddy#networking).
- `SECRET_KEY`: Generate with `openssl rand -hex 32` and keep it secure.
- `UTILS_SECRET`: Generate with `openssl rand -hex 32` and keep it secure.
- `AUTHENTIK_EMAIL__` variables: Set up for email notifications
- `POSTGRES_USER`: Username for Postgres
- `POSTGRES_DB`: Database for Postgres
- `DATABASE_CONNECTION_POOL_` variables: Adjust for connection pooling.
- `POSTGRES_PASSWORD`: Password for Postgress. Generate with `openssl rand 36 | base64`
- `URL`: Application URL
- `PORT`: Application port; if adjusted, adjust the `outline` service in `compose.yml` as well.
- `COLLABORATION_URL`: Used if running the [collobartion server separately](https://github.com/outline/outline/blob/main/docs/SERVICES.md).
- `OIDC_` variables: Configuration for OIDC authentication
- `SMTP_` variables: Configuration for mailing

You will find a number of derived or static variables as well. These can largely be ignored, though you can adjust them as needed.

### Running the Service

```bash
docker compose up -d
```

### Stopping the Service

```bash
docker compose down
```
