# DevOps

This section includes information for Docker, Kubernetes, and other DevOps-related topics.

## Useful Link
- [Chmod Calculator](https://chmod-calculator.com/)


## Docker

### Useful Docker Links
- ...

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

### Dockerfile commands

- `FROM` - Base image to build from -> `FROM node:20-alpine`
- `WORKDIR` - Set working directory -> `WORKDIR /app`
- `COPY` - Copy files into the image -> `COPY . .`
- `RUN` - Run command at build time -> `RUN npm install`
- `CMD` - Default command to run at container start -> `CMD ["node", "index.js"]`
- `ENTRYPOINT` - Like `CMD` but less overridable -> `ENTRYPOINT ["npm"]`
- `EXPOSE` - Document the port your app uses `EXPOSE 3000`
- `ENV` - Set environment variables -> `ENV NODE_ENV=production`
- `ARG` - Build-time variable -> `ARG NODE_VERSION=20`
- `LABEL` - Add metadata -> `LABEL maintainer="someone@example.com"`

### General Docker Information

- Provide envs for build process in dockerfile (for example, if you have envs in your `.npmrc` file to install fontawesome): `--mount=type=secret,id=auto-devops-build-secrets,mode=0500,uid=1000,gid=1000 . /run/secrets/auto-devops-build-secrets`
  - Afterwards, you may use this to build e.g.: `docker buildx build --secret id=auto-devops-build-secrets,src=C:\Users\<user>\AppData\repositories\auto-devops-build-secrets -t <tag>:latest`
  - In the file you can store your envs like you would do with a `.env` file.
  - This is basically the same process GitLab would use -> they also have a file prepared with the secrets, which is then provided with such a line in the dockerfile
  

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

### Docker Code Examples

#### Example Dockerfile

```dockerfile
# ----------- Stage 1: Build ------------
FROM node:20-alpine AS builder

# Set environment variables
ENV NODE_ENV=production \
    APP_HOME=/usr/src/app

# Create app directory
WORKDIR $APP_HOME

# Install dependencies separately to cache them
COPY package*.json ./
RUN npm ci --only=production

# Copy app source code
COPY . .

# Optional: Run tests or linters
# RUN npm run test

# Build assets (for frontend apps)
# RUN npm run build

# ----------- Stage 2: Production Image ------------
FROM node:20-alpine

# Set environment variables
ENV NODE_ENV=production \
    APP_HOME=/usr/src/app \
    PORT=3000

# Create non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Set working directory
WORKDIR $APP_HOME

# Copy only necessary files from builder
COPY --from=builder $APP_HOME .

# Change ownership
RUN chown -R appuser:appgroup $APP_HOME

# Use non-root user
USER appuser

# Expose the application port
EXPOSE $PORT

# Healthcheck (adjust as needed)
HEALTHCHECK --interval=30s --timeout=10s --start-period=10s --retries=3 \
  CMD wget --no-verbose --tries=1 --spider http://localhost:$PORT/health || exit 1

# Start the application
CMD ["node", "index.js"]
```

#### Example Docker Compose File

```yaml
version: "3.9"

services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: myapp
    ports:
      - "3000:3000"
    environment:
      NODE_ENV: production
      DATABASE_URL: postgres://user:password@db:5432/mydatabase
    volumes:
      - .:/usr/src/app:ro
    depends_on:
      db:
        condition: service_healthy
    healthcheck:
      test: ["CMD", "wget", "--spider", "-q", "http://localhost:3000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
    networks:
      - backend

  db:
    image: postgres:15-alpine
    container_name: mydb
    restart: always
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydatabase
    volumes:
      - db_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U user"]
      interval: 30s
      timeout: 5s
      retries: 5
    networks:
      - backend

volumes:
  db_data:

networks:
  backend:
```


## Kubernetes

### Useful Kubernetes Links
- [Kubernetes Tutorial](https://www.youtube.com/watch?v=2T86xAtR6Fo)
- [A visual guide on troubleshooting Kubernetes deployments](https://learnkube.com/troubleshooting-deployments)


### Helpful Kubernetes Commands

#### 📦 Work with Deployments / Pods
- Create or update resources from YAML: `kubectl apply -f <file>.yaml`
- Create a deployment quickly: `kubectl create deployment <name> --image=<image>`
- List all pods: `kubectl get pods`
- List all deployments: `kubectl get deployments`
- Detailed info about a specific pod: `kubectl describe pod <pod-name>`
- Delete a pod: `kubectl delete pod <pod-name>`
- Restart a deployment: `kubectl rollout restart deployment <name>`

#### 📡 Access & Logs
- View logs of a pod: `kubectl logs <pod-name>`
- Stream logs (like `tail -f`): `kubectl logs <pod-name> -f`
- Open a shell inside a pod: `kubectl exec -it <pod-name> -- /bin/sh`
- Forward port from pod to local machine: `kubectl port-forward <pod-name> 8080:80`
- Expose a deployment as a service: `kubectl expose deployment <name> --type=LoadBalancer --port=80`

#### 🔍 Cluster Info & Debugging
- List nodes in the cluster: `kubectl get nodes`
- Get cluster endpoint info: `kubectl cluster-info`
- Show full deployment details: `kubectl describe deployment <name>`
- Show all resources in the namespace: `kubectl get all`
- View recent cluster events (errors, etc.): `kubectl get events`

#### 📂 Namespaces & Contexts
- List all namespaces: `kubectl get namespaces`
- Show available kube contexts: `kubectl config get-contexts`
- Switch context (e.g. dev → prod): `kubectl config use-context <name>`
- Show active context: `kubectl config current-context`
- Work in a specific namespace: `kubectl -n <namespace> get pods`

#### 📁 Working with YAMLs
- See schema/help for a resource: `kubectl explain deployment`
- View deployment YAML: `kubectl get deployment <name> -o yaml`
- Delete resources defined in a file: `kubectl delete -f <file>.yaml`


### General Kubernetes Information

- Helm is a package manager for Kubernetes, designed to help developers and operators manage complex applications more easily. Just as tools like apt or yum manage packages on Linux, Helm manages Kubernetes resources using something called charts. A Helm chart is a collection of YAML templates and configuration files that define a set of Kubernetes resources needed to deploy and run an application or service. Helm simplifies the deployment process by allowing users to define reusable templates with configurable values. Instead of manually writing out dozens (or hundreds) of YAML files for each environment, you can define a chart once and customize it for different environments using values files. This makes it much easier to maintain consistency, manage upgrades, rollbacks, and apply best practices across different deployments. In essence, Helm abstracts away much of the complexity of Kubernetes resource management. It's especially valuable in CI/CD pipelines, DevOps workflows, and in environments where teams need to deploy and manage microservices or multi-component applications efficiently and repeatably.

- Ingress is a Kubernetes resource that manages external access to services within a cluster, typically HTTP. It provides a way to define rules for routing traffic to different services based on the request's host and path. Ingress controllers implement these rules, allowing you to expose multiple services under a single IP address or domain name. This is particularly useful for managing web applications, as it simplifies routing and can provide features like SSL termination, load balancing, and URL rewriting.

- GatewayAPI is a set of Kubernetes APIs that extend the Ingress functionality, providing more advanced traffic management capabilities. It allows for greater flexibility in defining how traffic is routed to services, including support for multiple protocols (HTTP, TCP, UDP), richer routing rules, and better integration with service meshes. GatewayAPI aims to standardize how traffic management is handled across different Kubernetes environments, making it easier to implement complex routing scenarios and policies. It's not to be confused with API Gateway, which is a separate service that provides a way to manage APIs in a Kubernetes cluster.

- Kubernetes is a container orchestration platform that manages groups of containers, often created using Docker. It handles tasks like scaling, distribution, and connectivity between containers, making it easier to manage large-scale containerized applications and their infrastructure. For instance, while you can set up Docker on a single server and route traffic to a lot of instances, or deploying multiple services that dynamically scale based on load, becomes challenging. Kubernetes addresses these complexities. Its command-line tool, `kubectl`, enables you to interact with Kubernetes clusters by communicating with the Kubernetes API server.

- Cluster: A Kubernetes Cluster is the entire system that includes a Control Plane (brains of the system) and multiple worker nodes (where apps run). You interact with the cluster to deploy and manage containerized applications.
- Control Plane: The Control Plane manages the entire Kubernetes cluster. It makes decisions about Scheduling, Scaling, Health checks, and Responding to events. Key Control Plane components include `kube-apiserver` (The main API. All tools & users talk to the cluster through this), `etcd` (Key-value store that holds all cluster data (like a database)), `kube-scheduler` (Decides which node a new Pod should run on), `kube-controller-manager` (Runs controllers that monitor cluster state and make corrections (e.g., replacing failed Pods)), `cloud-controller-manager` (Integrates with cloud providers (if used)). These usually run on Control Plane Nodes.
- Control Plane Node: A Control Plane Node is a VM or machine that runs the Control Plane components. In production, you may have multiple for high availability.
- Data Plane: This is where your actual applications run. Worker nodes are part of the Data Plane. Each Worker Node runs `kubelet` (Talks to the control plane. Makes sure containers run as expected), `kube-proxy` (Manages networking and load-balancing on the node), and container runtime (like Docker, which runs the containers).
- Worker Node: A Worker Node is a machine (VM or physical) that is part of the cluster and runs the containers via Pods. The control plane schedules Pods to run on these nodes.
- Pod: A Pod is the smallest deployable unit in Kubernetes. A Pod can have 1 or more containers (usually 1). All containers in a Pod share IP address, storage, and network namespace. You don’t run containers directly in Kubernetes — you run Pods.

- Container Runtime Interface (CRI): The Container Runtime Interface (CRI) enables Kubernetes to communicate with different container runtimes in a standardized way. The kubelet, which runs on every node, uses CRI to manage the lifecycle of containers—starting, stopping, and monitoring them. CRI uses gRPC as its protocol and abstracts the underlying container runtime, which allows Kubernetes to support multiple runtimes without being tightly coupled to any specific one. Common CRI-compatible runtimes include containerd (now the default in many Kubernetes setups), CRI-O, and previously Docker, which required a CRI shim (now deprecated). This interface ensures Kubernetes can be flexible and future-proof in how it runs containers.
- Container Network Interface (CNI): The Container Network Interface (CNI) provides Kubernetes with a standardized way to manage networking for Pods. Every time a Pod is created, Kubernetes uses a CNI plugin to set up its network: this includes creating a network namespace, assigning an IP address, and configuring routes so that Pods can communicate with each other and external services. CNI plugins are pluggable and you can choose different implementations based on your needs. Popular CNI plugins include Calico (with advanced network policy support), Flannel (simpler overlay networking), Cilium (based on eBPF with enhanced security and visibility), and Weave Net. CNI ensures Kubernetes can run in any network environment—from on-premises data centers to cloud platforms—while maintaining consistent Pod-to-Pod communication and enforcing network policies.
- Container Storage Interface (CSI): The Container Storage Interface (CSI) standardizes how Kubernetes interacts with storage systems to provision, attach, and mount volumes for Pods. Instead of building custom logic for each storage backend, Kubernetes relies on CSI drivers that know how to communicate with specific storage platforms. When a user defines a PersistentVolumeClaim (PVC), Kubernetes uses the CSI driver to dynamically provision storage, or bind to an existing volume, then mount it to the target node and Pod. This allows Kubernetes to support a wide range of storage backends such as AWS EBS, Google Persistent Disk, Ceph, NFS, or iSCSI, whether they are block or file-based systems. CSI makes Kubernetes storage highly modular and extensible, simplifying the addition of new storage types without changing core Kubernetes code.

- containerd and CRI-O are both popular container runtimes used by Kubernetes to manage containers. containerd is a general-purpose runtime originally from Docker, now a CNCF project, and is widely used across cloud platforms. CRI-O, on the other hand, is a lightweight runtime built specifically for Kubernetes, focusing on simplicity and security. While containerd offers broader flexibility, CRI-O is tightly integrated with Kubernetes and often used in Red Hat-based systems like OpenShift.

### Kubernetes Code Examples

#### Helm

- Directory structure:
```yaml
myapp/
├── Chart.yaml
├── values.yaml
└── templates/
    ├── deployment.yaml
    ├── service.yaml
    ├── secret.yaml
    └── redis-deployment.yaml
```

- Chart.yaml:

```yaml
apiVersion: v2
name: myapp
description: A complex web app with optional Redis
version: 1.0.0
appVersion: "2.1.0"
```

- values.yaml:

```yaml
replicaCount: 3

image:
  repository: myregistry/myapp
  tag: "2.1.0"
  pullPolicy: IfNotPresent

service:
  type: ClusterIP
  port: 80

env:
  - name: ENVIRONMENT
    value: "production"
  - name: LOG_LEVEL
    value: "debug"

secretEnv:
  enabled: true
  values:
    DB_PASSWORD: "supersecure"

redis:
  enabled: true
  image: redis:6.2-alpine
```


- templates/deployment.yaml:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ include "myapp.fullname" . }}
  labels:
    app: {{ include "myapp.name" . }}
spec:
  replicas: {{ .Values.replicaCount }}
  selector:
    matchLabels:
      app: {{ include "myapp.name" . }}
  template:
    metadata:
      labels:
        app: {{ include "myapp.name" . }}
    spec:
      containers:
        - name: {{ .Chart.Name }}
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}
          ports:
            - containerPort: 80
          env:
            {{- range .Values.env }}
            - name: {{ .name }}
              value: {{ .value | quote }}
            {{- end }}
            {{- if .Values.secretEnv.enabled }}
            {{- range $key, $val := .Values.secretEnv.values }}
            - name: {{ $key }}
              valueFrom:
                secretKeyRef:
                  name: {{ include "myapp.fullname" $ }}
                  key: {{ $key }}
            {{- end }}
            {{- end }}
