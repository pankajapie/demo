# Firebase Deployment Setup - Multi-Environment

## Prerequisites
- Firebase projects created (development and production)
- GitHub repository with push access
- Node.js 22 LTS and npm installed

## Environment Setup

### Development Environment
- **Project**: devprocess-f4521
- **Branch**: develop
- **Channel**: dev
- **URL**: https://devprocess-f4521--dev-[hash].web.app

### Production Environment
- **Project**: devprocess-f4521
- **Branch**: main
- **Channel**: live (default)
- **URL**: https://devprocess-f4521.web.app

## Setup Instructions

### 1. Download Firebase Service Account Key

1. Go to [Firebase Console](https://console.firebase.google.com)
2. Select your project: **devprocess-f4521**
3. Navigate to Project Settings → Service Accounts
4. Click "Generate New Private Key"
5. Download the JSON file

### 2. Configure GitHub Secrets

Add these secrets to your GitHub repository (Settings → Secrets and variables → Actions):

#### Required GitHub Secrets
- `FIREBASE_SERVICE_ACCOUNT` - Service account JSON for deployment
- `FIREBASE_API_KEY` - `AIzaSyCkItCxMkn1beQKxWcXdOx0OfZREGDCC7Y`
- `FIREBASE_AUTH_DOMAIN` - `devprocess-f4521.firebaseapp.com`
- `FIREBASE_PROJECT_ID` - `devprocess-f4521`
- `FIREBASE_STORAGE_BUCKET` - `devprocess-f4521.firebasestorage.app`
- `FIREBASE_MESSAGING_SENDER_ID` - `145417955075`
- `FIREBASE_APP_ID` - `1:145417955075:web:57fcfe369eaf234eb9ab36`
- `FIREBASE_MEASUREMENT_ID` - `G-FY9RJXLMFG`

### 3. Local Development Setup

1. Copy `.env.local.example` to `.env.local`
2. Fill in your Firebase development credentials
3. Install dependencies:
   ```bash
   npm install
   ```

### 4. Available Scripts

```bash
# Development
npm start:dev          # Start dev server
npm run build:dev      # Build for development
npm run deploy:dev     # Deploy to development

# Production
npm start:prod         # Start prod server
npm run build:prod     # Build for production
npm run deploy:prod    # Deploy to production

# Testing
npm test              # Run tests
```

## Deployment Workflow

### Automatic Deployment

- **Development**: Push to `develop` branch
- **Production**: Push to `main` branch

### Manual Deployment

```bash
# Development (preview channel)
firebase hosting:channel:deploy dev --expires 30d

# Production (live site)
firebase deploy --only hosting
```

## Environment Variables

- `.env.development` - Development defaults (committed)
- `.env.production` - Production defaults (committed)
- `.env.local` - Local overrides (not committed)

## GitHub Actions Environments

The workflows use GitHub Environments for:
- Deployment protection rules
- Environment-specific secrets
- Deployment history tracking

Configure environments in: Settings → Environments