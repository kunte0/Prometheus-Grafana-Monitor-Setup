# Prometheus + Grafana Monitor Setup
Prometheus + Grafana Monitor Setup with Docker-Compose

## About
You can remove stuff you dont need. This docker-compose setup includes:

- **prometheus**:
    - Prometheus is a systems and service monitoring system. It collects metrics from configured targets at given intervals.
- **grafana**
    - Grafana is a complete observability stack that allows you to monitor and analyze metrics, logs and traces. Its the webinterface that shows the graphes 🙂
- **cadvisor**
    - cAdvisor (Container Advisor) provides container users an understanding of the resource usage and performance characteristics of their running containers.
- **node_exporter**
    - Prometheus exporter for hardware and OS metrics exposed by *NIX kernels, written in Go with pluggable metric collectors.
- **blackbox**
    - The blackbox exporter allows blackbox probing of endpoints over HTTP, HTTPS, DNS, TCP and ICMP.
- **json_exporter**
    - A prometheus exporter which scrapes remote JSON by JSONPath. Log REST APIs.

## Setup
- Check the config files in `/config`
- `docker-compose up`
- port 9191 is exposed on localhost, use nginx or similar to proxy to grafana
```
server {
    listen 443 ssl;
    listen [::]:443 ssl;

    server_name g.yourdomain.com;

    location / {
        proxy_pass http://127.0.0.1:9191/;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```



## Usage

Go to grafana dashboard, login with `admin:admin` and change the password. Play around with it. Import some dashboards and panels Go to the [dashboard library](https://grafana.com/grafana/dashboards/), copy the id and import it. Setup alerts to telegram discord or slack.

