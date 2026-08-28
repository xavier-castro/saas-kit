# saas-kit

[![Watch the video](https://img.youtube.com/vi/TWQv_tr5ABI/maxresdefault.jpg)](https://www.youtube.com/watch?v=TWQv_tr5ABI&t=1s)

A monorepo SaaS application with user-facing frontend and data service backend.

## Setup

```bash
pnpm run setup
```

This installs all dependencies and builds required packages.

## Development

### User Application
```bash
pnpm run dev:user-application
```

### Data Service
```bash
pnpm run dev:data-service
```

## Deployment

The monorepo uses Wrangler environments to deploy four separate Workers to Cloudflare:
- `saas-kit-user-application-preview`
- `saas-kit-user-application-production`
- `saas-kit-data-service-preview`
- `saas-kit-data-service-production`

### Deploy All (Preview + Production)
```bash
pnpm deploy
```

This builds `data-ops` once, then deploys both preview and production environments for all apps.

### Deploy Individual Environments
```bash
# Deploy all apps to preview
pnpm run deploy:preview

# Deploy all apps to production
pnpm run deploy:production
```

### Deploy Individual Apps
```bash
# User Application (both environments)
pnpm run deploy:user-application

# Data Service (both environments)
pnpm run deploy:data-service
```

### Customizing Worker Names

After running `backpine create saas-kit --name your-project`, update the `name` fields in the wrangler.jsonc files:
- `apps/user-application/wrangler.jsonc` → `"name": "your-project-user-application"`
- `apps/data-service/wrangler.jsonc` → `"name": "your-project-data-service"`

This ensures your deployed Workers match your project name in the Cloudflare dashboard.

## Working with Individual Apps

You can also navigate into any sub-application directory and work with it independently in your IDE:

```bash
cd apps/user-application
# Open in your preferred IDE
```
