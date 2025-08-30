# Redis Installation

### Fresh Install Redis

- sudo apt update
- sudo apt install redis-server

### Start and Enable Redis

- sudo systemctl start redis-server
- sudo systemctl enable redis-server
- sudo systemctl status redis-server

After running "sudo systemctl status redis-server" this command, you should see

```
redis-server.service - Advanced key-value store
     Loaded: loaded (/lib/systemd/system/redis-server.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2025-08-30 20:36:13 IST; 16min ago
```

If this is failed... fix it!

### Test the Installation

- redis-cli

You should see:

```
127.0.0.1:6379>
```
