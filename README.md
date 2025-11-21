# Geek
Geek things👉👈

## webcoder

A bash script to set up VS Code Server with nginx reverse proxy.

### Features

- Downloads and installs the latest VS Code CLI if not already present
- Installs and configures nginx as a reverse proxy
- Automatically starts VS Code server as a systemd service
- Optionally configures SSL/TLS using certbot
- Supports custom port, domain, and security settings

### Usage

```bash
sudo ./webcoder [OPTIONS]
```

### Options

- `-p, --port PORT` - Port for VS Code server to listen on (default: 8000)
- `-d, --domain DOMAIN` - Domain name for nginx (default: use server IP)
- `-s, --secure` - Enable HTTPS with certbot (default: false)
- `-h, --help` - Display help message

### Examples

```bash
# Use defaults (port 8000, no domain, no SSL)
sudo ./webcoder

# Use custom port
sudo ./webcoder -p 9000

# Use with domain
sudo ./webcoder -p 8000 -d example.com

# Use with domain and SSL
sudo ./webcoder -p 8000 -d example.com -s
```

### Requirements

- Root/sudo privileges
- Internet connection for downloading VS Code CLI
- Supported OS: Linux, macOS
- Supported architectures: x64, arm64, armhf

### What the script does

1. Downloads and installs VS Code CLI to `~/.vscode-cli/`
2. Installs nginx web server
3. Configures nginx as a reverse proxy to VS Code server
4. Creates a systemd service for VS Code server
5. Starts VS Code server automatically
6. (Optional) Configures SSL/TLS certificates with certbot

### Service Management

After installation, VS Code server runs as a systemd service:

```bash
# Check status
sudo systemctl status vscode-server.service

# View logs
sudo journalctl -u vscode-server.service -f

# Stop server
sudo systemctl stop vscode-server.service

# Restart server
sudo systemctl restart vscode-server.service

# Disable auto-start on boot
sudo systemctl disable vscode-server.service
```

### Note

When using the `--secure` option, ensure:
1. Your domain points to the server's IP address
2. Ports 80 and 443 are open
3. You have a valid email for Let's Encrypt (or skip email prompt for testing)
