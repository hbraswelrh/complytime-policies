# complytime-policies

Centralized repository for Gemara policies used by [ComplyTime](https://github.com/complytime) tooling. Policies defined here will be released as OCI artifacts to Quay.io and consumed via the `complyctl get` command.

## Overview

This repository contains governance artifacts used to define and enforce security controls across supported platforms (GitHub, GitLab, etc.). The governance content follows the [Gemara](https://github.com/gemaraproj/gemara) framework and is organized into catalogs and policies.

## Repository Structure

```
complytime-policies/
├── governance/
│   ├── catalogs/    # Security control catalogs and definitions
│   └── policies/    # Implementation policies and technical controls
├── LICENSE
└── README.md
```

## Governance Content

### Catalogs

Security control catalogs define the set of controls and assessment requirements. Each catalog groups controls into families and specifies the objectives and applicability of each control.

- [Branch Protection Catalog](governance/catalogs/ampel-branch-protection-catalog.yaml) - Controls for protecting source code repositories via branch protection rules

### Policies

Implementation policies define how controls are evaluated, who is responsible, and what automated tools are used for assessment.

- [Branch Protection Policy](governance/policies/ampel-branch-protection-policy.yaml) - Automated evaluation policy for branch protection controls using AMPEL

## Usage

Policies from this repository are planned to be released as OCI artifacts to Quay.io. Once available, they can be consumed using the `complyctl get` command, which retrieves policies based on a configuration file.

```bash
complyctl get
```

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.
