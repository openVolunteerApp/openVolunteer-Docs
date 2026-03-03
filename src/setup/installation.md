# Installation
OpenVolunteer is a standard Laravel application and can be deployed anywhere PHP is supported. While it may be installed on traditional VPS infrastructure, the recommended approach—especially for volunteer-run organizations—is to deploy using a managed Laravel hosting platform such as Laravel Cloud.

Using a managed Laravel-native platform significantly reduces operational complexity, improves reliability, and allows your organization to focus on volunteers rather than infrastructure.

If your organization prefers to self-host, the following minimum requirements apply:

- PHP 8.2+
- Composer
- MySQL 8+ or PostgreSQL 14+
- Node.js 18+
- A web server
- Supervisor or systemd for queue workers
- SSL certificate

## Self-Hosting (Non-SaaS)
High-level installation steps:

1. Fork/Clone the repository.
2. Run `composer install`.
3. Run `npm install && npm run build`.
4. Copy `.env.example` to `.env` and configure.
5. Generate an application key:
    ```bash
    php artisan key:generate
    ```
6. Run migrations:
   ```
   php artisan migrate
   ```
7. Configure queue workers and scheduler.
    - _Queue workers may be used in future updates._
8. Configure web server and SSL.