# VS Code SSH Extension Research

## Overview
The **Visual Studio Code Remote - SSH** extension allows developers to connect to remote machines, virtual machines, or containers with running SSH servers and use VS Code's full feature set remotely.

## Key Features

### Remote Development Capabilities
- Open any folder on a remote machine using SSH
- Full VS Code feature set including IntelliSense, debugging, and code navigation
- No source code needs to be on local machine
- VS Code Server runs on remote machine independently

### Extension Management
When connected via SSH, VS Code manages extensions in two locations:

1. **Local Extensions (UI/Client side)**
   - Themes and snippets
   - Extensions that affect VS Code UI

2. **Remote Extensions (SSH host)**
   - Most development extensions
   - Language servers and debuggers
   - Extensions automatically install in correct location

### Extension Installation Options
- **Install from Extensions view**: Automatically installs in correct location
- **Always installed extensions**: Configure `remote.SSH.defaultExtensions` in settings
- **Force extension location**: Use `remote.extensionKind` setting to override defaults

## Getting Started

### Prerequisites
- OpenSSH compatible SSH client (PuTTY not supported)
- Visual Studio Code or VS Code Insiders
- Remote machine with SSH server running

### Supported Platforms
- **x86_64**: Debian 8+, Ubuntu 16.04+, CentOS/RHEL 7+
- **ARMv7l (AArch32)**: Raspberry Pi OS Stretch/9+ (32-bit)
- **ARMv8l (AArch64)**: Ubuntu 18.04+ (64-bit)
- **Windows**: 10/Server 2016/2019 (1803+) with OpenSSH Server
- **macOS**: 10.14+ (Mojave) with Remote Login enabled

### Installation Steps
1. Install Remote-SSH extension from VS Code marketplace
2. Set up SSH host (if needed)
3. Configure SSH key-based authentication (recommended)
4. Connect using Command Palette: `Remote-SSH: Connect to Host...`

## Connection Methods

### Basic Connection
```bash
# Command format
ssh user@hostname
# or for Windows domain accounts
ssh user@domain@hostname
```

### Using SSH Config File
VS Code can manage SSH configurations through config files:
```
Host remotehost.yourcompany.com
    User yourname
    HostName another-host-fqdn-or-ip-goes-here
    IdentityFile ~/.ssh/id_rsa-remote-ssh
```

## Advanced Features

### Port Forwarding
- **Temporary**: Use Command Palette `Forward a Port`
- **Permanent**: Configure in SSH config file using `LocalForward`

### Extension Search and Management
- Extensions view shows separate categories for local and remote
- Can install all local extensions on remote host
- Extension search works normally when connected
- Disabled extensions appear dimmed with install option

### Remote Terminal
- All terminal windows automatically run on remote host
- Can use `code` command from terminal for file operations
- Full bash/shell access to remote filesystem

## Configuration Examples

### Always Install Extensions
```json
"remote.SSH.defaultExtensions": [
    "eamodio.gitlens",
    "mutantdino.resourcemonitor"
]
```

### Force Extension Location
```json
"remote.extensionKind": {
    "ms-azuretools.vscode-containers": [ "ui" ],
    "ms-vscode-remote.remote-ssh-edit": [ "workspace" ]
}
```

### Port Forwarding in SSH Config
```
Host remote-linux-machine
    User myuser
    HostName remote-linux-machine.mydomain
    LocalForward 127.0.0.1:3000 127.0.0.1:3000
    LocalForward 127.0.0.1:27017 127.0.0.1:27017
```

## Debugging and Development

### Full Development Experience
- Complete IntelliSense support
- Debugging works as if code was local
- Breakpoints, variable inspection, call stack navigation
- Launch configurations in `.vscode/launch.json`

### File Operations
- File Explorer works with remote filesystem
- Can open folders and workspaces remotely
- Drag and drop file operations
- Integrated terminal for command-line operations

## Limitations and Considerations

### Known Limitations
- Password authentication not saved (key-based recommended)
- Alpine Linux not supported (glibc required)
- PuTTY not supported on Windows
- Some extensions may not work on ARM devices due to x86 native code

### Security Considerations
- Only connect to trusted remote machines
- Compromised remote could execute code on local machine
- Use key-based authentication when possible
- Consider using socket-based connections for multi-user hosts

## Troubleshooting Common Issues

### Connection Problems
- Verify SSH connectivity using command line first
- Check SSH file permissions
- Ensure required packages installed on remote (bash, tar, curl/wget)
- Check firewall settings for SSH port 22

### Extension Issues
- Some extensions may require specific architecture support
- Check extension documentation for remote development compatibility
- Use pre-release versions for latest features
- Report issues to extension authors with remote development context

## Related Extensions

### Remote Development Pack
Includes multiple remote development extensions:
- Remote - SSH
- Remote - Containers (Dev Containers)
- Remote - WSL

### Extension Marketplace
- Over 27+ million installs for Remote-SSH extension
- High user rating and active development
- Regular updates with VS Code releases
- Extensive documentation and community support

## Resources and Documentation

### Official Documentation
- [Remote Development using SSH](https://code.visualstudio.com/docs/remote/ssh)
- [SSH Tutorial](https://code.visualstudio.com/docs/remote/ssh-tutorial)
- [Extension Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)

### Community and Support
- GitHub repository for issues and feature requests
- Stack Overflow for questions
- VS Code documentation contributions welcome
- Troubleshooting guides available

This research shows that VS Code's Remote-SSH extension provides a comprehensive solution for remote development with full extension support and seamless integration with the VS Code ecosystem.