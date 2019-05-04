# Node Watcher

Node Watcher is a simple monitoring system using Prometheus and Grafana.

The system is based on Docker containers managed by docker-composer.


# Features

* [Prometheus](https://prometheus.io/) collects metrics from target node using
  [Prometheus Node Exporter](https://github.com/prometheus/node_exporter).

* A [Grafana](https://grafana.com/) dashboard allows you to visualize the metrics.

* Metrics can be inspected in alternative ways:
  * using the Prometheus web interface;
  * direct access to Node Exporter endpoint (eg. using curl).


# Requirements

* [Docker](https://docs.docker.com/install/) (Tested on v. 18.09.5)
* [Docker Compose](https://docs.docker.com/compose/install/) (Tested on v. 1.24.0)


# Docker containers

* Prometheus:
  * it will store the metrics in its local time-series database;
  * the web GUI will be accessible on localhost at address http://localhost:9090.

* Nodeexporter:
  * it is configured to access to the host for collecting system information
    (rootfs, proc, sys);
  * it is accessible on localhost at the address http://localhost:9100/metrics.

* Grafana:
  * it is autoconfigured to access Prometheus database;
  * it includes a simple dashboard to show CPU utilization, free memory and
    disk space;
  * it is accessible on localhost at the address http://locahost:3000


# Quick start

Demo setup for monitoring the host itself.

1. Install docker and docker-compose (see Requirements).
1. From node-watcher project dir run containers:
   ```bash
   docker-compose up -d
   ```
1. Login to grafana dashboard (user: admin; password: admin):
   http://localhost:3000

1. Try the Prometheus web GUI: http://localhost:9090

To monitor a different server, install node-exporter on it and modify the
"target" parameter in Prometheus configuration accordingly.


# Author

Alberto Eusebi <alberto.eusebi@albeus.eu>.
