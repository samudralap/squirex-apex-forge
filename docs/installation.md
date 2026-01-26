# Installation

## Download Binary (Recommended)

Download the pre-built binary for your platform from GitHub Releases:

| Platform | Binary | Architecture |
|----------|--------|--------------|
| macOS (Intel) | `apexforge-macos-x64` | x86_64 |
| macOS (Apple Silicon) | `apexforge-macos-arm64` | ARM64 |
| Linux | `apexforge-linux-x64` | x86_64 |
| Windows | `apexforge-win-x64.exe` | x64 |

## macOS / Linux

```bash
# Download (example for macOS Apple Silicon)
curl -L -o apexforge https://github.com/samudralap/ApexForge/releases/latest/download/apexforge-macos-arm64

# Make executable
chmod +x apexforge

# Move to PATH
sudo mv apexforge /usr/local/bin/

# Verify installation
apexforge --version
```

## Windows

1. Download `apexforge-win-x64.exe` from Releases.
2. Rename the file to `apexforge.exe`.
3. Add the location of the executable to your System PATH or move it to a directory already in PATH.
4. Run from Command Prompt or PowerShell.

### Verify Installation
```powershell
$ apexforge --version
0.1.0
```
