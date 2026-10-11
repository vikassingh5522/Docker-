1. What is Docker? — Docker is a platform used to build, package, and run applications inside containers.
2. Why do we need Docker? — Docker ensures applications run consistently across different environments.
3. Problems before Docker: environment differences — Applications could fail because development, testing, and production environments had different dependencies or configurations.
4. Virtual machine vs Docker container — A virtual machine runs its own operating system, while a container shares the host kernel.
5. Docker vs virtual machines — Docker containers are generally lightweight and start faster than virtual machines.
6. Advantages and disadvantages of Docker — Docker offers portability, consistency, and efficient resource usage, but introduces complexity in networking, storage, and security.
7. Docker architecture — Docker architecture consists of the Docker client, Docker daemon, APIs, images, containers, and registries.
8. Docker Engine — Docker Engine is the core technology that builds and runs containers.
9. Docker Client / Docker CLI — Docker CLI accepts commands such as `docker run` and sends requests to the Docker daemon.
10. Docker Daemon (`dockerd`) — The Docker daemon manages Docker images, containers, networks, and volumes.
11. Docker Desktop — Docker Desktop is a desktop application that provides Docker tools and a container environment on Windows and macOS.
12. Linux kernel and namespaces — The Linux kernel manages system resources, while namespaces isolate container processes and resources.
13. Control groups (cgroups) — Cgroups control and monitor container resource usage, such as CPU and memory.
14. Hypervisor vs container runtime — A hypervisor manages virtual machines, while a container runtime manages containers.
15. Container runtime: `containerd` and `runc` — `containerd` manages container lifecycles, while `runc` creates and runs containers using OCI standards.
16. Docker workflow: code → image → container — Write application code, package it into an image using a Dockerfile, and run that image as a container.





# Docker Roadmap — Beginner to Advanced

Here is a complete Docker learning roadmap designed for you to learn Docker step by step, practise commands in your VS Code terminal, and eventually deploy projects like your MeetSummarizer-AI application to AWS EC2.

Follow the topics in order. Don't try to learn everything in one day. First understand how Docker works, then build images and containers, then move to Docker Compose, networking, security, CI/CD, and deployment.

## Docker learning journey

Level 1 — Fundamentals

Understand Docker and why it is used.

Level 2 — Commands and Images

Run containers and create Docker images.

Level 3 — Dockerfile and Compose

Containerize frontend and backend applications.

Level 4 — Networking and Storage

Connect containers and persist data.

Level 5 — Production Docker

Security, optimization, debugging and monitoring.

Level 6 — DevOps and AWS

CI/CD, registries, EC2 and deployment.

## Level 1: Docker fundamentals

Goal: Understand what Docker is and how it works.

Fundamentals checklist

0/16

What is Docker?

Why do we need Docker?

Problems before Docker: environment differences

Virtual machine vs Docker container

Docker vs virtual machines

Advantages and disadvantages of Docker

Docker architecture

Docker Engine

Docker Client / Docker CLI

Docker Daemon (dockerd)

Docker Desktop

Linux kernel and namespaces

Control groups (cgroups)

Hypervisor vs container runtime

Container runtime: containerd and runc

Docker workflow: code → image → container

## Level 2: Docker installation and basic commands

Goal: Use Docker in your Windows and VS Code environment.

- Install Docker Desktop on Windows.
- Enable the WSL 2 backend.
- Understand Linux containers on Windows.
- Install Docker extensions in VS Code.
- Verify Docker installation: `docker --version`
- Check the Docker Engine: `docker info`
- Check running containers: `docker ps`
- Check all containers: `docker ps -a`
- Download an image: `docker pull nginx`
- List images: `docker images`
- Run a container: `docker run nginx`
- Run in detached mode: `docker run -d nginx`
- Assign a name: `docker run --name my-nginx nginx`
- Map ports: `docker run -p 8080:80 nginx`
- Stop a container: `docker stop my-nginx`
- Start a container: `docker start my-nginx`
- Restart a container: `docker restart my-nginx`
- Remove a container: `docker rm my-nginx`
- Remove an image: `docker rmi nginx`
- View logs: `docker logs my-nginx`
- Follow logs: `docker logs -f my-nginx`
- Open a shell inside a container: `docker exec -it my-nginx sh`
- Inspect configuration: `docker inspect my-nginx`
- View container resource usage: `docker stats`
- See filesystem changes: `docker diff my-nginx`

Practice: Run Nginx and open `http://localhost:8080`.

## Level 3: Docker images and registries

Goal: Understand how images are created, stored and shared.

