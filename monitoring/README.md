# Story Metrics and Grafana Dashboard


This repository contains detailed information about Avail metrics and the associated Grafana dashboard.  

## First steps  

Modify the config.toml file

```bash
prometheus = true
prometheus_listen_addr = ":26660"
```
![image](https://github.com/user-attachments/assets/fafc4510-efd8-4799-a304-4ed6e6970ef4)


Restart node:  
```bash
sudo systemctl restart story
sudo journalctl -u story -f
```
