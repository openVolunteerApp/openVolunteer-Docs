# Getting Started

OpenVolunteer is designed to be flexible in how it is deployed. Organizations may choose to self-host the application on their own infrastructure, or deploy it using a managed SaaS platform that integrates directly with GitHub for streamlined updates and maintenance.

Because this is a Laravel-based application, it follows standard modern PHP application patterns. If your organization already has experience managing web infrastructure, self-hosting may be a natural fit. If not, a hosted SaaS deployment model is strongly recommended for simplicity and long-term sustainability.

## SaaS Deployment (Recommended)
For most volunteer-driven nonprofits and community organizations, deploying to a SaaS platform that integrates directly with **GitHub** is the preferred option.

Modern application hosting platforms allow you to:

- Connect directly to your GitHub repository
- Automatically deploy on push to main or release branches
- Configure environment variables via a web dashboard
- Scale infrastructure as usage grows
- Enable automated backups
- Monitor performance and uptime

This approach significantly reduces infrastructure overhead and allows your team to focus on managing volunteers rather than managing servers.

SaaS deployment is especially recommended if:

- Your organization does not have dedicated IT staff
- Infrastructure management would fall to volunteers
- You want predictable monthly costs
- You prefer automated deployments and updates

## Recommended Workflow

Regardless of hosting model, the recommended workflow is:

1. Fork or clone the official OpenVolunteer repository.
2. Maintain your organization’s configuration in environment variables.
3. Use GitHub for version control and release tracking.
4. Deploy either to your own infrastructure or through a SaaS provider that supports Laravel applications and GitHub integration.