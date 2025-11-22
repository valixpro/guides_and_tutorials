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
