# Deploy 9Router to Railway

This guide explains how to deploy 9Router to Railway.

## Prerequisites

- [Railway](https://railway.app) account
- GitHub account with this repository forked

## Deployment Steps

### 1. Fork this repository

Fork this repo to your GitHub account.

### 2. Create new Railway project

1. Go to [Railway Dashboard](https://railway.app/dashboard)
2. Click **New Project** → **Deploy from GitHub repo**
3. Select your forked repository
4. Railway will auto-detect the `railway.json` and Dockerfile

### 3. Configure Environment Variables

In Railway project settings, add these variables:

| Variable | Value | Notes |
|----------|-------|-------|
| `PORT` | `20128` | Railway sets this automatically |
| `NODE_ENV` | `production` | Required for production mode |
| `JWT_SECRET` | Generate a secure string | Login security |
| `INITIAL_PASSWORD` | Set your admin password | First login password |
| `DATA_DIR` | `/app/data` | Data storage path |
| `BASE_URL` | `https://your-app.up.railway.app` | Replace with your Railway URL |
| `NEXT_PUBLIC_BASE_URL` | `https://your-app.up.railway.app` | Replace with your Railway URL |

### 4. Get Public URL

1. Go to **Settings** → **Networking**
2. Enable **Public Networking**
3. Your app URL will be: `https://your-app-name.up.railway.app`

### 5. Update BASE_URL

After getting your URL, update the environment variable:
- `BASE_URL` = `https://your-app-name.up.railway.app`
- `NEXT_PUBLIC_BASE_URL` = `https://your-app-name.up.railway.app`

### 6. Deploy

Railway will auto-deploy on push to `master` branch.

## Local Development

For local development, use:

```bash
bun install
bun server.js
```

Open http://localhost:20128

## Notes

- 9Router uses port `20128` by default
- The MITM server runs on port `443` (requires root)
- For localhost testing, use the default `http://localhost:20128`
- Railway deployments use dynamic `PORT` from Railway's environment
