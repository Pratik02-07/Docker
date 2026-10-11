# Docker Basics 

## What is Docker?

**Docker** is a platform that packages an application and the things it
needs into a unit called a **container**. Containers help an application
run more consistently across a developer's laptop, a test environment,
and a server.

Think of a container as a small, isolated environment for running an
application.

## Docker architecture: CLI, Engine, and Daemon

![Docker architecture: CLI sends requests to the Docker Daemon through
the Docker API, and the daemon manages containers and other Docker
objects.](docs/images/docker-architecture.png)

### 1. Docker CLI --- where you type commands

**CLI** means *Command-Line Interface*. It is the `docker` command you
run in a terminal.

Examples:

``` bash
docker --version
docker images
docker ps
docker run nginx
```

The CLI sends your request to the Docker API. It does not usually create
or start containers by itself.

### 2. Docker Daemon --- the background worker

The Docker Daemon is the background service named **`dockerd`**. It
listens for Docker API requests and performs work such as:

-   Downloading images when they are not available locally.
-   Creating, starting, stopping, and removing containers.
-   Managing Docker networks and volumes.
-   Building and managing images.

### 3. Docker Engine --- the overall Docker system

**Docker Engine** is the software used to build and run containers. It
includes the Docker Daemon, the Docker API, and the Docker CLI (which
you commonly use to send commands to it).

> **Easy way to remember:** CLI = send the command; Daemon = performs
> the work; Engine = the overall container platform.

## How a Docker command works

For example, when you run:

``` bash
docker run nginx
```

1.  You enter the command using the Docker CLI.
2.  The CLI sends a request through the Docker API.
3.  The Docker Daemon checks whether the `nginx` image is available
    locally. If needed, it downloads it from a registry.
4.  The daemon creates and starts a container from that image.
5.  Nginx runs inside the container.

To run Nginx in the background and publish it on port 8080 of your
computer, use:

``` bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Then open `http://localhost:8080` in your browser.

## Important Docker terms

| Term | Simple explanation | Example |
| :--- | :--- | :--- |
| **Image** | A read-only template used to create containers | `nginx:latest` |
| **Container** | A running or stopped instance created from an image | `my-nginx` |
| **Dockerfile** | Instructions for building your own image | `Dockerfile` |
| **Registry** | A place to store and download images | Docker Hub |
| **Volume** | Storage that can keep data even when a container is removed | Database files |
| **Network** | Lets containers communicate with each other and other systems | App-to-database connection |
| **Port mapping** | Connects a host port to a container port | `-p 8080:80` |

## Common commands

### Check Docker

``` bash
docker --version
docker info
docker version
```

### Work with images

``` bash
docker pull nginx       # Download an image
docker images           # List local images
docker build -t my-app . # Build an image from the Dockerfile in this folder
```

### Work with containers

``` bash
docker run nginx        # Create and start a container
docker ps               # List running containers
docker ps -a            # List all containers, including stopped ones
docker logs my-nginx    # View container logs
docker stop my-nginx    # Stop a container
docker start my-nginx   # Start a stopped container
docker rm my-nginx      # Remove a stopped container
```

### Clean up carefully

``` bash
docker image prune      # Remove dangling images
docker container prune  # Remove stopped containers
```

Cleanup commands delete resources. Check what you are removing before
running them.

## Image vs. container

A simple comparison:

-   **Image = recipe/template.** It contains the application and its
    packaged dependencies.
-   **Container = running instance.** Docker creates a container from an
    image.

One image can be used to create multiple containers.

## Docker and virtual machines

Docker containers usually share the host operating system's kernel, so
they are generally lighter and faster to start than virtual machines. A
virtual machine runs its own guest operating system on virtualized
hardware. Containers still provide isolation, but their isolation model
differs from that of virtual machines.

## Suggested learning path

1.  Install Docker Desktop (Windows/macOS) or Docker Engine (Linux).
2.  Learn `docker pull`, `docker images`, and `docker run`.
3.  Inspect containers with `docker ps`, `docker logs`, and
    `docker inspect`.
4.  Build a small image with a `Dockerfile`.
5.  Learn port mapping, volumes, and networks.
6.  Try Docker Compose to run a multi-container application.

## Docker visual guide

The infographic below gives you a quick overview of Docker concepts in
one place.

![Docker visual guide covering Docker basics, architecture, workflow,
images versus containers, lifecycle, common commands, volumes, networks,
registries, and summary.](docs/images/docker-complete-overview.png)


## Official resources

-   [Docker documentation](https://docs.docker.com/)
-   [Docker Get Started guide](https://docs.docker.com/get-started/)
-   [Docker Hub](https://hub.docker.com/)

------------------------------------------------------------------------

