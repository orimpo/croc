# SSH Connection Troubleshooting

## Issue
When clicking "Connect via SSH", the extension panel opens instead of the SSH connection dialog at the top.

**Error Update**: Command 'opensshremotes.openEmptyWindowInCurrentWindow' not found - This indicates the Remote-SSH extension is not properly installed or activated.

## Solutions for Extension Not Found Error

### 1. Install/Reinstall Remote-SSH Extension
1. Open Extensions panel (`Ctrl+Shift+X`)
2. Search for "Remote - SSH" by Microsoft
3. If installed, click "Uninstall" then "Install"
4. If not installed, click "Install"
5. Restart Cursor/VS Code after installation

### 2. Enable Required Extensions
Install all three Remote-SSH related extensions:
- **Remote - SSH** (ms-vscode-remote.remote-ssh)
- **Remote - SSH: Editing Configuration Files** (ms-vscode-remote.remote-ssh-edit)
- **Remote Explorer** (ms-vscode.remote-explorer)

### 3. Check Extension Status
1. Open Command Palette (`Ctrl+Shift+P`)
2. Type "Extensions: Show Installed Extensions"
3. Look for "Remote - SSH" and ensure it's enabled (not grayed out)
4. If disabled, click the gear icon and select "Enable"

### 4. Force Extension Activation
1. Open Command Palette (`Ctrl+Shift+P`)
2. Type "Developer: Reload Window"
3. After reload, try the SSH command again

### 5. Clear Extension Host Cache
1. Close Cursor/VS Code completely
2. Delete extension cache folders:
   - Linux: `rm -rf ~/.vscode/extensions/ms-vscode-remote.remote-ssh*`
   - Or manually delete in: `~/.vscode/extensions/`
3. Restart and reinstall the extension

## Original Solutions

### 6. Command Palette Method
Instead of clicking the button, try using the Command Palette:
- Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
- Type "Remote-SSH: Connect to Host"
- Select the command from the dropdown

### 7. Check SSH Configuration
- Verify your SSH config file exists at `~/.ssh/config`
- Ensure your SSH hosts are properly configured
- Test SSH connection from terminal first: `ssh user@hostname`

### 8. Reset Extension Settings
- Open Command Palette (`Ctrl+Shift+P`)
- Type "Remote-SSH: Reset Host List"
- Try reconnecting

### 9. Clear Extension Cache
- Close VS Code/Cursor
- Delete the remote SSH cache:
  - Windows: `%USERPROFILE%\.vscode\extensions\ms-vscode-remote.remote-ssh-*\`
  - macOS: `~/.vscode/extensions/ms-vscode-remote.remote-ssh-*/`
  - Linux: `~/.vscode/extensions/ms-vscode-remote.remote-ssh-*/`

### 10. Alternative Connection Methods
- Use the status bar: Click the remote indicator in the bottom-left corner
- Use File menu: File → Connect to Host (if available)
- Use the Command Palette: "Remote-SSH: Add New SSH Host"

### 11. Check Extension Logs
- Open Command Palette
- Type "Remote-SSH: Show Log"
- Look for any error messages

### 12. Restart and Retry
- Restart VS Code/Cursor completely
- Try the SSH connection again

## Immediate Fix for Your Error
1. **Install Remote-SSH Extension**: Go to Extensions (`Ctrl+Shift+X`) → Search "Remote - SSH" → Install
2. **Restart Cursor**: Close and reopen the application
3. **Try Command Palette**: `Ctrl+Shift+P` → "Remote-SSH: Connect to Host"

If the extension still doesn't work after installation, try the "Developer: Reload Window" command to force extension activation.