# Infrastructure

Infrastructure configuration

## Dev environment

### Step 1

Sign in to container registry from local docker at `ghcr.io`

First create a new [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) with permissions:
- read:packages
- write:packages
- delete:packages


Save the token as an environment variable:

```sh
export CR_PAT=YOUR_TOKEN
```
Sign in to ghcr:
```sh
echo $CR_PAT | docker login ghcr.io -u YOUR_USERNAME --password-stdin
```


### Step 2

Clone this repo:
```sh
git clone https://github.com/No-Code-DS/infrastructure.git
cd infrastructure
```

Set `ENGINE_PATH` and `FRONTEND_PATH` to directories containing appropriate Dockerfiles in `.env` file.

Inside `docker-compose.override.yml` comment out any service to not use the local version, instead it will pull the latest image from ghcr.

Build your local image:

```sh
docker compose build
```

Start microservices with:

```sh
docker compose --env-file .env up -d
```

If anything changed `docker-compose.override.yml` after it's last run, one should use `--force-recreate` flag to reflect the changes made.

```sh
docker compose --env-file .env up --force-recreate -d
```

To stop them run:
```sh
docker compose down
```
