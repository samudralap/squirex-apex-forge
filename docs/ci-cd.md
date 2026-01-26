# CI/CD Integration

## GitHub Actions — Using Binary Releases
Download and use the pre-built binary in your CI pipeline:

```yaml
name: Apex Tests

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Download ApexForge
        run: |
          curl -L -o apexforge https://github.com/samudralap/ApexForge/releases/latest/download/apexforge-linux-x64
          chmod +x apexforge
          sudo mv apexforge /usr/local/bin/
          
      - name: Verify Installation
        run: apexforge --version
        
      - name: Run Apex Tests
        run: apexforge run -d force-app/main/default/classes --junit test-results.xml
        
      - name: Upload Test Results
        uses: actions/upload-artifact@v4
        if: always()
        with:
          name: test-results
          path: test-results.xml
          
      - name: Publish Test Report
        uses: mikepenz/action-junit-report@v4
        if: always()
        with:
          report_paths: 'test-results.xml'
```

## GitHub Actions — Conflict Detection on PRs

```yaml
name: Conflict Analysis

on:
  pull_request:
    branches: [main, develop]

jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0  # Full history for branch comparison
      
      - name: Download ApexForge
        run: |
          curl -L -o apexforge https://github.com/samudralap/ApexForge/releases/latest/download/apexforge-linux-x64
          chmod +x apexforge
          
      - name: Analyze Conflicts
        run: |
          ./apexforge conflict \
            -b ${{ github.base_ref }},${{ github.head_ref }} \
            --simulate \
            --format markdown \
            -o conflict-report.md
            
      - name: Comment on PR
        uses: actions/github-script@v7
        with:
          script: |
            const fs = require('fs');
            const report = fs.readFileSync('conflict-report.md', 'utf8');
            github.rest.issues.createComment({
              owner: context.repo.owner,
              repo: context.repo.repo,
              issue_number: context.issue.number,
              body: report
            });
```

## GitLab CI

```yaml
apex-tests:
  stage: test
  image: node:18
  before_script:
    - curl -L -o /usr/local/bin/apexforge https://github.com/samudralap/ApexForge/releases/latest/download/apexforge-linux-x64
    - chmod +x /usr/local/bin/apexforge
  script:
    - apexforge run --junit test-results.xml
  artifacts:
    reports:
      junit: test-results.xml
```

## Jenkins Pipeline

```groovy
pipeline {
    agent any
    stages {
        stage('Setup') {
            steps {
                sh '''
                    curl -L -o apexforge https://github.com/samudralap/ApexForge/releases/latest/download/apexforge-linux-x64
                    chmod +x apexforge
                '''
            }
        }
        stage('Test') {
            steps {
                sh './apexforge run --junit test-results.xml'
            }
            post {
                always {
                    junit 'test-results.xml'
                }
            }
        }
    }
}
```
