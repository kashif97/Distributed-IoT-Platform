# Distributed IOT Platform

A distributed platform for deploying and managing digital applications across diverse domains. It integrates seamlessly with multiple data sources and leverages the oneM2M platform for standardized data collection, offering flexible configuration, robust security, and efficient resource utilization.

The name reflects its core design: **Distributed** for its cohesive, multi-service architecture; **IoT Application** for its compatibility with a broad spectrum of connected-device use cases; and **Manager** for the platform's role in orchestrating deployment, monitoring, and lifecycle management end-to-end.

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Architecture](#architecture)
4. [Microservices](#microservices)
5. [Requirements](#requirements)
6. [Folder Structure](#folder-structure)
7. [Getting Started](#getting-started)
8. [Future Scope](#future-scope)
9. [Contributing](#contributing)
10. [License](#license)

## Overview

The platform simplifies running and managing digital applications at scale:

- **Connect Easily** — versatile integration with a range of sensors and devices.
- **Gather Data** — collects data from diverse sources via the oneM2M platform.
- **Dynamic Configuration** — derives application needs from configuration files for optimal setup.
- **User Flexibility** — settings and deployments can be adjusted to individual requirements.

Its primary mission is to help teams deploy and oversee large-scale digital projects, with device connectivity, efficient data management, and real-time insights at its core.

## Features

- Real-time data analysis from various IoT sensors
- Effective anomaly detection
- RESTful APIs for seamless data access
- Standardized machine-to-machine communication using OneM2M
- Integration with AWS/Azure for resource management

## Architecture

The platform follows a modular, horizontally scalable microservices architecture, using Kafka for distributed messaging, replication, and high throughput. Key design principles include:

- **Fault Tolerance** — redundancy through multiple service instances; seamless error handling at the application layer
- **Scalability** — modular services, horizontal scaling, and asynchronous processing
- **Data Accessibility** — REST APIs for application data access; OneM2M + ThingsBoard integration for sensor data, with MQTT for ingestion
- **Security** — password-based authentication, LDAP for authorization, OAuth support, and API key management
- **Monitoring** — ThingsBoard.io server-side APIs for secure monitoring and control of IoT entities

## Microservices

| Service | Responsibility |
|---|---|
| **Monitoring Service** | Tracks health status of each module, sends failure notifications, provisions new instances, and reports usage trends |
| **Load Balancing Service** | Distributes load evenly across the platform; monitors CPU/RAM and requests additional nodes under high demand |
| **Node/VM Manager & Deployment Manager** | Initializes nodes with set configurations, allocates resources for service startup, and deallocates them post-lifecycle |
| **API Manager & Communication Manager** | Routes API access, sets rate limits, and manages data interchange between devices and components |
| **Deployment Manager & Bootstrap Service** | Manages application setup, tracks deployment status, and initiates platform startup |
| **Sensor Manager** | Handles sensor registration and live data streaming; includes traffic logging and an API gateway for service requests |
| **Notification Service** | Dispatches user notifications; integrates with Kafka for message processing and SMTP for email delivery |
| **Analytics Service** | Processes and visualizes sensor data (`Analytics.py`, `graphs.py`); surfaces insights to the user dashboard |
| **Logger Service** | Consumes log messages from the `topic_logger` Kafka topic and stores them in the Logger DB; provides a log viewing interface |

## Requirements

**Functional**
- API-driven sensor interaction via an integrated sensor manager
- Independent application development on top of platform APIs
- Unique ID-based sensor identification and data binding
- Scalable, reliable message handling between components
- Automated server initiation on new application deployment
- Load balancing across microservices
- Bundled packaging with configuration in XML or JSON

**Non-Functional**
- Reliable, high-performance, and intuitive by design
- Terminal-based UI for platform interaction
- Persistence via file-based storage or relational/non-relational databases (under evaluation)

**External Interfaces**
- OAuth support for authentication
- APIs for managing bare-metal resources on AWS/Azure

## Folder Structure

```
project-root-directory/
├── client/
│   └── src/                    # Client-side source files for UI and interactions
└── server/
    ├── ApplicationManager/     # Manages application and service lifecycle
    ├── Bootstrap/              # Initial setup and platform configuration
    ├── Logger/                 # Logging utilities
    ├── analytics/              # Data analytics and insights
    ├── api-manager/            # API endpoint management and routing
    ├── api/                    # API endpoints
    ├── docs/                   # Documentation
    ├── extras/                 # Additional utilities and helper scripts
    ├── load-balancer/          # Traffic distribution across services
    ├── monitoring-service/     # Service health and performance monitoring
    ├── node-manager/           # Node lifecycle operations
    ├── notification-manager/   # Notifications and alerting
    ├── schema/                 # Database schema and utilities
    └── sensor-manager/         # Sensor integration and data collection
```

## Getting Started

### 1. Setup

- Clone the project repository and navigate to the project directory.
- Ensure your application meets platform compatibility requirements (OS, language, dependencies).
- Deploy using the provided deployment script or tooling. See `docs/` for full deployment details.

### 2. Dependencies

- **Kafka** — powers the platform's distributed architecture, replication, and high throughput.
  [Download Kafka](https://kafka.apache.org/downloads)
- **ThingsBoard** — used for sensor integration and visualization.
  [Download ThingsBoard](https://thingsboard.io/download/)
- **OneM2M** — standard for machine-to-machine communication. Ensure devices support OneM2M and are configured to send data via MQTT.

### 3. Configuration

- Adjust default settings per microservice under `./config/` (XML or JSON).
- Set up password-based authentication or LDAP as needed.
- Store API keys securely.
- Register sensors on the platform and note their unique IDs and metadata.

For further assistance, refer to the detailed documentation in `docs/` or reach out to the support team.

## Future Scope

- **Broader Integration** — support for more IoT device types
- **Smarter Analysis** — upgraded data processing for clearer insights
- **Safety First** — strengthened security for users and devices
- **Ease of Use** — streamlined interfaces and workflows
- **Growing with Demand** — scaling to handle increased connections and data volume

