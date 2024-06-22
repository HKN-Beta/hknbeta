# Traefik Services

## Overview

hknbeta makes use of Traefik, a reverse proxy and load balancer, to route incoming requests to the appropriate service.

The services as handled by Traefik form the HKN infrastructure on hknbeta.  Traefik is configured to route incoming requests to the appropriate service based on the URL path.  For example, the frontend page for the POS service served at /pos comes from the `storefront` Docker image, built from [HKN-Beta/hknpos-frontend](https://github.com/HKN-Beta/hknpos-frontend).

Each HKN service has an associated GitHub repository, configured to run GitHub Actions on push.  The pushed code is built into a Docker image and deployed to the server via GitHub Actions.  

Currently, Traefik will not automatically route requests to a service unless the service is running.  This means that if you push a new service to the server, you will need to restart the Traefik service to get it to recognize the new service.  This is a security measure intended to avoid trigger-happy developers from accidentally exposing a service to the internet before it's ready!

For more mission-critical containers like the POS, pushes to `main` are protected.  Any attempt to modify POS code requires review from the facilities director or IT committee before it is merged into main and pushed to hknbeta.

Each page under this section describe the development and deployment process for each service under Traefik.

## Managing Traefik

Traefik itself is a Docker container, which manages the other Docker containers when a docker-compose file is written to include the other services.  The Traefik container is configured to listen on ports 80 and 443, and to route incoming requests to the appropriate service based on the URL path.

To restart the Traefik service on hknbeta, you can run the following commands in your terminal after cd'ing to the `~/traefik` directory.

```bash
docker compose down
docker compose --env-file default.env up -d
```

You can also use

```bash
docker compose --env-file default.env restart
```

Note that there is no hyphen between `docker` and `compose`.

The `default.env` file contains passwords for PostgreSQL.  To avoid having to deal with stored passwords, you should minimize exposed ports to the Internet and let Traefik handle the routing.

## Restarting one specific service

If you need to restart one specific service, you can run the following command in your terminal after cd'ing to the `~/traefik` directory.

```bash
docker compose restart <service_name>
```

## SSL certificates

The docker-compose.yml and traefik.yml files are configured to automatically fetch and/or renew SSL certificates from Let's Encrypt using the ACME protocol.  This means that you don't need to worry about SSL certificates for your service, as long as it's running under Traefik.