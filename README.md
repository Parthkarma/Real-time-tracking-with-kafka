# Real-time Tracking System with Kafka



## Overview

This project implements a real-time tracking system utilizing Apache Kafka for message streaming between delivery services and end users. The system enables live tracking of deliveries, providing timely updates and location information to enhance the delivery experience.

## Features
 Designed a Kafka event-driven system for 200K+ concurrent requests.
 Implemented tracking system using Kafka producers and consumers.
 Delivery Boy service publishes, End User service consumes updates.
 Separated services for efficient data streaming.
## Architecture

The system is built on a microservices architecture with these key components:

1. **Delivery Service**: Mobile application for delivery personnel to broadcast location and status
2. **Kafka Message Broker**: Central streaming platform for real-time data distribution
3. **Tracking Service**: Processes and enriches location data streams


## Technology Stack

- **Messaging**: Apache Kafka, Kafka Streams


## Prerequisites

- JDK 11 or later
- Maven 3.6.3 or later
- Docker and Docker Compose
- Node.js and npm (for frontend applications)
- Apache Kafka 2.8.0 or later

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/Parthkarma/Real-time-tracking-with-kafka.git
cd Real-time-tracking-with-kafka
```

### Start the Infrastructure

Using Docker Compose to start Kafka and other dependencies:

```bash
docker-compose up -d
```

### Build and Run the Services

#### Tracking Service

```bash
cd tracking-service
mvn clean install
mvn spring-boot:run
```

#### Delivery App Backend

```bash
cd delivery-service
mvn clean install
mvn spring-boot:run
```

#### End User App Backend

```bash
cd user-service
mvn clean install
mvn spring-boot:run
```

#### Web Frontend

```bash
cd web-client
npm install
npm start
```

The web application will be available at `http://localhost:3000`

## System Components

### Delivery Personnel App

- Mobile application for delivery personnel
- Features:
  - Auto-location sharing
  - Status updates (Picked up, In transit, Delivered)
  - Route optimization
  - Communication with customers

### Kafka Streams Application

- Processes location data in real-time
- Calculates ETAs based on current position and traffic data
- Detects delivery zones and triggers notifications
- Aggregates data for analytics

### End User Application

- Web and mobile interfaces for customers
- Features:
  - Live map with delivery location
  - Status notifications
  - ETA updates
  - Delivery history
  - Rating and feedback system


## Kafka Topics

- `delivery-locations` - Stream of GPS coordinates from delivery personnel
- `delivery-status-updates` - Delivery status change events
- `user-notifications` - Notifications to be sent to end users
- `delivery-analytics` - Aggregated data for analytics processing

## Configuration

### Kafka Configuration

Edit `application.properties` for each service:

```properties
# Kafka configuration
spring.kafka.bootstrap-servers=localhost:9092
spring.kafka.consumer.group-id=tracking-group
spring.kafka.consumer.auto-offset-reset=earliest
```

### Application Configuration

Configure tracking parameters in `tracking-service/src/main/resources/application.properties`:

```properties
# Tracking configuration
tracking.update-frequency-seconds=10
tracking.geofence-radius-meters=200
tracking.eta-calculation-algorithm=google-maps
```

## Deployment

The application is containerized and can be deployed to any Kubernetes cluster:

```bash
# Build Docker images
docker-compose build

# Push to container registry
docker-compose push

# Deploy to Kubernetes
kubectl apply -f kubernetes/
```


## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

Parth - [GitHub](https://github.com/Parthkarma)

Project Link: [https://github.com/Parthkarma/Real-time-tracking-with-kafka](https://github.com/Parthkarma/Real-time-tracking-with-kafka)

## Acknowledgements

- [Apache Kafka](https://kafka.apache.org/)
- [Spring Boot](https://spring.io/projects/spring-boot)
