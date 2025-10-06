# OpenAudioMc Client Deployment

## Cloudflare Pages Deployment

To deploy the OpenAudioMc client to Cloudflare Pages, follow these steps:

### Prerequisites

1. **Fork this repository** to your own GitHub or GitLab account

### Deployment Steps

1. **Navigate to Cloudflare Pages**
   - Go to: https://dash.cloudflare.com/?to=/:account/pages/new/provider/github

2. **Link your Git provider**
   - Connect your GitHub or GitLab account

3. **Configure your deployment** with the following settings:

#### Build Configuration

| Setting | Value |
|---------|-------|
| **Git repository** | `Codixer/OpenAudioMc` |
| **Build command** | `npm install && npm run lint && npm run build` |
| **Build output** | `build/` |
| **Root directory** | `client/` |
| **Build comments** | Enabled |
| **Build cache** | Enabled (Clear Cache) |

#### Branch Control

| Setting | Value |
|---------|-------|
| **Production branch** | `master` |
| **Automatic deployments** | Enabled |

#### Build Watch Paths

| Setting | Value |
|---------|-------|
| **Include paths** | `/client/*` |

#### Build System

| Setting | Value |
|---------|-------|
| **Build system version** | Version 3 |

#### Deploy Hooks

| Setting | Value |
|---------|-------|
| **Deploy hooks** | No deploy hooks defined |

### Notes

- The build process will automatically run linting and build the production-ready client
- The output will be generated in the `build/` directory
- Changes to files in the `/client/` directory will trigger automatic deployments
