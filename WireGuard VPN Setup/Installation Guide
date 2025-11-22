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




3. Restart Vaultwarden

```bash
docker compose down
docker compose up -d
```
