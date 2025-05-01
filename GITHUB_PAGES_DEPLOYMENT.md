# GitHub Pages Deployment Guide

This document outlines the steps taken to deploy this Vite + React application to GitHub Pages.

## Prerequisites
- Node.js and npm installed
- Git installed
- A GitHub account
- A GitHub repository for your project

## Configuration Steps

### 1. Update vite.config.ts
Add the base URL configuration in `vite.config.ts`:
```typescript
export default defineConfig({
  plugins: [react()],
  base: '/vite-pages-test/', // Replace with your repository name
})
```

### 2. Update package.json
Add deployment scripts to `package.json`:
```json
{
  "scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  }
}
```

### 3. Install gh-pages
Install the gh-pages package as a dev dependency:
```bash
npm install gh-pages --save-dev
```

## Deployment Process

### 1. Commit Your Changes
```bash
git add .
git commit -m "Configure GitHub Pages deployment"
git push origin main
```

### 2. Deploy to GitHub Pages
```bash
npm run deploy
```
This command will:
- Build your application (`npm run build`)
- Deploy the contents of the `dist` folder to the `gh-pages` branch

### 3. Configure GitHub Repository
1. Go to your GitHub repository
2. Navigate to Settings > Pages
3. Under "Source", select:
   - Branch: `gh-pages`
   - Folder: `/` (root)
4. Save the settings

## Accessing Your Site
Your site will be available at:
```
https://<your-username>.github.io/vite-pages-test/
```

## Important Notes
- Make sure all internal links in your application use relative paths
- If using React Router, ensure it's configured to work with the base URL
- The site may take a few minutes to become available after deployment
- You can check the deployment status in the "Actions" tab of your GitHub repository

## Troubleshooting
- If the site doesn't load, check if the base URL in `vite.config.ts` matches your repository name
- Ensure all assets are using relative paths
- Check the GitHub Actions logs for any deployment errors
- Clear your browser cache if you don't see the latest changes 