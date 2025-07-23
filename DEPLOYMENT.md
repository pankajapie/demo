# Firebase Deployment Setup

## Prerequisites
- Firebase project created (devprocess-f4521)
- GitHub repository with push access
- Node.js and npm installed

## Setup Instructions

### 1. Download Firebase Service Account Key
1. Go to [Firebase Console](https://console.firebase.google.com)
2. Select your project: **devprocess-f4521**
3. Navigate to Project Settings → Service Accounts
4. Click "Generate New Private Key"
5. Download the JSON file

### 2. Add Service Account to GitHub Secrets
1. Go to your GitHub repository
2. Navigate to Settings → Secrets and variables → Actions
3. Click "New repository secret"
4. Name: `FIREBASE_SERVICE_ACCOUNT`
5. Value: Paste the entire contents of the downloaded JSON file
6. Click "Add secret"

### 3. Install Dependencies
```bash
npm install
```

### 4. Test Locally
```bash
npm run build
npx firebase serve --only hosting
```

### 5. Deploy
Push to the main branch to trigger automatic deployment:
```bash
git add .
git commit -m "Deploy to Firebase"
git push origin main
```

## Manual Deployment
If you need to deploy manually:
```bash
npx firebase deploy --only hosting
```

## Environment Variables
The `.env` file contains Firebase configuration. Never commit this file.
Use `.env.example` as a template for other developers.

## Service Account
Your service account email: `firebase-adminsdk-fbsvc@devprocess-f4521.iam.gserviceaccount.com`