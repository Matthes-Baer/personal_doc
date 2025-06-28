# DevOps

This section includes information for Docker, Kubernetes, and other DevOps-related topics.

## Docker

### Helpful Docker Commands

- Enter a mariadb shell (with Docker Desktop you already have the shell accessible): `docker exec -it container_name -u root -p`

- Build an image with a set variable by adding `ARG SOME_VAR` and then afterwards you can use it like `RUN npm config set -- //npm.fontawesome.com/:_authToken="${SOME_VAR}"` (within the Dockerfile) if you run a command like: `docker buildx build --build-arg SOME_VAR=123123 -t my_application .`

- Create a custom volume (to be able to name it): `docker volume create named_volume`

- Stop a Container: `docker stop container_name_or_id`

- Remove a Container: `docker rm container_name_or_id`

- Run a mariaDB container with a specific name and volume: `docker run --name my-mariadb-container -p 3306:3306 -v <volume_name>:/var/lib/mysql -e MARIADB_ROOT_PASSWORD=my_secret_password -d mariadb` (potentially add `--bind-address=0.0.0

- Run a Postgres container with a specific name and volume (user is `postgres` by default / when connecting via HeidiSQL not every library works for connecting): `docker run --name my_postgres_container -p 5432:5432 -v <volume_name>:/var/lib/postgresql/data -e POSTGRES_PASSWORD=my_secret_password -d postgres`
  what paths you need to use.

- Overview of docker disk usage: `docker system df`

- View all docker images on the machine: `docker images`

- Build a docker image (in the same directory as the application): `docker buildx build -t IMAGE_NAME:TAG .`

- View all current running and stopped processes: `docker ps -a`

- Start a container with .env file in project (Port to reach it:Port the application was exposed to through dockerfile): `docker run -p 3000:5000 --env-file .env APP_NAME:latest`

- Remove a docker image: `docker rmi IMAGE_NAME:TAG`

- Stop a container: `docker stop CONTAINER_NAME_OR_ID`

- Remove a stopped container: `docker rm CONTAINER_NAME_OR_ID`

- Delete all non-used and hanging images: `docker image prune -a`

- Delete the builder cache: `docker builder prune`

- Delete the volumes: `docker volume prune`

- Delete stopped containers: `docker container prune`

- View the layers of the corresponding docker image: `docker history IMAGE_NAME:TAG`

- Run the docker-compose.yml file: `docker-compose up`

- Stop the docker compose applications: `docker-compose down`

- Rebuild the containers from the docker compose: `docker-compose up --build`

- View the docker compose logs: `docker-compose logs -f`


### General Docker Information

- When using Docker Desktop, assign a volume like this for mariadb:
  - Host Path`/var/lib/docker/volumes/<volume-name>/_data`
  - Container Path `/var/lib/mysql`

- When using Docker Desktop, assign a volume like this for postgres:
  - Host Path: `/var/lib/docker/volumes/<volume_name>/_data`
  - Container Path: `/var/lib/postgresql/data`
  - Don't forget the `POSTGRES_PASSWORD` env

- When using Docker Desktop with pgadmin, you have to use `host.docker.internal` for the host name if you want to connect to a local postgres docker container

- In Docker Desktop you can assign user/roles for a postgres server, which can be the owner of some database in that server. These user/roles can then have different passwords and permissions.

- Connection string for some postgres database: `postgres://<username>:<password>@<postgres_server>:5432/<database_name>?sslmode=verify-full` - The `verify-full` helps to make sure that the owner (the user) can access the database, even if the user has no permissions to access the server itself. This is for ssl connections, so you need to have the certificate files in the right place. The `sslmode` can also be set to `require`, which is less strict, but still requires a valid certificate. This is useful for pgadmin, for example, with heidiSQL, you don't have to set the `sslmode` to `require` or `verify-full`, as it will work without it.

- Using the Docker Desktop Export Volume feature:
  1. Export a volume in a file
  2. Create a new volume and overwrite the new volume by importing the exported volume
  - For MariaDB: Start new container with new volume (described above), and then import the exported volume
  - For Postgres: Using the command from above, will actually mount two volumes to the container (it creates a new random one).
    - The import process then won't work like with mariadb.
    - Instead, start the container via Docker Desktop directly (this will actually only bind the volume you want) - see above for paths you need to use

- When setting a pnpm config variable in a dockerfile, this only counts for the current user. So when the user changes, the variables may be lost. If you use `pnpm install` after a user change in such situations and the install process is dependent on the pnpm config variables it will fail.

- For all containers it is important to use an exposed port. Otherwise, you won't be able to access the container from your host machine.

- When creating a new mariaDB container in portainer, you have to add a `MARIADB_ROOT_PASSWORD` env variable. The username is automatically set to "root" in this case. This way you are able to connect to this container with HeidiSQL.

- When creating a new postgreSQL container in portainer, you have to add `POSTGRES_PASSWORD` env variable. The username is automatically set to `postgres` by default. This way you are able to connect to this container with HeidiSQL, for example. A new PostgreSQL database can be picked from the connection window in HeidiSQL, the tables are placed within the public schema. To create a custom schema use `CREATE SCHEMA my_schema AUTHORIZATION postgres;` via SQL.

- If a Docker container needs to be connected to another docker container, they need to be in the same bridge network (I think) and they need to use the container's IP while you on your local machine may be able to just use localhost, for example.

- Docker Compose makes it possible to use containers name to connect to each other instead of IPs

- Docker Desktop enables the use of docker within Windows (so it doesn't have to be done through wsl anymore)


## Kubernetes

### Helpful Kubernetes Commands

- ...

### General Kubernetes Information

- Kubernetes is a container orchestration platform that manages groups of containers, often created using Docker. It handles tasks like scaling, distribution, and connectivity between containers, making it easier to manage large-scale containerized applications and their infrastructure. For instance, while you can set up Docker on a single server and route traffic to a lot of instances, or deploying multiple services that dynamically scale based on load, becomes challenging. Kubernetes addresses these complexities. Its command-line tool, `kubectl`, enables you to interact with Kubernetes clusters by communicating with the Kubernetes API server.




