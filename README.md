# System Monitor Dashboard

A real-time system monitoring tool that collects hardware metrics (CPU, memory, disk, GPU, and temperature) from Windows or Linux hosts using Prometheus exporters. It logs data and generates a live HTML dashboard served via Docker containers.

## Features

- **Real-Time Monitoring**: Collects metrics every 3 seconds from Prometheus exporters (windows_exporter for Windows, node_exporter for Linux).
- **Cross-Platform**: Automatically detects OS and adapts metric collection.
- **Web Dashboard**: Auto-refreshing HTML interface with progress bars and color-coded alerts.
- **Historical Logging**: Stores metrics in a log file for analysis.
- **Dockerized**: Easy deployment with containerized components.
- **Print Reports**: JavaScript-powered summary with averages, mins, and maxes.

## Architecture

- **Data Collector**: Bash script fetches metrics via HTTP, processes them, and logs to file.
- **Report Generator**: Parses logs and generates HTML dashboard.
- **Web Server**: Python HTTP server serves the dashboard on port 8080.

## Prerequisites

- Docker and Docker Compose installed.
- Prometheus exporter running on host:
  - Windows: [windows_exporter](https://github.com/prometheus-community/windows_exporter) on port 9182.
  - Linux: [node_exporter](https://github.com/prometheus/node_exporter) on port 9100.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/system-monitor-dashboard.git
   cd system-monitor-dashboard
   ```

2. Ensure the exporter is running on your host.

3. Start the containers:
   ```bash
   docker-compose up
   ```

## Usage

- Access the dashboard at `http://localhost:8080/dashboard.html`.
- The page auto-refreshes every 3 seconds.
- Click "Print Report" for historical statistics.

## Configuration

- Edit `collector/system_collector.sh` to change URLs or metrics.
- Modify thresholds in `collector/generate_report.sh` for alerts.

## Technologies Used

- Docker & Docker Compose
- Bash scripting
- HTML/CSS/JavaScript
- Prometheus exporters

## Contributing

Feel free to submit issues or pull requests.

## License

MIT License
