1. Download Caddy

```bash
wget https://github.com/caddyserver/caddy/releases/download/v2.8.4/caddy_2.8.4_linux_amd64.deb
 -O caddy.deb
sudo apt install -y ./caddy.deb
```

2. Edit Caddyfile

```bash
sudo nano /etc/caddy/Caddyfile
```

3. Insert configuration

```
vault.your_domain {
reverse_proxy localhost:8080
}
```

4. Reload Caddy

```bash
sudo systemctl reload caddy
```

5. DNS requirements

Create A record
Name: vault
Value: YOUR_SERVER_IP
TTL: 300

Cloudflare users → grey cloud (proxy OFF)

📄 3. smtp.md — SMTP Configuration
1. Open compose.yaml

```bash
nano compose.yaml
```

2. Add SMTP configuration inside environment:

```
SMTP_HOST: "smtp.gmail.com"
SMTP_FROM: "yourmail@gmail.com
"
SMTP_PORT: "587"
SMTP_SECURITY: "starttls"
SMTP_USERNAME: "yourmail@gmail.com
"
SMTP_PASSWORD: "APP_PASSWORD"
SMTP_TIMEOUT: "15"
```

3. Restart Vaultwarden

```bash
docker compose down
docker compose up -d
```
