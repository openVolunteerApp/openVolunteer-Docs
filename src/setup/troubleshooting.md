# Common Troubleshooting

## Mail sending issues
Password reset emails never arrive, invites don’t send, or you see mail errors in logs.

Common causes and checks:
- Incorrect SMTP host/port/encryption. Port 587 typically uses tls (STARTTLS), port 465 typically uses ssl.
- Blocked outbound SMTP from your hosting provider. Some hosts restrict SMTP ports.
- Unverified sender/domain. Some providers require the From address or domain to be verified.
- Config cache not refreshed. If you changed .env values, clear and rebuild config cache.

## Site takes several seconds to respond
After a deploy or a period of inactivity, the site takes several seconds before it starts responding normally. Subsequent requests are fast.

This is commonly caused by “cold start” behavior. Depending on your runtime and platform settings, an application instance may need to spin up (or “warm up”) before it can handle requests at full speed. During that window, PHP may be booting the application, caches may be warming, and dependencies may be loading for the first time.

If this is happening on **Laravel Cloud**, disable "Hibration" on the database and/or web server.