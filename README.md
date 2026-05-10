<<<<<<< HEAD
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
=======
🖥️ OS System Monitor (Cross-Platform)
A lightweight, containerized monitoring solution that provides a real-time web dashboard for system health. This tool bridges the gap between raw hardware metrics (from Prometheus exporters) and a human-readable interface, supporting both Windows and Linux/WSL hosts.

🚀 Quick Start
1. Prerequisites
Ensure your host machine is running a metrics exporter:

Windows: windows_exporter (Enable collectors: cpu,memory,thermalzone,gpu,logical_disk).

Linux: node_exporter.

2. Run with Docker
Deploy the monitor using Docker Hub:

Bash

docker run -d \
  --name system-monitor \
  -p 8080:80 \
  -v $(pwd)/logs:/app/logs \
  --add-host=host.docker.internal:host-gateway \
  abdallahamrr/os_system_monitor:latest

📊 Features
Live Dashboard: Auto-refreshing HTML interface with dynamic, color-coded health bars.

Cross-Platform: Automatic detection and normalization of metrics for both Windows and Linux.

Hardware Tracking: Real-time monitoring of CPU Load, Temperature, GPU Utilization, Memory, and Disk I/O.

Session Reports: Built-in JavaScript engine to generate instant summary reports (Min/Max/Avg) with a single click.

Zero-Dependency UI: No heavy databases required; uses an efficient flat-file logging system.

🛠️ System Architecture
The project follows a modular 3-tier design:

The Source (Host): Prometheus-style exporters expose hardware data at :9182 (Win) or :9100 (NIX).

The Collector (Bash): A Dockerized script polls the host, calculates deltas (for live load accuracy), and handles OS-specific metric naming.

The Reporter (HTML/JS): A secondary script converts logs into a CSS-styled dashboard and generates historical session data.

📂 Project Structure
Plaintext

.
├── monitor.sh          # Primary data collection engine
├── reporter.sh         # HTML dashboard & report generator
├── Dockerfile          # Container configuration
├── docker-compose.yml  # Multi-container orchestration
└── logs/
    ├── system_metrics.log  # Flat-file database (History)
    └── dashboard.html      # Live web interface
>>>>>>> f5fb0583a6411f23959f58d7163aec59e69f6db5
