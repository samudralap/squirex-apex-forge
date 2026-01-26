# ApexForge 🔨

[![License](https://img.shields.io/github/license/samudralap/squirex-apex-forge)](LICENSE.md)
[![Release](https://img.shields.io/github/v/release/samudralap/squirex-apex-forge)](https://github.com/samudralap/squirex-apex-forge/releases)
[![Build Status](https://github.com/samudralap/squirex-apex-forge/actions/workflows/release.yml/badge.svg)](https://github.com/samudralap/squirex-apex-forge/actions)

**Local Apex test execution and branch conflict prediction CLI**

Run Salesforce Apex tests locally without deploying to an org. ApexForge parses your Apex code, executes it against an in-memory mock runtime, and predicts merge conflicts before they happen.

## Installation

### Quick Install (macOS / Linux)
```bash
curl -L -o apexforge https://github.com/samudralap/ApexForge/releases/latest/download/apexforge-macos-arm64
chmod +x apexforge
sudo mv apexforge /usr/local/bin/
apexforge --version
```
> Note: Replace `apexforge-macos-arm64` with the appropriate binary for your system if needed.

For Windows and detailed installation instructions, see [Installation Docs](docs/installation.md).

## Quick Start
```bash
# Run all test classes in current directory
apexforge run

# Run tests from specific directory
apexforge run -d force-app/main/default/classes

# Analyze branches for conflicts
apexforge conflict -b main,feature/my-feature
```

## Documentation
- [Installation Guide](docs/installation.md)
- [Command Reference](docs/commands.md)
- [Runtime Features & Limits](docs/features.md)
- [CI/CD Integration](docs/ci-cd.md)
- [VS Code Extension](docs/vscode-extension.md)

## License
Proprietary Software — See [LICENSE.md](LICENSE.md) for terms.
Copyright © 2026 Prasanth Samudrala. All Rights Reserved.
