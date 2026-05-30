# APK Build Guide - 3 Methods

## Method 1: Expo EAS (Recommended - Easiest)

### Step 1: Create Account
1. Go to https://expo.dev
2. Sign up with Google/GitHub
3. Verify email

### Step 2: Upload Project
1. Download `peafowl-education-vscode.tar.gz`
2. Extract it to a folder
3. Go to https://expo.dev and click "Create Project"
4. Upload the extracted folder

### Step 3: Build APK
1. Go to https://expo.dev/build
2. Click "Create Build"
3. Select **Android**
4. Select **APK** (not AAB)
5. Click "Build"
6. Wait 10-15 minutes
7. Download APK file

**Free:** 30 builds/month on free tier

---

## Method 2: Appcircle

### Step 1: Create Account
1. Go to https://appcircle.io
2. Sign up with email
3. Verify account

### Step 2: Create App
1. Click "Create App"
2. Name: "Peafowl Education"
3. Select **Android**

### Step 3: Upload Source
1. Upload the extracted project folder
2. Or connect GitHub repo

### Step 4: Build
1. Go to "Build Profile"
2. Select **Android** → **Release**
3. Click "Start Build"
4. Wait 10-15 minutes
5. Download APK

**Free:** 500 build minutes/month

---

## Method 3: Codemagic

### Step 1: Create Account
1. Go to https://codemagic.io
2. Sign up with GitHub
3. Verify account

### Step 2: Setup Project
1. Click "Add Application"
2. Upload project folder
3. Or connect GitHub repo

### Step 3: Configure Build
1. Add **codemagic.yaml** file:
```yaml
workflows:
  android-build:
    name: Build APK
    max_build_duration: 120
    environment:
      node: 20
    scripts:
      - name: Install dependencies
        script: npm install
      - name: Build APK
        script: npx eas build -p android --profile preview
    artifacts:
      - build-*.apk
```

### Step 4: Build
1. Click "Start New Build"
2. Wait 10-15 minutes
3. Download APK

**Free:** 500 build minutes/month

---

## Quick Comparison

| Platform | Free Builds | Speed | Easy | Best For |
|----------|------------|-------|------|----------|
| Expo EAS | 30/month | Fast | Very Easy | Expo projects |
| Appcircle | 500 min | Fast | Easy | Any mobile app |
| Codemagic | 500 min | Fast | Medium | Complex CI/CD |

---

## Phone Install
1. Enable **Unknown Sources** in Settings
2. Download APK from build site
3. Tap APK file to install
4. Open app!

## Troubleshooting
- **APK not installing?** → Enable "Install Unknown Apps" for browser
- **App crashes?** → Use `preview` profile (not production)
- **Build fails?** → Check `package.json` and `app.json` are correct
