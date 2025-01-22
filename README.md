# Sensor Farm

A distributed system for collecting, processing and visualizing sensor data built with Go and JavaScript.

## Overview

This project implements a distributed sensor monitoring system with the following components:

- Simulated sensors that generate random readings within configured ranges
- Message queue (RabbitMQ) for reliable data transport between components
- Data persistence layer using PostgreSQL
- Web interface for real-time visualization of sensor readings

## Architecture

The system consists of several key components:

- **Sensors**: Simulated sensors that generate readings and publish to message queue
- **Coordinator**: Handles discovery and coordination between components
- **Data Manager**: Persists sensor readings to PostgreSQL database
- **Web UI**: Real-time visualization dashboard built with WebSocket and CanvasJS charts

Data flows through the system as follows:

1. Sensors publish readings to RabbitMQ exchanges
2. Coordinator manages sensor discovery and data routing
3. Data Manager subscribes to readings and persists to database
4. Web UI receives readings via WebSocket and updates charts in real-time

## Prerequisites

- Go 1.x
- PostgreSQL
- RabbitMQ
- Node.js (for web UI dependencies)

## Installation

1. Clone the repository
2. Set up PostgreSQL database and create required tables
3. Install RabbitMQ and ensure it's running
4. Install Node.js dependencies for web UI:

```bash
cd web
npm install
```

## Running the System

Start each component in separate terminals:

```bash
# Start coordinator
./start_coordinator.bat

# Start simulated sensors
./start_sensors.bat

# Start data manager
cd datamanager/exec
go run main.go

# Start web interface
cd web
go run main.go
```

The web interface will be available at http://localhost:3000

## Configuration

- Sensor parameters can be configured in start_sensors.bat
- Database connection settings in datamanager/db.go and web/model/db.go
- RabbitMQ connection settings in qutils/queueutils.go

## License

[Add license information]

## Contributing

[Add contribution guidelines]

This project was created for learning and demonstration purposes of building distributed systems with Go.
