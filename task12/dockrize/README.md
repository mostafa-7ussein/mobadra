WordPress and MySQL with phpMyAdmin
## Overview
This project uses Docker Compose to set up a WordPress site, a MySQL database, and phpMyAdmin for database management. The services are defined in a `docker-compose.yml` file and are set to restart automatically if any issues occur.

Services
- **MySQL Database**: Runs a MySQL container.
- **WordPress**: Runs a WordPress container.
- **phpMyAdmin**: Provides an interface to manage the MySQL database.
## Prerequisites

Ensure you have Docker and Docker Compose installed on your machine.
### Run the Services

Start the services using Docker Compose:
`docker-compose up -d`
### Access the Services

- **WordPress**: Open your browser and go to `http://localhost:1000` to access the WordPress setup page.
- **phpMyAdmin**: Go to `http://localhost:8008` to manage the MySQL database.
### Stopping the Services

To stop the services, run:
`docker-compose down`
This command will stop and remove the containers, but the data in the MySQL database will be preserved in the `mysql` volume.

## Volumes

- **mysql**: This volume stores the MySQL database files and ensures persistence between container restarts.
## Environment Variables

- `MYSQL_ROOT_PASSWORD`: Root password for the MySQL database.
- `MYSQL_DATABASE`: The name of the database used by WordPress.
- `MYSQL_USER`: Username for the MySQL database.
- `MYSQL_PASSWORD`: Password for the MySQL user.
- `WORDPRESS_DB_HOST`: The hostname and port of the MySQL service.
- `WORDPRESS_DB_USER`: The MySQL database user for WordPress.
- `WORDPRESS_DB_PASSWORD`: The password for the WordPress database user.
- `WORDPRESS_DB_NAME`: The name of the WordPress database.

