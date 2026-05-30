# Peafowl Education - Play Store Setup Guide

## Step 1: Expo Account Setup
1. Go to https://expo.dev and create an account
2. Create a new project called "peafawl-education"
3. Get your Expo Access Token:
   - Go to https://expo.dev/settings/access-tokens
   - Click "Create Token" and copy it

## Step 2: GitHub Secrets Setup
1. Push this code to a GitHub repository
2. Go to your GitHub repo → Settings → Secrets and variables → Actions
3. Add a new secret:
   - Name: `EXPO_TOKEN`
   - Value: (paste your Expo token from Step 1)

## Step 3: Automatic APK Build
1. Go to your GitHub repo → Actions tab
2. Click "EAS Build & Submit" workflow
3. Click "Run workflow" and select:
   - `preview` for APK (direct install)
   - `production` for AAB (Play Store upload)
4. Build will start automatically and APK download link will be provided

## Step 4: Play Store Publish
1. Create Google Play Console account ($25 one-time fee)
2. Create a new app in Play Console
3. Go to "Setup" → "API Access" → link your Google Cloud project
4. Create a Service Account with "Release Manager" role
5. Download the JSON key file
6. In Expo dashboard, go to your project → Submit → Android
7. Upload the service account JSON key
8. Run production build: `eas build -p android --profile production`
9. Then submit: `eas submit -p android`

## Manual Build (Alternative)
```bash
# Install EAS CLI
npm install -g eas-cli

# Login to Expo
eas login

# Configure project
eas build:configure

# Build APK (preview)
eas build -p android --profile preview

# Build AAB (Play Store)
eas build -p android --profile production

# Submit to Play Store
eas submit -p android
```

## Build Profiles
- **preview**: APK file for direct install/testing
- **production**: AAB file for Play Store upload

## Notes
- APK builds are free on Expo
- Play Store requires $25 one-time developer fee
- First build may take 10-15 minutes
- All builds are done in cloud (no local setup needed)
