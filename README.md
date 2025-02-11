# Prometheus-Monitoring-for-Golang-Counters-Gauges-Histograms-Summaries



This project demonstrates how to monitor and instrument a Golang application using Prometheus. It covers the four primary Prometheus metrics types:
- **Counter**
- **Gauge**
- **Histogram**
- **Summary**

## Prerequisites

Ensure you have the following installed on your system:
- [Golang](https://golang.org/dl/)
- [Docker](https://www.docker.com/get-started)
- [Prometheus](https://prometheus.io/download/)
- [Grafana (optional)](https://grafana.com/grafana/download)

## Installation and Setup

1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/golang-prometheus-monitoring.git
   cd golang-prometheus-monitoring
   ```

2. Install dependencies:
   ```sh
   go mod tidy
   ```

3. Run the Golang application:
   ```sh
   go run main.go
   ```

4. Open your browser and visit:
   - Metrics Endpoint: [http://localhost:8080/metrics](http://localhost:8080/metrics)
   - Application Endpoint: [http://localhost:8080](http://localhost:8080)

## Running with Docker

To simplify deployment, you can run the project using Docker.

### 1. Build the Docker Image
```sh
  docker build -t golang-prometheus-monitoring .
```

### 2. Run the Docker Container
```sh
  docker run -p 8080:8080 golang-prometheus-monitoring
```

### 3. Verify the Metrics
Once the container is running, access the metrics endpoint:
[http://localhost:8080/metrics](http://localhost:8080/metrics)

## Configuration for Prometheus

To scrape metrics from this application, update your `prometheus.yml` configuration:

```yaml
scrape_configs:
  - job_name: 'my_app'
    metrics_path: '/metrics'
    static_configs:
      - targets: ['host.docker.internal:8080']
```

Start Prometheus with the following command:
```sh
prometheus --config.file=prometheus.yml
```

## Visualizing Metrics in Grafana (Optional)

1. Start Grafana and login at [http://localhost:3000](http://localhost:3000)
2. Add Prometheus as a data source (URL: `http://localhost:9090`)
3. Create a dashboard and add panels to visualize metrics

## Acknowledgments
This project was inspired by Anton Putra YouTube tutorial on Prometheus Monitoring. A huge thanks

