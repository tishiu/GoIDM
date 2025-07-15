# GoIDM - Golang-based Download Manager

[![Go Version](https://img.shields.io/badge/Go-1.18+-blue.svg)](https://golang.org)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

## Overview
GoIDM is a robust download management system built with Golang. It provides efficient and reliable file downloading capabilities through a microservices architecture and modern cloud-native technologies.

## Architecture

### Service Layer
GoLoad utilizes a microservices architecture with clear separation of concerns:

```
+-------------------+
|    API Gateway    |
| (gRPC & HTTP)     |
+-------------------+
        |
        v
+-------------------+
|  Session Service  |
| (Authentication)  |
+-------------------+
        |
        v
+-------------------+
| Account Service   |
| (User Management) |
+-------------------+
        |
        v
+-------------------+
| Download Service  |
| (File Operations) |
+-------------------+
```
<img width="953" height="555" alt="image" src="https://github.com/user-attachments/assets/127305a2-e7af-4148-b2b1-451c22628fc8" />

### Technology Stack
- **Backend**: Golang 1.18+
- **Database**: MySQL (Relational Data)
- **Message Queue**: Kafka (Asynchronous Processing)
- **Caching**: Redis (Session & Rate Limiting)
- **Storage**: AWS S3 (Optional)
- **Container**: Docker & Docker Compose

## Key Features

### Scalability
- Horizontal scaling via Docker containers
- Load balancing through API Gateway
- Distributed processing with Kafka
- Caching layer for improved performance

### Reliability
- Fault-tolerant architecture
- Retry mechanisms for failed downloads
- Health monitoring and metrics
- Graceful degradation

### Performance
- Asynchronous processing
- Batch operations
- Connection pooling
- Efficient memory management

## Project Structure
```
GoLoad/
├── api/          # API endpoints and handlers
├── cmd/          # Application entry points
├── configs/      # Configuration files
├── deployments/  # Docker and Kubernetes manifests
├── internal/     # 
│   ├── service/  # Business logic
│   ├── repo/     # Data access layer
│   ├── middleware/ # Cross-cutting concerns
│   └── util/     # Helper functions
├── go.mod        # Dependency management
└── go.sum        # Dependency checksums
```

## Getting Started

### Prerequisites
- Go 1.18 or higher
- Docker & Docker Compose
- MySQL 8.0+
- Kafka cluster
- Redis server
- AWS credentials (for S3)

### Installation
```bash
# Clone the repository
git clone [repository-url]

cd GoLoad

# Build the project
docker-compose build

# Start all services
docker-compose up -d
```

## Development

### Running Tests
```bash
# Run unit tests
go test ./... -v

# Run integration tests
go test -tags=integration ./... -v

# Run performance tests
go test -tags=perf ./... -v
```

### Local Development
```bash
# Start development environment
docker-compose -f docker-compose.dev.yml up

# Run migrations
docker-compose exec db mysql -u root -p < database/migrations.sql
```

## Deployment

### Production Deployment
```bash
# Build production images
docker-compose -f docker-compose.prod.yml build

# Deploy to production
docker-compose -f docker-compose.prod.yml up -d
```

### Kubernetes Deployment
```bash
# Deploy to Kubernetes
kubectl apply -f deployments/kubernetes/
```

## Monitoring & Logging

### Metrics
- Prometheus for metrics collection
- Grafana for visualization
- Custom metrics for download performance

### Logging
- Structured logging
- ELK stack integration
- Log rotation and retention

## Security

### Authentication & Authorization
- JWT-based authentication
- Role-based access control
- Rate limiting
- Input validation

### Data Protection
- SSL/TLS encryption
- Secure file handling
- Audit logging
- Regular security updates

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support
For support, please:
- Open an issue on GitHub
- Join our Discord community
- Email tranmap04@gmail.com
- Follow me on GitHub: [tishiu](https://github.com/tishiu)
