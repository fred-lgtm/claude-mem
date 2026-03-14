# Brickface Enterprise Configuration

This repository is a Brickface Enterprise fork of [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) with enterprise-grade security and operational standards.

## Enterprise Standards Applied

### 1. Security

- **Secret Management**: All credentials managed via 1Password CLI (`op://` references)
- **Secret Scanning**: Automated secret detection via TruffleHog in CI pipeline
- **Security Contact**: fred@brickface.com (see SECURITY.md)
- **Dependency Auditing**: Automated via Dependabot

### 2. CI/CD Pipeline

The following GitHub Actions workflows are configured:

- **ci.yml**: Automated linting, testing, and security scanning
- **claude.yml**: Claude Code automation for PR reviews and issue responses
- **claude-code-review.yml**: Automated code reviews
- **summary.yml**: PR summary generation
- **convert-feature-requests.yml**: Automated feature request triage

### 3. Authentication & Authorization

- **CODEOWNERS**: Repository owned by @fred-lgtm
- **1Password Integration**: Credentials referenced via `op://` URIs
- **GitHub PAT**: Stored as `op://Brickface-Credentials/GitHub PAT/password`

### 4. Infrastructure

Environment variables are managed through `.env.example` with 1Password references:

```bash
GITHUB_PERSONAL_ACCESS_TOKEN=op://Brickface-Credentials/GitHub PAT/password
OLLAMA_HOST=http://5.9.138.21:11434
N8N_API_KEY=op://Brickface-Credentials/n8n API Key/password
HUBSPOT_API_KEY=op://Brickface-Credentials/HubSpot API Key/password
COMPOSIO_API_KEY=op://Brickface-Credentials/Composio API Key/password
```

Run commands with 1Password CLI:
```bash
op run --env-file=.env.example -- <command>
```

## Repository Information

- **Owner**: fred-lgtm (Brickface Enterprise)
- **Upstream**: thedotmack/claude-mem
- **Marketplace Name**: brickface
- **Security Contact**: fred@brickface.com

## Installation for Brickface Team

```bash
# Add the Brickface marketplace
/plugin marketplace add brickface

# Install claude-mem
/plugin install claude-mem
```

## Maintenance

### Syncing with Upstream

To sync with upstream changes from thedotmack/claude-mem:

```bash
# Add upstream remote if not already added
git remote add upstream https://github.com/thedotmack/claude-mem.git

# Fetch upstream changes
git fetch upstream

# Merge or rebase with upstream main
git merge upstream/main
# or
git rebase upstream/main

# Resolve conflicts if any
# Then push to origin
git push origin main
```

### Version Management

This fork maintains its own version numbering that tracks the upstream version. The version-bump skill is available for semantic versioning.

## Differences from Upstream

1. **Repository URLs**: Updated to point to fred-lgtm/claude-mem
2. **Marketplace Configuration**: Changed to "brickface" marketplace
3. **Enterprise Security**: Added comprehensive CI/CD and secret management
4. **1Password Integration**: All credentials reference Brickface vault
5. **Security Policies**: Custom security contact and policies

## Support

- **Enterprise Issues**: Contact fred@brickface.com
- **Upstream Issues**: Report to https://github.com/thedotmack/claude-mem/issues
- **Internal Documentation**: See `.claude/` and `docs/` directories

## License

Maintains original AGPL-3.0 license from upstream project.

Copyright (C) 2025 Alex Newman (@thedotmack). All rights reserved.
Brickface Enterprise fork maintained by fred-lgtm.
