Java Spring Boot Application Docker Setup
Overview
This project uses a Dockerfile to containerize a Java Spring Boot application. The Dockerfile is based on the Eclipse Temurin base image and automates the build and run process for the application.

## Dockerfile Breakdown
### Explanation

- **FROM eclipse-temurin**
    
    : This line specifies the base image for the container. Eclipse Temurin is an OpenJDK distribution.
    
- **WORKDIR /app**: Sets the working directory inside the container to `/app`. All subsequent commands are run from this directory.
    
- **COPY . .**: Copies the entire content of the project into the `/app` directory inside the container.
    
- **EXPOSE 8080**: Exposes port 8080 to allow external access to the application once it's running inside the container.
    
- **RUN ./mvnw package**: Runs the Maven Wrapper command to package the application. This step builds the application and creates an executable JAR file in the `target` directory.
    
- **CMD ["/bin/sh", "-c", "java -jar /app/target/*.jar"]**: Specifies the command to run the application. It uses a shell to execute the `java -jar` command, which starts the Spring Boot application using the JAR file created in the previous step.
- ## Building the Docker Image

To build the Docker image, run the following command from the project root directory (where the Dockerfile is located):
docker build -t my-java-app .

## Running the Docker Container
After building the image, you can run the container using:
docker run -p 8080:8080 my-java-app
- `-p 8080:8080`: Maps port 8080 on your local machine to port 8080 in the container, allowing you to access the application at `http://localhost:8080`.
## Accessing the Application

Once the container is running, open your web browser and navigate to:
http://localhost:8080

## Stopping the Container

To stop the running container, you can use the `docker ps` command to find the container ID and then stop it with:
docker stop <container_id>
