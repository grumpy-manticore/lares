# caddy

[Caddy](https://caddyserver.com/) is an HTTPS server. I primarily use it as a reverse proxy.

## Getting Started

### .env

First, copy `.env.example`.

```bash
cp .env.example .env
```

Then fill out the values appropriately.
- `CADDY_NETWORK`: Docker network used by Caddy and other services that use it as a proxy. See [Networking](#networking) below.
- `CADDY_DOMAIN`: The root domain of your server.
- `TZ`: Your time zone

### Caddyfile

Next, copy `Caddyfile.example`

```bash
cp Caddyfile.example Caddyfile
```

Then add your services as needed. Reference the [Caddyfile Documentation](https://caddyserver.com/docs/caddyfile) for more complicated set ups.

> **Caddyfile in .gitignore?**  
> Technically, you don't need to `.gitignore` your `Caddyfile` - it shouldn't have any sensitive data - especially with your domain being in `.env`. I manage my Caddyfiles outside of this repo because I often have more than one instance of Caddy in my stack, so I just `.gitignore` those files and treat them as a build asset.

### Networking
In Docker, `localhost` refers to the internal `localhost` of a container. Docker Compose creates a default network for your containers, allowing them to reference each other with the container's name instead of `localhost`. However, these networks are scoped to the compose file.

For Caddy to route requests to services defined in other Docker Compose files, we need to create a network and attach it to all services referenced by Caddy - including Caddy itself.

### Creating the Network
Make sure to use the same value in CADDY_NETWORK value in `.env` as you do here.

```bash
docker network create {CADDY_NETWORK}
```

### Running the Service

```bash
docker compose up -d
```

### Reloading the Caddyfile
You can do this after you make changes to your Caddyfile.

```bash
docker compose exec -w /etc/caddy caddy caddy reload
```

### Formatting the Caddyfile
Caddy will often complain about formatting; you can fix it with this.

```bash
docker compose exec -w /etc/caddy caddy caddy fmt --overwrite
```

### Stopping the Service

```bash
docker compose down
```

### Removing the Network

```bash
docker network remove {CADDY_NETWORK}
```