- What is a Docker image?
- What is a Docker container?
- Image vs container
- Image layers and writable container layers
- Image tags: `nginx:alpine`, `node:22-alpine`
- Image IDs and digests
- Image caching
- Docker Hub
- Public vs private repositories
- Pulling and pushing images
- Docker login and logout
- Container registries: Docker Hub, Amazon ECR, GitHub Container Registry
- Image naming conventions
- Image versioning and tagging
- Build and export image information
- Multi-platform images: AMD64 vs ARM64
- Cleaning unused images and build cache

Important commands:

```
docker pull nginx:alpine
docker images
docker image inspect nginx:alpine
docker tag my-app:latest username/my-app:v1
docker login
docker push username/my-app:v1
docker image prune
docker builder prune
```

Learn how `docker image prune` differs from `docker system prune` before cleaning anything.

## Level 4: Dockerfile — the most important topic

Goal: Create your own Docker images for real applications.

Learn these Dockerfile instructions in order:

| Instruction     | Purpose                               |
| --------------- | ------------------------------------- |
| `FROM`          | Selects the base image                |
| `WORKDIR`       | Sets the working directory            |
| `COPY`          | Copies files into the image           |
| `ADD`           | Copies files with additional features |
| `RUN`           | Executes commands while building      |
| `ENV`           | Defines environment variables         |
| `ARG`           | Defines build-time variables          |
| `EXPOSE`        | Documents the intended container port |
| `CMD`           | Defines the default command           |
| `ENTRYPOINT`    | Defines the main executable           |
| `USER`          | Selects the runtime user              |
| `VOLUME`        | Declares a mount point                |
| `HEALTHCHECK`   | Defines a health check                |
| `.dockerignore` | Excludes files from the build context |

Advanced Dockerfile concepts:

- Build context and build cache
- Layer optimization
- Multi-stage builds
- Production vs development Dockerfiles
- Non-root containers
- Dependency installation and lockfiles
- Node.js, Python and Java Dockerfiles
- Build arguments vs environment variables
- Image size optimization
- Reproducible builds
- Pinning image versions
- Distroless and minimal base images

Practice: Build your backend and frontend images.

```
docker build -t meetsummarizer-backend ./Backend
docker build -t meetsummarizer-frontend ./Frontend
docker images
```

These commands assume each directory contains a file named `Dockerfile`. If your files are named `dockerfile` in lowercase, add `-f Backend/dockerfile` or `-f Frontend/dockerfile` and use the repository root as the build context.

## Level 5: Ports, networking and communication

Goal: Connect frontend, backend, Nginx and databases.

- What is a Docker network?
- Bridge network
- Host network
- None network
- User-defined bridge network
- Network isolation
- Container-to-container communication
- Service discovery and DNS
- Container IP vs host IP
- Port mapping: `-p 8080:80`
- `EXPOSE` vs `ports` vs `expose`
- Docker Compose default network
- Network aliases
- Inspecting and removing networks
- Reverse proxies
- Nginx configuration
- HTTP vs HTTPS
- WebSockets and reverse-proxy timeouts
- Troubleshooting connection refused and DNS errors

Useful commands:

```
docker network ls
docker network inspect meetsummarizer-ai_default
docker network create my-network
docker network connect my-network my-container
docker network rm my-network
```

Practice: Route browser traffic through Nginx to the frontend and backend. Your current MeetSummarizer-AI project is a good example.

## Level 6: Docker volumes and persistent storage

Goal: Preserve data when containers are removed or recreated.

- Container filesystem
- Ephemeral container data
- Volumes vs bind mounts
- Named volumes
- Anonymous volumes
- Read-only mounts (`:ro`)
- Persistent database storage
- Volume permissions and ownership
- Volume backup and restore
- Volume inspection and cleanup
- Mounting configuration files
- Volume initialization and seed data
- What happens when a volume is deleted?

Commands:

```
docker volume ls
docker volume inspect backend-data
docker volume create my-volume
docker volume rm my-volume
docker compose down
```

Remember: `docker compose down` normally preserves named volumes. Do not use `docker compose down -v` unless you intend to delete the Compose project's volumes and their stored data.

## Level 7: Docker Compose

Goal: Run a complete multi-container application using one configuration file.

- What is Docker Compose?
- Compose YAML structure
- `services`, `networks` and `volumes`
- `build` and `image`
- `ports` vs `expose`
- `environment` vs `env_file`
- `depends_on`
- Health checks and readiness
- `restart` policies
- Service names and DNS
- Environment-specific Compose files
- Development and production overrides
- Scaling services
- Compose profiles
- Secrets and configuration
- Build and start services
- View logs and container status
- Rebuild after changing source code
- Stop and remove containers
- Troubleshooting YAML indentation

Main commands:

```
docker compose config
docker compose build
docker compose up -d
docker compose ps
docker compose logs -f
docker compose restart
docker compose stop
docker compose start
docker compose down
```

