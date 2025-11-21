# Geek
Geek things👉👈

## webcoder

A bash script to set up VS Code Server with nginx reverse proxy.

### Features

- Downloads and installs the latest VS Code CLI if not already present
- Installs and configures nginx as a reverse proxy
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

### Note

When using the `--secure` option, ensure:
1. Your domain points to the server's IP address
2. Ports 80 and 443 are open
3. You have a valid email for Let's Encrypt (or modify the certbot command)
