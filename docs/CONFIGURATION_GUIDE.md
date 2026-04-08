# Infra-Config Configuration Guide

## Overview

This guide provides detailed instructions for configuring the `infra-config` repository and its associated infrastructure resources. It is intended for platform and infrastructure team members.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Environment Setup](#environment-setup)
3. [Configuration Files](#configuration-files)
4. [Common Operations](#common-operations)
5. [Troubleshooting](#troubleshooting)

## Prerequisites

- Access to the TechCorp GitHub organization
- Appropriate role-based access (write or higher)
- Local development environment with Git configured
- VPN connection to the TechCorp internal network

## Environment Setup

1. Clone the repository:
   ```bash
   git clone git@github.com:TechCorp/infra-config.git
   cd infra-config
   ```

2. Create a feature branch for your changes:
   ```bash
   git checkout -b <your-branch-name>
   ```

3. Make your changes and push to the remote:
   ```bash
   git add .
   git commit -m "descriptive commit message"
   git push origin <your-branch-name>
   ```

## Configuration Files

| File | Description | Updated By |
|------|-------------|------------|
| `config/base.yaml` | Base configuration shared across all environments | Platform Team |
| `config/production.yaml` | Production-specific overrides | Infrastructure Team |
| `config/staging.yaml` | Staging-specific overrides | Platform Team |
| `secrets/` | Encrypted secrets (never commit plaintext) | DevOps Lead |

## Common Operations

### Adding a New Service

1. Add the service definition to `config/base.yaml` under the `services` key.
2. Add environment-specific overrides in the corresponding environment config.
3. Open a pull request and request review from at least one team member.
4. After approval, merge to `main` and notify the infrastructure team.

### Updating an Existing Configuration

1. Modify the relevant config file on a feature branch.
2. Validate the configuration locally using the provided linter:
   ```bash
   ./scripts/validate-config.sh
   ```
3. Open a pull request with a clear description of the change and its impact.

## Troubleshooting

### Config validation fails
- Ensure YAML syntax is correct (use `yamllint`).
- Check that all required keys are present per the schema in `schemas/config-schema.json`.

### Deployment issues after config change
- Verify the change was merged to `main` and the CI pipeline completed successfully.
- Check the deployment logs in the CI/CD dashboard.
- Contact the infrastructure team (`@techcorp/infrastructure`) if the issue persists.

---

*Last updated: 2025-01-22 by Alice Chen (Platform Team)*
