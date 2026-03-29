# Command Reference

## `squirex scan` — Agentforce Capability Scan

Run a static capability scan on Agentforce metadata files to detect configuration vulnerabilities like Excessive Agency and missing FLS masking.

```bash
squirex scan [options]
```

### Options
- `-d, --directory <dir>`: Workspace root directory (default: ".")
- `--sarif <file>`: Output SARIF to file (default: stdout)
- `--rules <ids>`: Comma-separated rule IDs to run (default: all)

### Examples
```bash
# Full workspace scan
squirex scan

# Output SARIF for CI/CD integration
squirex scan --sarif results.sarif

# Scan only for Prompt Injection and FLS rules
squirex scan --rules AGENTFORCE-1.1,AGENTFORCE-1.3
```

---

## `squirex scan-pr` — PR Delta Scan

Run Agentforce Capability Scan scoped only to lines and files changed in the pull request.

```bash
squirex scan-pr -b <branch> [options]
```

### Required
- `-b, --base <branch>`: Base branch to diff against (e.g., `main`)

### Options
- `-d, --directory <dir>`: Workspace root directory (default: ".")
- `--sarif <file>`: Output SARIF to file (default: stdout)

### Examples
```bash
# Compare against main
squirex scan-pr -b main

# Output SARIF for CI/CD integration
squirex scan-pr -b main --sarif report.sarif
```

---

## `squirex run` — Secondary: Local Apex Runtime

Run Apex tests locally with full mock runtime support.

### Examples
```bash
# Run tests in current directory
squirex run

# Run specific class
squirex run -f AccountUtilsTest.cls
```

---

## `squirex conflict` — Secondary: Conflict Prediction

Analyze two branches to predict Apex merge conflicts before they happen.

### Examples
```bash
# Compare main with feature branch
squirex conflict -b main,feature/new-accounts
```
