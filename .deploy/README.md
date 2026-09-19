# Stalwart cloud deployment

This folder contains a Docker Compose deployment for the Stalwart mail and collaboration server.

## Server requirements

Use a dedicated Linux VPS with a public IPv4 address. The deployment exposes the Stalwart management and mail ports directly, so avoid a host where ports 25, 443, 465, 587, 993 or the other listed ports are already occupied.

## First start

1. Copy `.env.example` to `.env`.
2. Replace the placeholder recovery password with a strong random password.
3. Run `docker compose up -d` from this directory.
4. Open `http://SERVER_IP:8080/admin` and sign in with the recovery administrator credentials.
5. Complete the setup wizard, then configure the intended mail hostname and domain.

For a production domain, point the mail hostname to the VPS, configure the DNS records recommended by Stalwart, enable TLS, and then use the HTTPS administration URL.
