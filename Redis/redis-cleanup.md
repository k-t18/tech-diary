# Cleanup Existing Redis Installation

### Stop and Remove the Redis Service

- sudo systemctl stop redis-server
- sudo systemctl disable redis-server

### Uninstall Redis

- sudo apt-get purge --auto-remove redis-server
- sudo apt-get remove redis-tools

### Remove Leftover Files and Directories

```
sudo rm -rf /etc/redis
sudo rm -rf /var/log/redis
sudo rm -rf /var/lib/redis
sudo rm -rf /run/redis*
sudo rm -rf /usr/local/bin/redis*
```

### Clean Package Cache

```
sudo apt-get autoremove
sudo apt-get autoclean
```

### 5. (Optional) Check for Any Remaining Redis Files

- whereis redis-server
- which redis-server

If any binary remains in /usr/bin/redis-server, you can remove it:

- sudo rm -f /usr/bin/redis-server
