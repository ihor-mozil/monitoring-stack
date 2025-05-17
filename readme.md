# Monitoring Stack: Prometheus, Grafana, Node Exporter

This project provides a simple monitoring stack using Docker Compose, featuring Prometheus for metrics collection, Grafana for visualization, and Node Exporter for exposing host metrics.

## Project Structure

```
.
├── docker-compose.yml
├── prometheus.yml
└── provisioning/
    └── datasources/
        └── prometheus.yml
```

- **docker-compose.yml**: Defines and configures the Prometheus, Grafana, and Node Exporter services.
- **prometheus.yml**: Prometheus configuration file specifying scrape targets.
- **provisioning/datasources/prometheus.yml**: Grafana provisioning file to automatically add Prometheus as a data source.

## Step-by-Step Instructions

### 1. Clone the Repository

Clone this repository to your local machine:

```sh
git clone <repository-url>
cd <repository-directory>
```

### 2. Review Configuration Files

- **prometheus.yml**:  
  Configures Prometheus to scrape metrics from Node Exporter at `node_exporter:9100`.

- **provisioning/datasources/prometheus.yml**:  
  Automatically adds Prometheus as the default data source in Grafana.

### 3. Start the Monitoring Stack

Run the following command to start all services:

```sh
docker-compose up -d
```

This will start:
- **Prometheus** on port `9090`
- **Grafana** on port `3000`
- **Node Exporter** on port `9100`

### 4. Access the Services

- **Prometheus UI**: [http://localhost:9090](http://localhost:9090)
- **Grafana UI**: [http://localhost:3000](http://localhost:3000)  
  - Login with username `admin` and password `admin` (default, change in production).

### 5. Add Dashboards in Grafana

- Prometheus is already configured as a data source.
- Import dashboards or create your own to visualize metrics from Node Exporter.

### 6. Stopping the Stack

To stop all services:

```sh
docker-compose down
```

## Usage Guidelines

- **Customizing Prometheus Targets**:  
  Edit [`prometheus.yml`](prometheus.yml) to add or modify scrape targets.

- **Provisioning Additional Grafana Data Sources**:  
  Add more YAML files in [`provisioning/datasources/`](provisioning/datasources/prometheus.yml) as needed.

- **Persisting Data**:  
  Prometheus and Grafana data are stored in Docker volumes (`prometheus_data`, `grafana_data`) for persistence.

## Troubleshooting

- Ensure Docker and Docker Compose are installed.
- Check container logs for errors:
  ```sh
  docker-compose logs prometheus
  docker-compose logs grafana
  docker-compose logs node_exporter
  ```

---

**References:**
- [Prometheus Documentation](https://prometheus.io/docs/)
- [Grafana Documentation](https://grafana.com/docs/)
- [Node Exporter Documentation](https://github.com/prometheus/node_exporter)
