# ApexForge - Local Apex Testing for VS Code

[![Version](https://img.shields.io/visual-studio-marketplace/v/prasanth-samudrala.apexforge)](https://marketplace.visualstudio.com/items?itemName=prasanth-samudrala.apexforge)
[![Installs](https://img.shields.io/visual-studio-marketplace/i/prasanth-samudrala.apexforge)](https://marketplace.visualstudio.com/items?itemName=prasanth-samudrala.apexforge)

Run Salesforce Apex tests locally without deploying to a Salesforce org. Perfect for rapid development cycles and AI-agent integration.

## Features

- **Local Test Execution**: Run Apex tests without Salesforce deployment
- **Git Conflict Analysis**: Detect potential merge conflicts in Apex files across branches
- **File Parsing**: Extract structure from Apex files (classes, methods, SOQL queries)
- **AI Agent Integration**: MCP (Model Context Protocol) server for Cursor, Claude Code, and other AI tools
- **VS Code Integration**: Test Explorer, CodeLens, and diagnostics support

## Installation

1. Install from [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=prasanth-samudrala.apexforge).
2. The extension will automatically download the ApexForge binary on first activation.
3. Open a workspace containing Apex files (`.cls` or `.trigger`).

## Usage

### Run Tests

- **Run All Tests**: `Cmd/Ctrl+Shift+P` → "ApexForge: Run All Tests"
- **Run Tests in File**: Right-click on a `.cls` file → "ApexForge: Run Tests in Current File"
- **Run Single Test**: Click "Run Test" CodeLens above any `@IsTest` method
- **Keyboard Shortcut**: `Cmd/Ctrl+Shift+T` to run tests in current file

### Analyze Branch Conflicts

1. Open Command Palette (`Cmd/Ctrl+Shift+P`)
2. Run "ApexForge: Analyze Branch Conflicts"
3. Select two branches to compare
4. View conflict analysis in the output panel

### Parse Apex Files

1. Open an Apex file
2. Run "ApexForge: Parse Current File"
3. View extracted structure (classes, methods, annotations, SOQL)

## AI Agent Integration (MCP)

ApexForge includes an MCP server for integration with AI coding assistants.

### Available Tools

| Tool | Description |
|------|-------------|
| `apexforge_run_tests` | Run Apex tests with file/directory/pattern options |
| `apexforge_analyze_conflicts` | Analyze branches for merge conflicts |
| `apexforge_parse_file` | Extract file structure |

### Enable MCP Server

1. Open VS Code Settings
2. Search for "ApexForge"
3. Enable "Enable MCP" option

Or add to your `settings.json`:

```json
{
  "apexforge.enableMcp": true
}
```

## Configuration

| Setting | Default | Description |
|---------|---------|-------------|
| `apexforge.binaryPath` | `""` | Custom binary path (auto-downloaded if empty) |
| `apexforge.testPattern` | `**/*Test.cls` | Glob pattern for test files |
| `apexforge.parallelTests` | `true` | Run tests in parallel |
| `apexforge.maxParallel` | `4` | Maximum parallel test executions |
| `apexforge.timeout` | `30000` | Test timeout in milliseconds |
| `apexforge.showCodeLens` | `true` | Show Run Test links above test methods |
| `apexforge.enableMcp` | `false` | Enable MCP server for AI agents |

## Licensing

ApexForge offers a free trial with 5 test runs. After that, a license is required.

- **Free Trial**: 5 free test executions
- **Pro License**: Unlimited usage - [Get License](https://apex-forge.dev/pricing)

### Enter License Key

1. Run "ApexForge: Enter License Key"
2. Paste your license key (format: `AF-XXXX-XXXX-XXXX-XXXX`)
3. License is validated and stored securely

### Check Usage

Run "ApexForge: Show Usage & License Status" to see remaining trial uses or license status.

## Support
- **Issues**: [GitHub Issues](https://github.com/samudralap/apexforge-vscode/issues)
- **Documentation**: [ApexForge Docs](https://apex-forge.dev/docs)
- **Email**: support@apex-forge.dev
