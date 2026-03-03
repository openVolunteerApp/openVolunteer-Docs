# WordPress Login
This application can optionally integrate with an existing WordPress installation to allow users to sign in using their WordPress account. This is intended for organizations that already run a WordPress site (for membership, content, or community operations) and want a single shared login identity across both platforms.

This is an advanced feature. It requires direct connectivity to the WordPress database (read access at minimum), and it assumes your WordPress site is already managing users.

## What this integration does

When enabled, the application can:

- Authenticate users against WordPress user records.
    Optionally associate a Laravel user account with a WordPress user ID.
- Allow “existing WordPress users” to access the volunteer portal without creating a separate password.

## What it does not do by default

This integration does not automatically:

- Manage WordPress users (create/delete/update) unless you explicitly build that behavior.
- Share WordPress sessions/cookies (this is not “SSO via WordPress cookies”).
- Sync profile fields beyond what you choose to map.

## Prerequisites
Before enabling this:

- You have access to the WordPress database credentials (host, database name, username, password).
- Your Laravel application can reach that database host over the network.
- Your WordPress site’s users table prefix is known (commonly wp_, but not always).
- You understand that network/database exposure is a security boundary. Prefer least-privilege credentials.

While not required, its recommened you create a dedicated MySQL user for this integration with the minimum permissions required. In most cases: `SELECT` only is sufficient since we're only authenticating and reading user metadata.

## Environment variables (.env)

Add these variables to your Laravel application environment.

```ini
WP_DB_HOST=127.0.0.1
WP_DB_DATABASE=wordpress
WP_DB_USERNAME=wordpress_reader
WP_DB_PASSWORD=your_password_here
WP_DB_PREFIX=wp_
```