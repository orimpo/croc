# SSH Connection Troubleshooting

## Issue
When clicking "Connect via SSH", the extension panel opens instead of the SSH connection dialog at the top.

## Possible Solutions

### 1. Check Extension Installation
- Ensure the "Remote - SSH" extension is properly installed and enabled
- Go to Extensions panel and verify it's not disabled
- Try disabling and re-enabling the extension

### 2. Command Palette Method
Instead of clicking the button, try using the Command Palette:
- Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
- Type "Remote-SSH: Connect to Host"
- Select the command from the dropdown

### 3. Check SSH Configuration
- Verify your SSH config file exists at `~/.ssh/config`
- Ensure your SSH hosts are properly configured
- Test SSH connection from terminal first: `ssh user@hostname`

### 4. Reset Extension Settings
- Open Command Palette (`Ctrl+Shift+P`)
- Type "Remote-SSH: Reset Host List"
- Try reconnecting

### 5. Clear Extension Cache
- Close VS Code/Cursor
- Delete the remote SSH cache:
  - Windows: `%USERPROFILE%\.vscode\extensions\ms-vscode-remote.remote-ssh-*\`
  - macOS: `~/.vscode/extensions/ms-vscode-remote.remote-ssh-*/`
  - Linux: `~/.vscode/extensions/ms-vscode-remote.remote-ssh-*/`

### 6. Alternative Connection Methods
- Use the status bar: Click the remote indicator in the bottom-left corner
- Use File menu: File → Connect to Host (if available)
- Use the Command Palette: "Remote-SSH: Add New SSH Host"

### 7. Check Extension Logs
- Open Command Palette
- Type "Remote-SSH: Show Log"
- Look for any error messages

### 8. Restart and Retry
- Restart VS Code/Cursor completely
- Try the SSH connection again

## Quick Fix
The most reliable method is usually:
1. Press `Ctrl+Shift+P`
2. Type "Remote-SSH: Connect to Host"
3. Select your configured host or add a new one

If none of these solutions work, the issue might be related to extension conflicts or a corrupted installation that requires reinstalling the Remote-SSH extension.