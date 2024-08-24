Spring PetClinic Microservices
## Overview

This project is a microservices-based implementation of the Spring PetClinic application. The application is designed to be run in both development and production environments using Docker and Docker Compose. It includes services such as a Spring Boot application and MySQL/PostgreSQL databases, with Nginx as a load balancer in the production environment.

## Table of Contents
- [Overview](#overview)
- [Project Structure](#project-structure)
- [Docker Setup](#docker-setup)
    - [Development Environment](#development-environment)
    - [Production Environment](#production-environment)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
  .
├── Dockerfile
├── docker-compose.yml
├── dockerComposeDev.yml
├── dockerComposeProd.yml
├── src/
│   └── main/
│       └── java/
│           └── com/
│               └── example/
│                   └── petclinic/
│                       └── ...
└── README.md
## Docker Setup

### Prerequisites

- **Docker**: Make sure you have Docker installed. Get Docker
- **Docker Compose**: Docker Compose is required to run the `docker-compose` commands. Get Docker Compose

### Installation

1. **Clone the repository**:
   git clone https://github.com/mostafa-7ussein/Devops.git
	cd Devops
	
**Build and run the application**:

- For Development:
  docker-compose -f dockerComposeDev.yml up --build
docker-compose -f task10/dockerComposeProd.yml up --build
### Usage

- **Access the application**:
    
    - Development: `http://localhost:2011`
    - Production: `http://localhost:1551`
- **Database access**:
    
    - MySQL (Development): `mysql -u petclinic -p -h 127.0.0.1 -P 4004`
    - PostgreSQL (Production): `psql -U petclinic -h 127.0.0.1 -p 5432`

### Contributing

Contributions are welcome! Please submit a pull request or open an issue to discuss what you would like to change.

### License

This project is licensed under the MIT License. See the LICENSE file for details.