For your project, understand this flow:

`docker-compose.yml`

Build backend and frontend images

Start backend + frontend + Nginx containers

Open `http://localhost`

## Level 8: Environment variables and secrets

- `.env` files
- Environment variables in Compose
- Build-time vs runtime configuration
- `.env` vs `env_file`
- Frontend build-time variables
- Backend runtime variables
- API keys and database credentials
- Why secrets should not be hardcoded into Dockerfiles
- Why `.env` files should not be committed to Git
- Docker secrets and external secret managers
- AWS Secrets Manager and Systems Manager Parameter Store
- Environment variable debugging

Important: Vite-based frontend variables are typically embedded during the frontend build. Do not assume that changing the container's runtime environment automatically changes an already-built frontend.

## Level 9: Docker security

- Run as a non-root user
- Minimize the image attack surface
- Use trusted base images
- Keep base images and dependencies updated
- Avoid embedding secrets in images
- Docker socket security
- Linux capabilities
- Read-only root filesystems
- Container privilege and isolation
- Resource limits
- Image vulnerability scanning
- Software supply-chain security
- Image signing and provenance
- Least-privilege access
- Network isolation
- Secure registry access

## Level 10: Debugging and troubleshooting

Learn how to diagnose common issues rather than only memorizing commands.

- Container exits immediately
- Port already in use
- Image build fails
- `npm ci` fails
- Missing files during `COPY`
- Incorrect working directory
- Application listens on the wrong port
- Application binds only to `localhost`
- Nginx returns `502 Bad Gateway`
- Nginx returns `404 Not Found`
- Frontend loads but API requests fail
- DNS resolution errors
- Missing environment variables
- Container permission errors
- Volume hides files from the image
- Health checks fail
- Out-of-memory errors
- Inspecting logs, exit codes and container state

Useful commands:

```
docker compose ps -a
docker compose logs --tail=100
docker inspect <container-name>
docker exec -it <container-name> sh
docker stats
docker events
```

## Level 11: Production optimization and monitoring

- Multi-stage builds
- Small production images
- BuildKit and build cache
- CPU and memory limits
- Health checks
- Graceful shutdown
- Restart policies
- Log rotation and log drivers
- Metrics and monitoring
- Container resource monitoring
- Vulnerability scanning
- Image lifecycle management
- Zero-downtime deployment concepts
- Backup and recovery
- Container orchestration fundamentals

Tools worth knowing: Docker Scout, Trivy, Prometheus, Grafana and centralized logging systems.

## Level 12: Git, CI/CD and Docker

Goal: Automatically build and deploy images when you push code.

- Git basics: commit, push, pull and branches
- CI/CD pipeline fundamentals
- GitHub Actions
- Automated tests
- Docker image builds in CI
- Image tagging with commit hashes
- Push images to a registry
- Deploy images to a server
- Environment separation: development, staging, production
- Secure CI/CD credentials
- Rollback strategies
- Deployment verification
- Build caching in CI
- Automated image scanning

Typical workflow:

1\. Developer pushes code to GitHub

2\. CI pipeline runs tests

3\. Docker images are built

4\. Images are pushed to a registry

5\. EC2 pulls the new images

6\. Docker Compose starts the application

7\. Health checks verify the deployment

## Level 13: Docker deployment on AWS

- What is AWS EC2?
- Linux commands and SSH
- Security groups and firewall rules
- Installing Docker on EC2
- Deploying with Docker Compose
- Docker Hub vs Amazon ECR
- Pulling images onto EC2
- Running frontend, backend and Nginx
- Connecting to Amazon RDS
- Environment variables on production servers
- HTTPS with a domain and TLS certificate
- Reverse proxy configuration
- AWS IAM roles and permissions
- AWS Secrets Manager
- CloudWatch logs and monitoring
- Persistent storage and backups
- Deployment updates and rollbacks
- CI/CD from GitHub to EC2
- Troubleshooting production deployments

Practical goal: Deploy MeetSummarizer-AI so that users can access it through a public URL, the frontend can call the backend, and your data persists safely.

## Level 14: Advanced Docker and orchestration

Study these after you are comfortable with Docker Compose and production deployment.

- Docker Engine API
- containerd and OCI standards
- BuildKit internals
- Multi-platform builds
- Container security profiles
- Advanced networking
- Docker Swarm concepts
- Kubernetes architecture
- Pods, Deployments and Services
- ConfigMaps and Secrets
- Ingress and load balancing
- Helm charts
- Container orchestration and scaling

You do not need to learn Kubernetes before you can use Docker effectively. Master images, containers, Compose, networking, volumes and deployment first.

## Your practical project roadmap

Use these projects to test your knowledge.

