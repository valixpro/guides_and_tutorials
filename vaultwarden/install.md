1. Update the system

```bash
sudo apt update && sudo apt upgrade -y
```

2. Install required packages

```bash
sudo apt install -y ca-certificates curl gnupg lsb-release ufw
```

3. Add Docker GPG key

```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg

| sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

4. Add Docker repository

```bash
echo
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg]
https://download.docker.com/linux/ubuntu

$(. /etc/os-release && echo $VERSION_CODENAME) stable"
| sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. Install Docker & Compose

```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

6. Create Vaultwarden user

```bash
sudo adduser vaultwarden
sudo usermod -aG docker vaultwarden
```

7. Prepare working directory

```bash
sudo mkdir -p /opt/vaultwarden
sudo chown -R vaultwarden:vaultwarden /opt/vaultwarden
sudo chmod -R 700 /opt/vaultwarden
```

8. Switch user

```bash
sudo su - vaultwarden
cd /opt/vaultwarden
```

9. Generate ADMIN_TOKEN

```bash
openssl rand -base64 48
```

10. Create compose.yaml

```bash
nano compose.yaml
```

11. Insert this configuration

```yaml
services:
vaultwarden:
image: vaultwarden/server:latest
container_name: vaultwarden
restart: unless-stopped
environment:
WEBSOCKET_ENABLED: "true"
SIGNUPS_ALLOWED: "false"
DOMAIN: "https://vault.your_domain"
ADMIN_TOKEN: "YOUR_ADMIN_TOKEN"
LOG_LEVEL: "info"
volumes:
- ./vw-data:/data
ports:
- "8080:80"
```

12. Start Vaultwarden

```bash
docker compose up -d
```
