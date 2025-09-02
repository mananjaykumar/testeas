# EAS GitHub Actions Automation

Automated EAS builds and deployments using GitHub Actions.

## 🚀 **How It Works**

### **Automatic Triggers**
- **Push to `develop`**: Builds development versions for testing
- **Push to `main`**: Builds + deploys to production + publishes updates
- **Pull Request to `main`**: Runs pre-build checks only

### **Manual Triggers**
- **Build**: Choose platform (Android/iOS/all) and profile (development/production)
- **Deploy**: Automatic deployment on main branch with production profile

## ⚙️ **Setup**

### **1. Add Expo Token**
```bash
# Get token from: https://expo.dev/accounts/[username]/settings/access-tokens
# Add to GitHub Secrets as: EXPO_TOKEN
```

### **2. Configure GitHub Secrets**
- Go to repo Settings → Secrets → Actions
- Add `EXPO_TOKEN` with your Expo access token

## 🔄 **Workflow Steps**

### **Pre-build (All triggers)**
1. ✅ Code checkout
2. ✅ Dependencies install
3. ✅ Linting
4. ✅ Tests (if available)

### **Build (Push/Manual)**
1. ✅ EAS build for selected platforms
2. ✅ Development profile for auto-triggers
3. ✅ Custom profile for manual triggers

### **Deploy (Main branch only)**
1. ✅ EAS Update publish
2. ✅ App store submission (production only)

## 📋 **Usage**

### **Development**
```bash
git push origin develop
# → Builds development versions for testing
```

### **Production**
```bash
git push origin main
# → Builds + deploys + publishes updates
```

### **Manual Build**
1. Go to Actions → EAS Build & Deploy → Run workflow
2. Select platform and profile
3. Click "Run workflow"

## 🎯 **Benefits**

- ✅ **Automated**: No manual builds needed
- ✅ **Integrated**: Git-based triggers
- ✅ **Flexible**: Manual control when needed
- ✅ **Complete**: Build, deploy, and update pipeline
- ✅ **Safe**: Pre-build checks and conditional deployments

## 🔧 **Configuration**

### **Build Profiles**
- `development`: Internal distribution, debug builds
- `preview`: Internal distribution, release builds for testing
- `production`: Store distribution, release builds

### **Platforms**
- `android`: Android APK/AAB
- `ios`: iOS app
- `all`: Both platforms

The workflow automatically handles the complete CI/CD pipeline for your Expo app!
