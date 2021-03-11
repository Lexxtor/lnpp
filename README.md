<!-- markdownlint-disable MD033 MD041 -->

<p align="center">
  <span>
    <img src="https://raw.githubusercontent.com/saltchang/lnpp/main/static/images/LNPP_LOGO.png" height="200">
    <h1 align="center">LNPP</h1>
  </span>
</p>

This is for you all **LNPPers**.  
A Docker Compose setup for the environment of LNPP.

- **L**inux
- **N**ginx
- **P**ostgreSQL
- **P**HP

## Requirements

- Docker
- Docker Compose
- Laravel (Optional)

## Quick Start

Setup the environment variables:

```bash
cp .env.example .env
```

Run the Docker Compose:

```bash
docker-compose up
```

Or run it in background:

```bash
docker-compose up -d
```

Open the browser and visit the **[localhost](http://localhost)**, you will see your app running happily.

### Database

You can access the postgreSQL at `127.0.0.1:5432`(default).

Notice that `docker/postgres/*` will be created.  
Those files are Database archives for PostgreSQL.

Feel free to edit the `docker/postgres/.gitignore` if you need.

## Commands

### Run

```bash
# Run containers in foreground
docker-compose up

# Or run in background and see the logs (recommended)
docker-compose up -d
docker-compose logs --tail=1000 -f

# --tail: for limit the output logs
# -f: keep following the logs updated

# If you need to build and then run
docker-compose up -d --build
```

### Stop

```bash
docker-compose down
```

### List all your running containers

```bash
docker ps

# If your want to check the stopped containers
docker ps -a
```

## Environment Variables

The environment variables defined in `.env` files:

- `APP_NAME`: The app name
- `POSTGRES_USER`: The username to be created for postgres
- `POSTGRES_PASSWORD`: The password to be created for the user of postgres
- `POSTGRES_DB`: The database name to be created for the postgres
- `PGDATA_PATH`: The directory for storing the localdata of postgres
- `WEB_SERVER_PORT`: The public port for your web application

## Docker Resources

In `docker/`, there are some initial configuration files for the PHP and Nginx.

### PHP

- `php/Dockerfile`: For config the docker image of php
- `php/php.ini`: For config the php to use

### Nginx

- `nginx/nginx.conf`: For config the nginx web server

## Multiple Servers

To run more server at one time, copy the `docker/nginx/nginx.conf` and edit the config for creating multiple web server, and then restart the docker compose.

See on [Stackoverflow](https://stackoverflow.com/questions/49489482/docker-nginx-multiple-apps-on-one-host).

## Laravel

In the `src/`, create your Laravel application.

Optional: You can change the setting `index public/index.php;` in `docker/nginx/nginx.conf` if you need.

Restart the docker compose and you will see the application of Laravel.

## More

I hope these contents can help you guys.

Thanks and happy hacking.
