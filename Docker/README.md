# 🐳 Docker Multi-Stage Build and Deployment for Django Application

This guide demonstrates how to create Dockerfiles using a multi-stage build approach for a Django application, as well as how to configure a MySQL database with environment variables. Additionally, it includes a Docker Compose file for networking and deployment.

![docker_logo](/Figures/docker_logo.png)
## Multi-Stage Dockerfile for Django Application

### Build Stage
- Use the official Python image (`python:3.11-alpine`) as the base image.
- Set environment variables to optimize Python performance.
- Install the necessary build dependencies (e.g., `musl-dev`, `pkgconfig`, `mariadb-dev`).
- Copy the `requirements.txt` and install Python dependencies, then to the container.

### Final Stage
- Use the official Python image again, but without the build dependencies.
- Copy the installed dependencies and the application code from the build stage to the final image.
- Expose the port the Django application will run on (default is port `8000`).
- Define the command to run the Django application using `python manage.py runserver`.

## Dockerfile for MySQL Database with Environment Variables

- Use the official MySQL image (`mysql:8.0`) as the base image.
- Define `ARG` variables (`DB_USER`, `DB_PASS`) for MySQL username and password.
- Copy the initial SQL script to `/docker-entrypoint-initdb.d/` to initialize the database when the container starts.
- Expose MySQL's default port (`3306`).

## Docker Compose Configuration for Network and Deployment

- **MySQL Service**: 
  - Use a custom MySQL image.
  - Expose port `3306` and persist data using Docker volumes (`mysql_data`).
  - Define the `app_network` for service networking.

- **Django Application Service**: 
  - Use a custom Django application image.
  - Set a dependency on the MySQL service (`depends_on`).
  - Expose port `8000` and use a startup command with a 45-second delay to ensure MySQL is ready.
  - Also connects to the `app_network`.
  - Create a volume for the database.

## Docker Commands

1. **Build the Docker images**:
    ```bash
    docker-compose build
    ```

2. **Start the containers**:
    ```bash
    docker-compose up
    ```

3. **Stop and remove the containers**:
    ```bash
    docker-compose down
    ```

This setup includes multi-stage Dockerfile optimization, environment variables for database credentials, and a Docker Compose configuration to manage services and their networking.
