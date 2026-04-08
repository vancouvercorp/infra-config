# Infra-Config Documentation

## Overview

This repository manages the infrastructure configuration for TechCorp's platform and services. It contains deployment configs, environment settings, and infrastructure-as-code definitions used across the organization.

## Repository Structure

```
infra-config/
├── config/          # Environment-specific configuration files
├── deployments/     # Deployment manifests and templates
├── docs/            # Project documentation
├── scripts/         # Helper scripts for infrastructure management
└── secrets/         # (Never commit plaintext secrets — use vault references)
```

## Getting Started

### Prerequisites

- Access to the TechCorp infrastructure AWS account
- `kubectl` configured for the target cluster
- `terraform` >= 1.5.x installed
- `helm` >= 3.x installed

### Quick Start

1. Clone this repository:
   ```bash
   git clone https://github.com/TechCorp/infra-config.git
   cd infra-config
   ```

2. Review the environment configurations under `config/`.

3. Apply changes using the provided scripts in `scripts/`.

## Environments

| Environment | Cluster       | Region         |
|-------------|---------------|----------------|
| dev         | dev-cluster   | us-west-2      |
| staging     | staging-cluster | us-west-2    |
| production  | prod-cluster  | us-west-2      |

## Deployment Process

1. Create a feature branch from `main`.
2. Make configuration changes.
3. Open a pull request for review.
4. After approval, merge to `main` to trigger the deployment pipeline.
5. Monitor deployment via the CI/CD dashboard.

## Contributing Guidelines

- All changes to `production/` configs require two approvals.
- Never commit secrets or credentials. Use environment variable references or vault integration.
- Run `scripts/validate.sh` locally before pushing.
- Tag all releases following semantic versioning (e.g., `v1.2.3`).

## Contacts

- **Platform Team Lead:** Carol Williams (Engineering Manager)
- **DevOps Lead:** Eve Johnson
- **Infrastructure Escalation:** #infra-alerts on Slack

## Changelog

- **2025-01-22** — Initial documentation structure and contributing guidelines added.
