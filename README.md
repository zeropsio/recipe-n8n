# Zerops x n8n

[n8n](https://n8n.io) is a powerful open-source workflow automation tool. [Zerops](https://zerops.io) recipe for n8n offers a scalable solution — n8n server with separate scalable workers, PostgreSQL database, Valkey (Redis alternative) for worker communication, S3 storage for files, and Mailpit for email testing.

![n8n](https://github.com/zeropsio/recipe-shared-assets/blob/main/covers/svg/cover-n8n.svg)

<br/>

## Deploy on Zerops
You can either click the deploy button to deploy directly on Zerops, or manually copy the [import yaml](https://github.com/zeropsio/recipe-n8n/blob/main/zerops-project-import.yml) to the import dialog in the Zerops app.

[![Deploy on Zerops](https://github.com/zeropsio/recipe-shared-assets/blob/main/deploy-button/green/deploy-button.svg)](https://app.zerops.io/recipe/n8n)

<br/>

## Recipe features

- n8n running on **Zerops Node.js** service with auto-scaling
- Separate **n8n workers** for parallel task processing with auto-scaling
- Zerops **PostgreSQL 16** service as database
- Zerops **Valkey** (Redis alternative) service for communication between main server and workers
- Zerops **Object Storage** (S3 compatible) service for file storage
- Logs set up to use **syslog** and accessible through Zerops GUI
- Utilization of Zerops built-in **environment variables** system
- [Mailpit](https://github.com/axllent/mailpit) as **SMTP mock server** for email testing

<br/>

## Production vs. development

Base of the recipe is ready for production, the difference comes down to:

- Use highly available version of the PostgreSQL database (change `mode` from `NON_HA` to `HA` in recipe YAML, `db` service section)
- Use production-ready third-party SMTP server instead of Mailpit (change `N8N_SMTP_` secret variables in recipe YAML `app` service)

<br/>

## Changes made over the default installation

If you want to modify your existing n8n app to efficiently run on Zerops, these are the general steps we took:

- Add [zerops.yml](https://github.com/zeropsio/recipe-n8n/blob/main/zerops.yml) to your repository, our example includes optimized build process and configuration for multiple workers
- Utilize Zerops [environment variables](https://github.com/zeropsio/recipe-n8n/blob/main/zerops.yml#L48-L107) and [secrets](https://github.com/zeropsio/recipe-n8n/blob/main/zerops-project-import.yml#L36-L36) to setup database, S3 storage, Valkey, and other services

<br/>
<br/>

Need help setting your project up? Join [Zerops Discord community](https://discord.com/invite/WDvCZ54).