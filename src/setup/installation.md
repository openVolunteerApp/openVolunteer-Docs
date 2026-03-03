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

## Laravel Cloud
This walkthrough is assuming you're using Laravel Cloud, but adjust the steps for any other provider.

First, Go to https://cloud.laravel.com/ and create an account. Create a company (or individual) account with the "Starter" plan. Then complete the steps to deploy.

### Fork and Create App

1. Login / Create a Github account.
2. Go to the github repo and fork it using the Fork button in the top right.
    - You can leave the owner as yourself or set it to an org account.
    - Name can remain openVolunteer or whatever you choose.
    - Leave "Copy the Main Branch Only" checked
3. Back on Laravel cloud, Connect your GitHub account.
4. Create your first application.
    - Choose Github
    - Import a Repository
    - Select the repo you forked in step 2.
    - For Region, choose something that makes sense for where you’ll be using this primarily. (Example: US East)
    - Click “Create Application”

### Setup Resources

1. Under “App Cluster”, this is your web server. 
    - You can leave this be.
    - You may want to disable “Hibernation”
2. Add a **Database** Resource
    > Databases house all your data that is entered into the application. Your volunteers/users, departments, hours, shifts, everything.
    - Click “Add Resource”, then “Database”
    - You can leave Name alone
    - You can select Laravel MySQL or Postgres
    - Region: Leave as the same region you selected before.
    - Configuration, you can leave this as “Dev” for now
    - Click "Create Database Cluster"
3. Add a **Bucket** Resource.
    > Buckets are storage for images and other resources. This will be used to set your app icon and other files. It will be barely used (at this time).
    - You can leave the name be.
    - Visibility change to “Public”
    - Allowed origins: You can leave be
    - Click “**Create bucket**”
    - On the next page, leave “Disk name” alone, and click “**Add Bucket**”.
4. You should have a database, and a bucket.
5. Now you can go ahead and click on “Deploy” in the top right.
6. Once its done deploying, it should have no errors. You can access it by going to the Cloud domain they create for you.

Once you are ready to start using it properly, you may want to setup a Custom Domain and setup a [Mail Server](./email.md) connection.

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