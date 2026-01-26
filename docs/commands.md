# Command Reference

## `apexforge run` — Execute Tests

Run Apex tests locally with full mock runtime support.

```bash
apexforge run [options]
```

### Options
- `-f, --file <files...>`: Specific files to test
- `-d, --directory <dir>`: Directory to scan for tests (default: ".")
- `-p, --pattern <pattern>`: File pattern to match (default: "**/*Test.cls")
- `--filter <regex>`: Filter test methods by regex
- `-s, --schema <file>`: Schema JSON file for SObject validation
- `-v, --verbose`: Verbose output with debug info
- `-j, --json`: Output results as JSON
- `--junit <file>`: Output JUnit XML report
- `--timeout <ms>`: Test timeout in milliseconds (default: 30000)
- `--fail-fast`: Stop on first failure
- `--parallel`: Run tests in parallel
- `--max-parallel <n>`: Max parallel tests (default: 4)

### Examples
```bash
# Run with verbose output
apexforge run -v

# Run specific class with JSON output
apexforge run -f AccountUtilsTest.cls --json

# Generate JUnit report for CI
apexforge run --junit test-results.xml

# Run tests in parallel
apexforge run --parallel --max-parallel 8
```

---

## `apexforge conflict` — Predict Merge Conflicts

Analyze two branches to predict Apex merge conflicts before they happen.

```bash
apexforge conflict [options]
```

### Required
- `-b, --branches <b1,b2>`: Two branches to compare (comma-separated)

### Options
- `-d, --directory <dir>`: Repository directory (default: ".")
- `-f, --files <patterns>`: File patterns to analyze
- `--simulate`: Simulate merge and predict test outcomes
- `--format <format>`: Output format: console, json, markdown, html (default: console)
- `-o, --output <file>`: Output file for report
- `-v, --verbose`: Verbose output

### Examples
```bash
# Compare main with feature branch
apexforge conflict -b main,feature/new-accounts

# Full simulation with predictions
apexforge conflict -b develop,feature/api-update --simulate -v

# Generate markdown report
apexforge conflict -b main,release/v2 --format markdown -o conflict-report.md
```

---

## `apexforge parse` — Debug Parser Output

Parse an Apex file and display the AST structure.

```bash
apexforge parse <file> [options]
```

### Options
- `-o, --output <format>`: Output format: json, tree (default: tree)
- `--tests`: Extract test method information
- `--soql`: Extract SOQL queries
- `--dml`: Extract DML statements

### Examples
```bash
# View AST tree
apexforge parse AccountService.cls

# Extract as JSON
apexforge parse MyClass.cls -o json

# Show test methods only
apexforge parse AccountTest.cls --tests
```

---

## `apexforge hook` — Git Hook Management

Install git hooks for automatic test validation.

```bash
apexforge hook [options]
```

### Options
- `--install`: Install git hooks
- `--uninstall`: Remove git hooks
- `--type <type>`: Hook type: pre-commit, pre-push, pre-merge (default: pre-commit)
- `-d, --directory <dir>`: Git repository directory (default: ".")

### Examples
```bash
# Show hook status
apexforge hook

# Install pre-commit hook
apexforge hook --install

# Install pre-push hook
apexforge hook --install --type pre-push
```
