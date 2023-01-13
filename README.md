# Nginx Tutorial
This is a containerized Nginx server that serves a simple static HTML website.
Certbot has been added to help set up HTTPS if desired.

## Setup
The project uses the following:
- Nginx
- Docker
- Docker Compose

Ensure Docker and Docker Compose are installed before continuing.

## Running the Application
To build and run, enter ```docker compose up -d --build```, then
go to http://localhost using your web browser.

### Setting Up HTTPS With Certbot
There are configurations already set up via `cli.ini` in the `certbot` directory.
To receive an SSL certificate using those configurations, run:
```
docker compose run --no-deps --rm certbot certonly -d [enter domain here]
```

Fill out the prompt, then configure Nginx to use the SSL certificate and domain.

To renew the SSL certificate and use the newest certificate, run:
```
docker compose run --no-deps --rm certbot renew && docker exec nginx nginx -s reload
```

**NOTE**: Ensure port 443 is exposed in `docker-compose.yml` for HTTPS.
