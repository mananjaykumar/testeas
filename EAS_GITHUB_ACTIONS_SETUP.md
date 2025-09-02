# EAS GitHub Actions Automation

This repository includes automated workflows for EAS (Expo Application Services) using GitHub Actions.

## Workflows

### 1. EAS Build (`eas-build.yml`)
- **Triggers**: Push to main/develop, PRs to main, manual dispatch
- **Features**: 
  - Automatic builds on code changes
  - Manual builds with platform/profile selection
  - Linting before builds
  - Supports development and production profiles

### 2. EAS Submit (`eas-submit.yml`)
- **Triggers**: Manual dispatch only
- **Features**:
  - Submit builds to app stores
  - Platform selection (Android/iOS/all)
  - Production profile support

### 3. EAS Update (`eas-update.yml`)
- **Triggers**: Push to main, manual dispatch
- **Features**:
  - Publish over-the-air updates
  - Custom channels and messages
  - Automatic updates on main branch

## Setup Instructions

### 1. Generate Expo Token
```bash
# Install EAS CLI globally
npm install -g @expo/eas-cli

# Login to Expo
eas login

# Generate access token
eas token:create
```

### 2. Add GitHub Secrets
Go to your GitHub repository → Settings → Secrets and variables → Actions, then add:

- `EXPO_TOKEN`: Your Expo access token from step 1

### 3. Configure EAS Project
Ensure your `eas.json` has the necessary profiles. The workflows support:
- `development`: For development builds
- `production`: For production builds and submissions

### 4. Usage

#### Automatic Builds
- Push to `main` or `develop` branches triggers development builds
- Pull requests to `main` trigger development builds

#### Manual Actions
1. **Build**: Go to Actions → EAS Build → Run workflow
2. **Submit**: Go to Actions → EAS Submit → Run workflow  
3. **Update**: Go to Actions → EAS Update → Run workflow

## Customization

### Adding Production Build Profile
Add to your `eas.json`:
```json
{
  "build": {
    "production": {
      "distribution": "store",
      "android": {
        "buildType": "aab",
        "credentialsSource": "remote"
      },
      "ios": {
        "buildConfiguration": "Release",
        "credentialsSource": "remote"
      }
    }
  }
}
```

### Environment-Specific Updates
Modify the update workflow to use different channels:
- `staging` for testing
- `production` for live users

## Security Notes
- Never commit your `EXPO_TOKEN` to the repository
- Use repository secrets for all sensitive data
- Consider using branch protection rules for production deployments
