# Story Metrics and Grafana Dashboard


This repository contains detailed information about Avail metrics and the associated Grafana dashboard.  

## First steps  

Modify the config.toml file in $HOME/.story/story/

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

Check prometheus:
Open a browser and use the url: 26660
http://(your node IP)/26660

Or check it on your server:
```bash
curl http://localhost:26660/metrics
```
![image](https://github.com/user-attachments/assets/22b1c52e-c9b9-4d94-bfa8-b3cd3166d0f3)

## Configure Prometheus  

Log in to your Prometheus server and edit the configuration file:
/etc/prometheus/prometheus.yml

```bash
- job_name: storyRPC
  static_configs:
  - targets: ['(your node IP):26662']
```

