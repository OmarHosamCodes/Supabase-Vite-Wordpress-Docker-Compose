```markdown
# Quadrillion Local Development Environment

This repository contains the Docker Compose setup for the Quadrillion project, providing a complete local development environment. It includes Supabase for the backend, WordPress for content management, and several Next.js applications for the frontend, all containerized for easy setup and management.

## Project Structure

The repository is organized into the following main components:

- `loyal-rev-admin-panel/`: The admin dashboard application.
- `loyal-rev-api/`: The core API server.
- `loyal-rev-UI-integration/`: Frontend components for UI integration.
- `loyal-rev-website/`: The main project website.
- `supabase/`: Supabase configuration and data.
- `wp-plugin/`: The custom WordPress plugin for Quadrillion.
- `nginx/`: Nginx configuration.
- `docker-compose.yml`: The main Docker Compose file orchestrating all the services.
- `README.md`: This file.

## Prerequisites

- Docker and Docker Compose must be installed on your system.
- You need to create a `.env` file in the root of the project. You can copy the contents of `.env.example` and fill in the required values.

## Getting Started

1.  **Clone the repository:**
    ```bash
    git clone <your-repo-url>
    cd Quadrillion
    ```

2.  **Set up the environment:**
    Create a `.env` file in the root directory by copying `.env.example` and updating the variables as needed.

3.  **Start the services:**
    ```bash
    docker-compose up -d
    ```

4.  **Access the services:**
    Once the containers are running, you can access the different parts of the application:

    - **Supabase Studio:** [http://localhost:8000](http://localhost:8000)
    - **WordPress Admin:** [http://localhost:8090/wp-admin](http://localhost:8090/wp-admin)
    - **phpMyAdmin:** [http://localhost:8091](http://localhost:8091)
    - **Admin Panel:** [http://localhost:8092](http://localhost:8092)
    - **UI Integration:** [http://localhost:8093](http://localhost:8093)
    - **API Server:** [http://localhost:8095](http://localhost:8095)

5.  **Stopping the environment:**
    To stop all running containers, use the following command:
    ```bash
    docker-compose down
    ```

## Services Overview

The `docker-compose.yml` file defines the following services:

- **Supabase:** A suite of services providing the backend infrastructure, including:
  - `studio`: The Supabase dashboard.
  - `kong`: The API gateway.
  - `auth`: GoTrue for authentication.
  - `rest`: PostgREST for RESTful API access to the database.
  - `realtime`: Realtime broadcasting service.
  - `storage`: S3-compatible object storage.
  - `imgproxy`: Image transformation service.
  - `meta`: Manages database metadata.
  - `functions`: Edge functions runtime.
  - `analytics`: Logflare for analytics.
  - `db`: PostgreSQL database.
  - `vector`: Log aggregation.
  - `supavisor`: Connection pooler.

- **WordPress:**
  - `wordpress`: The WordPress application.
  - `wordpress_db`: MySQL database for WordPress.
  - `wpcli`: WP-CLI for command-line management.
  - `phpmyadmin`: Web-based database management for the WordPress database.

- **Frontend Applications:**
  - `dashboardui`: The admin panel application.
  - `iframes`: The UI integration application.

- **Backend:**
  - `api`: The core API server.

## Environment Variables

The `.env` file is crucial for configuring the services. Below is an example with explanations for the key variables.

```env
# Supabase
POSTGRES_PASSWORD=your_strong_password
JWT_SECRET=your_jwt_secret
ANON_KEY=your_anon_key
SERVICE_ROLE_KEY=your_service_role_key

# WordPress
WP_PORT=8090
WP_DB_USER=wordpress
WP_DB_PASSWORD=wordpress
WP_DB_NAME=wordpress

# phpMyAdmin
PMA_PORT=8091

# Frontend Apps
DASHBOARD_PORT=8092
IFRAME_PORT=8093

# API
API_PORT=8095

# ... other variables
```

Make sure to replace the placeholder values with your actual secrets and configuration.

This README provides a basic guide to setting up the Supabase development environment using Docker Compose.  For more detailed information about Supabase and its services, please refer to the official Supabase documentation: [https://supabase.com/docs](https://supabase.com/docs)