```

- templates/secret.yaml:

```yaml
{{- if .Values.secretEnv.enabled }}
apiVersion: v1
kind: Secret
metadata:
  name: {{ include "myapp.fullname" . }}
type: Opaque
data:
  {{- range $key, $val := .Values.secretEnv.values }}
  {{ $key }}: {{ $val | b64enc }}
  {{- end }}
{{- end }}
```

- templates/redis-deployment.yaml:

```yaml
{{- if .Values.redis.enabled }}
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ include "myapp.fullname" . }}-redis
spec:
  replicas: 1
  selector:
    matchLabels:
      app: redis
  template:
    metadata:
      labels:
        app: redis
    spec:
      containers:
        - name: redis
          image: {{ .Values.redis.image }}
          ports:
            - containerPort: 6379
{{- end }}
```

- templates/service.yaml: 

```yaml
apiVersion: v1
kind: Service
metadata:
  name: {{ include "myapp.fullname" . }}
spec:
  type: {{ .Values.service.type }}
  selector:
    app: {{ include "myapp.name" . }}
  ports:
    - port: {{ .Values.service.port }}
      targetPort: 80
```

- templates/_helpers.tpl:

```yaml
{{- define "myapp.name" -}}
{{ .Chart.Name }}
{{- end }}

{{- define "myapp.fullname" -}}
{{ printf "%s-%s" .Release.Name .Chart.Name }}
{{- end }}
```

Then: 

```sh
helm lint myapp/
helm install myapp ./myapp --dry-run --debug
```

General install command:

```sh
helm install myapp ./myapp
```
