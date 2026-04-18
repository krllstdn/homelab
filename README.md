# Homelab

Personal self-hosted infrastructure running on a good old ThinkPad via Docker Compose, accessible remotely via Tailscale.

## Services

| Service | Purpose | Port |
|---------|---------|------|
| Audiobookshelf | Ebooks & audiobooks | 13378 |
| Navidrome | Music server | 4533 |
| Nextcloud | File sync & calendar | 8081 |
| Forgejo | Git hosting | 3001 |
| AdGuard Home | Network-wide ad blocking | 3003 |
| Portainer | Docker management | 9000 |
| Homepage | Dashboard | 3000 |

## Setup

Requirements: Docker, Docker Compose, Tailscale

```bash
git clone git@github.com:krllstdn/homelab.git
cd homelab
cp <service>/.env.example .env  # fill in your tokens (if there are any)
cd <service> && docker compose up -d
```

## Security

- All services accessible only via Tailscale (no public ports)
- SELinux enabled (Fedora)
- Secrets via `.env` files, never committed

## Configuration

Copy `config/services.yaml.example` to `config/services.yaml` and replace placeholders:

- `YOUR_TAILSCALE_IP` — your Tailscale IP (`tailscale ip -4`)
- `YOUR_PORTAINER_TOKEN` — Portainer → Account Settings → Access Tokens

## Planned
- Immich — photo management
- Vaultwarden — passwords (needs Caddy/HTTPS)
- Uptime Kuma — service monitoring
- FreshRSS — RSS reader
- Paperless-ngx — document management
- Hoarder — bookmark manager
- Glances — system monitoring
- Caddy — reverse proxy + HTTPS

## Notes

- Fedora KDE Plasma host
- `systemd-resolved` disabled, AdGuard handles DNS
