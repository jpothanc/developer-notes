# Linux System services


```bash
# 1. List all services (active, inactive, and failed)
systemctl list-units --type=service --all

# 2. List only active services
systemctl list-units --type=service --state=active

# 3. List failed services
systemctl list-units --type=service --state=failed

# 4. List services with their enable/disable status
systemctl list-unit-files --type=service

# 5. Search for a specific service by name
systemctl list-units --type=service | grep <service-name>

# 6. Check the status of a specific service
systemctl status <service-name>

# 7. Start a service
sudo systemctl start <service-name>

# 8. Stop a service
sudo systemctl stop <service-name>

# 9. Restart a service
sudo systemctl restart <service-name>

# 10. Reload a service without stopping it (if supported)
sudo systemctl reload <service-name>

# 11. Enable a service to start at boot
sudo systemctl enable <service-name>

# 12. Disable a service from starting at boot
sudo systemctl disable <service-name>

# 13. Mask a service to prevent it from being started manually or automatically
sudo systemctl mask <service-name>

# 14. Unmask a service to allow it to start again
sudo systemctl unmask <service-name>

# 15. View logs of a specific service (using journalctl)
sudo journalctl -u <service-name>

# 16. View logs of a service with real-time updates
sudo journalctl -u <service-name> -f

# 17. List legacy services (if using init.d)
service --status-all

# 18. Check if a service is enabled
systemctl is-enabled <service-name>

# 19. Check if a service is active (running)
systemctl is-active <service-name>

# 20. Reload systemd to recognize changes (e.g., after modifying a service file)
sudo systemctl daemon-reload

# 21. Show all systemd services and their dependencies
systemctl list-dependencies

# 22. Get detailed info about a specific service
systemctl show <service-name>

# 23. Disable graphical interface and switch to multi-user (CLI only)
sudo systemctl set-default multi-user.target

# 24. Re-enable graphical interface
sudo systemctl set-default graphical.target

```
