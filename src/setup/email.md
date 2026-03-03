# Sending Email

This application sends email for things like invitations, password resets, notifications, and other system messages. Laravel supports multiple mail “drivers” (SMTP, API providers, etc.). In most cases, SMTP is the simplest and most portable option, and it works the same way whether you host this app yourself or deploy it via Laravel Cloud.

## What you’ll need

Before configuring anything, gather the following from your email provider:

- Mail host (example: smtp.mailgun.org, smtp.sendgrid.net, smtp.office365.com)
- Mail port (commonly 587 for STARTTLS, 465 for implicit TLS)
- Username and password (or an API-specific SMTP credential)
- Encryption type (tls or ssl)
- A “From” address and name (what recipients see)

Recommended: Use a dedicated sending domain (like mail.yourorg.org) and make sure SPF, DKIM, and DMARC are configured with your email provider. This improves deliverability and reduces the chance of messages going to spam.

## SMTP

### Laravel Cloud setup

1. Open your Environment Variables settings in Laravel Cloud
2. Add the mail variables
    ```ini
    MAIL_MAILER=smtp
    MAIL_HOST=your.smtp.host
    MAIL_PORT=587
    MAIL_USERNAME=your_smtp_username
    MAIL_PASSWORD=your_smtp_password
    MAIL_ENCRYPTION=tls
    MAIL_FROM_ADDRESS=no-reply@yourorg.org
    MAIL_FROM_NAME="Your Organization"
    ```

3. Deploy/redeploy so the new variables take effect

    After updating environment variables, trigger a deploy (or redeploy) so the running application picks up the changes. If the platform caches configuration during build/runtime, redeploying is the simplest way to ensure everything is applied cleanly.


### Self-hosted setup

1. Configure your .env file
    On your server, set the following environment variables. These keys are standard Laravel mail settings:

    ```ini
    MAIL_MAILER=smtp
    MAIL_HOST=your.smtp.host
    MAIL_PORT=587
    MAIL_USERNAME=your_smtp_username
    MAIL_PASSWORD=your_smtp_password
    MAIL_ENCRYPTION=tls
    MAIL_FROM_ADDRESS=no-reply@yourorg.org
    MAIL_FROM_NAME="Your Organization"
    ```

    Notes:
    If your provider uses port 465, set MAIL_PORT=465 and MAIL_ENCRYPTION=ssl.
Some providers require MAIL_ENCRYPTION=null (rare). If so, omit it or set it to an empty value.

2. Clear and rebuild config cache (production)

    If your deployment uses config caching (common in production), update the cache so Laravel picks up the new environment values:
    ```
    php artisan config:clear
    php artisan config:cache
    ```

## API Provider

Laravel can also send through API-based providers (depending on your Laravel version and installed packages). If your organization prefers an API provider (like Mailgun, SES, Postmark, or Resend). 

The key idea remains the same: set the mailer/driver and provider credentials via environment variables, whether self-hosted or in Laravel Cloud.