# Infrastructure

Infrastructure configuration

### Dev environment

Set `ENGINE_PATH` and `FRONTEND_PATH` to directories containing appropriate Dockerfiles in `.env` file.

Start microservices with:

```sh
docker compose --env-file .env up -d
```

To stop them run:
```sh
docker compose down
```
