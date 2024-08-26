Java Spring Boot Application with MySQL Database
# Overview

This project uses Docker to containerize a Java Spring Boot application along with a MySQL database. The setup is defined using a Dockerfile for the application and a Docker Compose file to orchestrate both the application and the database services.

### Explanation

- **FROM eclipse-temurin
    
    **: Specifies the base image, which is Eclipse Temurin, an OpenJDK distribution.
- **WORKDIR /app**: Sets the working directory inside the container to `/app`.
- **COPY . .**: Copies the entire content of your project into the `/app` directory inside the container.
- **EXPOSE 8080**: Exposes port 8080 for the application.
- **RUN ./mvnw package**: Runs the Maven Wrapper to package the application into a JAR file.
- **CMD ["/bin/sh", "-c", "java -jar /app/target/*.jar"]**: Runs the Spring Boot application using the JAR file created by Maven.

## Docker Compose Setup

The following `docker-compose.yml` file is used to orchestrate the services:
### Explanation

- **db**: This service uses the official MySQL image.
    
    - **healthcheck**: Verifies that the MySQL service is up and running.
    - **environment**: Sets the MySQL root password, a user, and the database name.
    - **ports**: Maps MySQL's default port (3306) to port 4004 on your machine.
    - **volumes**: Stores MySQL data persistently in a Docker volume named `volumedb`.
- **app**: This service builds and runs the Java Spring Boot application using the Dockerfile.
    
    - **depends_on**: Ensures that the `db` service is healthy before starting the application.
    - **environment**: Configures the Spring Boot application to connect to the MySQL database and activates the MySQL profile.
    - **ports**: Maps port 8080 in the container to port 4005 on your machine.

### Volumes

- **volumedb**: This volume stores the MySQL data, ensuring persistence even if the MySQL container is stopped or removed.
## Building and Running the Application
### Build and Run the Services

Use Docker Compose to build and start the services:
docker-compose up --build

### Access the Services

- **Spring Boot Application**: Open your browser and go to `http://localhost:4005` to access the application.
    
- **MySQL Database**: You can connect to the database using a MySQL client like so:
- mysql -u petclinic -p -h 127.0.0.1 -P 4004

### Stopping the Services

To stop the services, run:
docker-compose down
This command stops and removes the containers, but the MySQL data remains intact in the `volumedb` volume.
