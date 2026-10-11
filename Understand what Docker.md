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
