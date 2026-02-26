# prestashop-docker

Simple Docker Compose setup to run the latest PrestaShop with MariaDB.

## Quick start
1. Review and edit `.env` for passwords and admin account settings.
2. Start services:
   ```bash
   docker compose up -d
   ```
3. Open the storefront:
   - Local: `http://localhost:8080`
   - Codespaces: `https://<CODESPACE_NAME>-8080.app.github.dev`

## Admin panel
- Admin URL is randomized on first install. Find it by listing folders in the container:
  ```bash
  docker compose exec -T prestashop sh -lc 'ls -1 /var/www/html | grep -E "^admin"'
  ```
- Example admin URL (replace with your folder):
  `https://<CODESPACE_NAME>-8080.app.github.dev/adminXXXXXXXXXXXX/login`

Default credentials (from `.env`):
- Email: `admin@example.com`
- Password: `admin123`

## Codespaces notes
- Do not add `:8080` to the `*.app.github.dev` URL. The port is already encoded in the subdomain.
- If the browser auto-adds `:8080`, open the URL in a fresh incognito window.

## Notes
- The PrestaShop container uses `prestashop/prestashop:latest`.
- Data is persisted in Docker volumes: `db_data`, `prestashop_data`.