[How to Run AdventureWorks Using Azure Data Studio on Mac | by Lauren Esser | Analytics Vidhya | Medium](https://images.openai.com/static-rsc-4/vdyWZ9geXCJOurX3qh8RnLe1rs123SZ3IGVagXZ69Xvcyve1zHZ_VDCSzCptrZjbz-b5-fqIyAWv1kjdPzy3Nxf9ua6wX1XG9QLk69Y7HHnI-jSpal0tfvOjXI0Kup1TSP1ErByE22J-Ju_AaPO5mVm4V0y0HcvYP4t9lMLluXE?purpose=inline)

Project 1 — Run Nginx

Beginner

Download an image, start a container, map port `8080:80`, open the page, view logs and stop the container.

[Node.JS : API’s. Construindo e Consumindo uma API com… | by Hugo Habbema | Medium](https://images.openai.com/static-rsc-4/A4L0tA-gEW8J1GU025A0Bv_lXC3cCV44hy8r2osdLNYOfSStf-9ICyxTzjHjxkjIzGsDinXiG6bkJqPgORNrOodyzRD9dfhM2xf2PI14I2puDup4fyFf2MMJl8Tfc7Ooddb85kQiQTRDnk_wi5X-6S49EyRN4OdDgwGhUM_ZIhQ?purpose=inline)

Project 2 — Containerize a Node.js backend

Beginner

Write a Dockerfile, install dependencies, configure the port and test an API endpoint.

[GitHub - ahlam-laouadi/Dashboard_ReactJS: Admin dashboard build with ReactJs and Sass preprocessor with dark and light mode.](https://images.openai.com/static-rsc-4/gCzGjIZtJesZLiaX64zHTYmCzeRynCsWMUX5CCTEE2Vc3XAy6GCyL2VAal0OCoG-DeYlYVDXWThWOBrtZR7kHpQiKTMg-fGrbErWDiA7_94gNaYM5wBr7KUteBQxKgRxXeJFcIRZ8TbujOeJV9epzR0jQtJvIDUUGYqIuK8P3Y8?purpose=inline)

Project 3 — Containerize a frontend

Intermediate

Build a production frontend image and serve its static files.

[Docker for local web development, part 5: HTTPS all the things — osteel's blog](https://images.openai.com/static-rsc-4/4H8KBwTmmHST6XFOK-PFBH_hcPW7Tdz6AGO2MXCKdaDNCyTSW-YG6sKS8OcBUirXcv0ww0tF2aBgBzJtYYQ3RJkVxKCqelhSkH1kiQ8pxU6eDC0mK4pworlxIp32ETPOubMOMapZe1ndpqVCKNMVhk-i8gWP4EaEBTBwuSPNJnc?purpose=inline)

Project 4 — MeetSummarizer-AI

Intermediate

Run backend, frontend and Nginx using Docker Compose. Verify routing, environment variables, logs and data persistence.

[Next.js on AWS: Deployment Strategies - DEV Community](https://images.openai.com/static-rsc-4/ENHttcL1XvvZEVG4Q_7tygBSzI-xuHnxEvM2UNC7fyxDbOBoWO_9E00Xjvg3VJ1oJA_ycrFRtC1Zd55Zhoq_05lHXjWL-M-RM0LvCdbgpiknlJxGudSXEH82OjWBjQo-cWP7fd_rrADCnRxj7Vn99ghm7h-CIwU2gM2QIuTUxfY?purpose=inline)

Project 5 — AWS deployment

Advanced

Push images to a registry, pull them onto EC2, configure security and deploy with a repeatable process.

## Suggested 30-day study plan

| Days  | Topics                                        |
| ----- | --------------------------------------------- |
| 1–3   | Docker fundamentals and architecture          |
| 4–6   | Installation and commands                     |
| 7–9   | Images, registries and tags                   |
| 10–13 | Dockerfile and multi-stage builds             |
| 14–16 | Networking and port mapping                   |
| 17–18 | Volumes and persistent data                   |
| 19–21 | Docker Compose                                |
| 22–24 | Environment variables, security and debugging |
| 25–26 | Optimization and monitoring                   |
| 27–28 | GitHub Actions and CI/CD                      |
| 29–30 | AWS EC2 deployment and revision               |

This is a suggested schedule, not a requirement to finish every topic within 30 days.

## Start here

Since you have already built the backend and frontend images and started Nginx in MeetSummarizer-AI, you have begun working with several intermediate concepts.

Your next step should be to understand these five topics deeply:

1. Docker architecture — client, daemon and engine.
2. Dockerfile — how your images are built.
3. Image vs container — what gets created at each step.
4. Docker Compose — how all three services run together.
5. Networking and Nginx — how `localhost:80` reaches the frontend and backend.

Once these are clear, debugging and deploying the application will become much easier.
