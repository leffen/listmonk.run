# Listmonk Deployment with Docker Compose

This repository contains the configuration files to deploy [Listmonk](https://listmonk.app/), a self-hosted newsletter and mailing list manager, using Docker Compose.

## Prerequisites

- Docker installed on your system.
- Docker Compose installed.
- Basic understanding of Docker and Docker Compose.

## Project Structure

- `.gitignore`: Specifies files and directories to be ignored by Git.
- `docker-compose.yml`: Defines the services, networks, and volumes for the Listmonk and PostgreSQL containers.

## Setup Instructions

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd listmonk.run
   ```

2. Create a directory for uploads:
   ```bash
   mkdir uploads
   ```

3. Start the services:
   ```bash
   docker compose up -d
   ```

   - The `app` service runs the Listmonk application.
   - The `db` service runs the PostgreSQL database.

4. Access the Listmonk web interface:
   - Open your browser and navigate to [http://localhost:9000](http://localhost:9000).
   - If you set `LISTMONK_ADMIN_USER` and `LISTMONK_ADMIN_PASSWORD` environment variables, use them to log in. Otherwise, create an admin user via the web interface.

## Configuration

- The `docker-compose.yml` file is pre-configured to use environment variables for database credentials and other settings.
- To customize the configuration, edit the `docker-compose.yml` file or pass environment variables during deployment.

## Data Persistence

- The PostgreSQL data is stored in a Docker volume named `listmonk-data`.
- Uploaded files are stored in the `uploads` directory on the host machine, which is mounted to `/listmonk/uploads` in the container.

## Stopping the Services

To stop the services, run:
```bash
docker compose down
```

## Updating Listmonk

To update to the latest version of Listmonk:
1. Pull the latest image:
   ```bash
   docker pull listmonk/listmonk:latest
   ```
2. Restart the services:
   ```bash
   docker compose up -d
   ```

## Troubleshooting

- Check the logs for any issues:
  ```bash
  docker compose logs
  ```
- Ensure that the `uploads` directory has the correct permissions.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
