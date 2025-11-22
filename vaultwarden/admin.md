1. Access the admin panel

```
https://vault.your_domain/admin
```

2. Enter the ADMIN_TOKEN

Generated earlier via:
```bash
openssl rand -base64 48
```

3. Recommended security settings

Disable public registration

Enable 2FA enforcement

Keep Websocket enabled

Use strong SMTP password

4. Disable new signups manually (optional)

```bash
SIGNUPS_ALLOWED="false"
```

5. Backup data folder

```bash
tar -czvf vw-backup.tar.gz /opt/vaultwarden/vw-data
```
