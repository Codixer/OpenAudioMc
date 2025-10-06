# OpenAudioMc Client - Cloudflare Pages Deployment Guide

This guide will walk you through deploying the OpenAudioMc web client to Cloudflare Pages. Cloudflare Pages provides automatic builds and deployments from your Git repository with global CDN distribution.

## Prerequisites

Before you begin, make sure you have:

1. **A Cloudflare account** - Sign up at [cloudflare.com](https://cloudflare.com) if you don't have one
2. **A fork of this repository** - Fork the `Codixer/OpenAudioMc` repository to your own GitHub or GitLab account
3. **Access to your Git provider** - You'll need to authorize Cloudflare to access your GitHub or GitLab account

## Deployment Steps

### Step 1: Navigate to Cloudflare Pages

1. Log in to your Cloudflare account
2. Go to the Cloudflare Pages creation page: https://dash.cloudflare.com/?to=/:account/pages/new/provider/github
3. You'll see the "Create a project" interface

### Step 2: Connect Your Git Provider and Select Repository

On the "Select repository" page, you'll need to connect your GitHub or GitLab account if you haven't already.

<img width="1045" alt="Cloudflare Pages repository selection interface" src="https://github.com/user-attachments/assets/99801bf7-867d-4324-8e8d-722d77606624">

1. **Connect your account**: 
   - If this is your first time, click on the GitHub or GitLab tab
   - Click "Add account" to link your Git provider
   - Authorize Cloudflare to access your repositories

2. **Select your repository**:
   - Once connected, you'll see a list of your repositories
   - Find and select your forked `OpenAudioMc` repository
   - If you don't see your repository, you may need to configure repository access for the Cloudflare Pages app on GitHub/GitLab

3. Click **"Begin setup"** to proceed to the build configuration

### Step 3: Configure Build Settings

Now you'll configure how Cloudflare Pages should build and deploy your project.

<img width="1038" alt="Cloudflare Pages build configuration settings" src="https://github.com/user-attachments/assets/90dab1d0-d621-4359-a88d-d09e3ebfa7c0">

#### Project Configuration

1. **Project name**: Enter a name for your project (e.g., `openaudiomc-client`)
   - This will be used in your deployment URL: `your-project-name.pages.dev`

2. **Production branch**: Select `master`
   - This is the branch that will be deployed to production
   - Every commit to this branch will trigger a new deployment

#### Build Settings

3. **Framework preset**: Select **"React (Vite)"** or **"None"**
   - Cloudflare should auto-detect Vite, but you can select it manually if needed

4. **Build command**: Enter the following command:
   ```
   npm install && npm run lint && npm run build
   ```
   - This will install dependencies, run linting checks, and build the production bundle

5. **Build output directory**: Enter:
   ```
   build/
   ```
   - This is where Vite outputs the compiled production files (configured in `vite.config.js`)

#### Advanced Settings (Root directory)

6. Click on **"Root directory (advanced)"** to expand the advanced options

7. **Root directory path**: Enter:
   ```
   client/
   ```
   - This tells Cloudflare that the web client code is in the `client/` subdirectory of the repository
   - Cloudflare will run all build commands from this directory

### Step 4: Deploy Your Site

1. Review all your settings to ensure they match the configuration above
2. Click **"Save and Deploy"**
3. Cloudflare Pages will now:
   - Clone your repository
   - Install dependencies
   - Run the build command
   - Deploy your site to the global CDN

### Step 5: Monitor Your Deployment

After clicking "Save and Deploy":

1. You'll be redirected to the deployment page
2. You can watch the build logs in real-time
3. The deployment typically takes 2-5 minutes
4. Once complete, you'll receive a deployment URL (e.g., `https://your-project-name.pages.dev`)

## Post-Deployment Configuration

### Automatic Deployments

- **Production deployments**: Any push to the `master` branch will trigger a new production deployment
- **Preview deployments**: Pushes to other branches will create preview deployments with unique URLs
- **Build watch paths**: Deployments will only trigger when files in `/client/*` change

### Build Settings Summary

For future reference, here's a summary of all the build settings:

| Setting | Value |
|---------|-------|
| **Framework preset** | React (Vite) |
| **Build command** | `npm install && npm run lint && npm run build` |
| **Build output directory** | `build/` |
| **Root directory** | `client/` |
| **Production branch** | `master` |
| **Build watch paths** | `/client/*` |

### Environment Variables (Optional)

If you need to add environment variables:

1. Go to your project settings in Cloudflare Pages
2. Navigate to "Settings" → "Environment variables"
3. Add any required variables for production or preview environments

## Troubleshooting

### Build Failures

If your deployment fails:

1. Check the build logs in the Cloudflare Pages dashboard
2. Ensure all dependencies are listed in `package.json`
3. Verify the build command works locally by running: `npm install && npm run lint && npm run build`
4. Check that the `build/` directory is created after running the build

### Repository Not Showing

If your repository doesn't appear in the list:

1. Go to your GitHub/GitLab account settings
2. Find the Cloudflare Pages app under "Installed GitHub Apps" or "Applications"
3. Grant access to the specific repository or all repositories

### Build Command Issues

- The build command must succeed for deployment to complete
- If linting fails, fix the issues in your code and push again
- Make sure you're using Node.js version compatible with the project (check `.nvmrc` or `package.json` for version requirements)

## Additional Resources

- [Cloudflare Pages Documentation](https://developers.cloudflare.com/pages/)
- [Vite Documentation](https://vitejs.dev/)
- [OpenAudioMc Documentation](https://openaudiomc.net/docs)

## Support

If you encounter any issues with the deployment process, please:

1. Check the [Cloudflare Pages documentation](https://developers.cloudflare.com/pages/)
2. Visit the [OpenAudioMc Discord](https://discord.openaudiomc.net/)
3. Open an issue on the [GitHub repository](https://github.com/Codixer/OpenAudioMc/issues)
