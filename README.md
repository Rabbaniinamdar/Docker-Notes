# Docker-Notes


# 🐳 Containers vs Virtual Machines (VMs)



## 🔹 What Are Containers?

Containers are **lightweight, portable, and self-contained executable images** that package applications along with their dependencies (libraries, binaries, config files) needed to run them. They share the host operating system’s kernel and provide a **consistent environment** across development, testing, and production.

### 🧰 Key Features:
- Share host OS kernel.
- Faster startup (milliseconds).
- Small footprint (MBs).
- Run isolated processes.
- Easy to deploy, scale, and manage.
- Orchestrated using tools like **Docker** and **Kubernetes**.

### ✅ Benefits:
- Efficient use of system resources.
- Ideal for **microservices** and **CI/CD pipelines**.
- High **portability** across platforms.
- Easier to test, build, and deploy.

---

## 🔹 What Are Virtual Machines (VMs)?

A **virtual machine** is a software emulation of a complete physical machine that includes a full guest operating system. VMs are managed by a **hypervisor** (like VMware, VirtualBox, Hyper-V) which abstracts and allocates the host machine’s hardware resources (CPU, memory, storage).

### 🧰 Key Features:
- Each VM runs its own OS (Linux, Windows, etc.).
- Provides strong isolation and security.
- More resource-intensive.
- Slower to start (minutes).
- Useful for running legacy or multiple OS environments.

### ✅ Benefits:
- Better **security and isolation**.
- Useful for running **different OSes** on the same hardware.
- Good for **legacy apps**, full-system emulation, and **disaster recovery**.

---

## 🔄 Key Differences Between Containers and VMs:

| Feature                 | **Containers**                                      | **Virtual Machines**                                |
|------------------------|-----------------------------------------------------|-----------------------------------------------------|
| **OS Architecture**     | Share host OS kernel                                | Each has its own full OS                            |
| **Startup Time**        | Fast (milliseconds)                                 | Slow (minutes)                                      |
| **Size**                | Lightweight (MBs)                                   | Heavyweight (GBs)                                   |
| **Resource Usage**      | Low (efficient)                                     | High (each VM requires CPU, memory, storage)        |
| **Isolation**           | Process-level isolation                            | Full OS-level isolation                             |
| **Portability**         | High (can run anywhere with a container runtime)    | Lower (tied to specific hypervisors/platforms)      |
| **Security**            | Moderate                                            | Strong (due to complete OS separation)              |
| **Use Case**            | Microservices, cloud-native apps                    | Legacy apps, full OS support needed                 |
| **Management**          | Managed using Docker, Kubernetes                    | Managed using Hypervisors (VMware, VirtualBox)      |

---

## 🧠 Relationship Between Containers and VMs

- **Not mutually exclusive**: You can run containers inside VMs to combine the benefits of both (e.g., security of VMs with speed of containers).
- **Use containers for**: Fast, scalable, and portable apps.
- **Use VMs for**: Isolated, secure, and OS-specific environments.

---

## 🚀 Use Cases

### 📦 Containers
- **Web development**: Consistent environment across dev/stage/prod.
- **Microservices**: Independent, isolated deployment units.
- **CI/CD pipelines**: Automated build, test, deploy flows.
- **Cloud computing**: Easily scalable container orchestration.
- **Modern architecture**: Decompose monoliths into microservices.

### 💻 Virtual Machines
- **Testing environments**: Safely test software in isolated OSes.
- **Development**: Cross-platform development and testing.
- **Isolation and Security**: Prevent threats from spreading.
- **Cloud infrastructure**: Scalable and customizable virtual servers.
- **Disaster Recovery**: Easy to back up and restore full systems.

---

## 🧾 Summary

- Containers and VMs both offer **application isolation**, but differ in approach.
- Containers are more **lightweight, portable, and faster**, while VMs offer **stronger isolation and flexibility in OS choice**.
- The best choice depends on your application’s requirements regarding speed, security, OS dependency, and resource availability.

---

# 🐳 What is Docker?

**Docker** is an open-source platform that enables developers to **build, ship, and run applications** as lightweight, portable, and self-sufficient containers.

### 🔧 Key Functions of Docker:
- Automates **deployment** of applications inside containers.
- Manages **scaling** and **orchestration** (with tools like Docker Compose or Kubernetes).
- Provides a consistent environment across **development**, **testing**, and **production**.
- Supports efficient **versioning**, **isolation**, and **portability** of applications.

### 🧰 What Docker Includes:
- **Docker Engine**: Core runtime that runs and manages containers.
- **Docker CLI**: Command-line interface to interact with Docker.
- **Docker Images**: Read-only templates used to create containers.
- **Docker Containers**: Running instances of images.
- **Docker Hub**: Cloud-based registry for sharing images.
- **Dockerfile**: Script for defining how an image is built.

---

## 💡 Why Use Docker?
- **Lightweight**: Shares host OS kernel (no full OS per app).
- **Portable**: Runs on any system with Docker installed.
- **Fast**: Quick startup and shutdown.
- **Isolated**: Applications run independently in their own environments.
- **Efficient**: Saves system resources compared to traditional VMs.

---

# 📦 What is Software Containerization?

**Software containerization** is a form of **operating system-level virtualization** that allows you to run and deploy applications in isolated environments called **containers**.

### 🔍 Key Characteristics:
- Encapsulates the **application**, its **code**, and **dependencies** (binaries, libraries, etc.) in one package.
- Containers run on the **same OS kernel**, but in isolated user spaces.
- **Faster and more efficient** than traditional virtualization methods.

### 🏗 Where Containers Can Run:
- On **bare-metal physical servers**.
- Inside **virtual machines (VMs)**.
- In **cloud environments** (AWS, Azure, GCP).
- Across **various OS platforms** that support container runtimes.

---

## 🚀 Benefits of Containerization:
- Enables **microservices architecture** (breaking apps into small, independent services).
- Supports **DevOps and CI/CD pipelines**.
- Reduces **dependency issues** ("works on my machine" problem).
- Enhances **scalability** and **resilience**.


# 🏗️ Docker Architecture

Docker architecture follows a **client-server model**, where the **Docker Client** interacts with the **Docker Daemon (Server)** using **REST APIs** to build, run, and manage containers.

---

## 📌 Components of Docker Architecture

### 1. **Docker Client**
- The user-facing interface.
- Sends commands to the Docker Daemon using CLI or REST API.
- Commands include: `docker build`, `docker run`, `docker pull`, etc.

> ✅ Acts as a frontend to communicate with the Docker Server.

---

### 2. **Docker Remote API**
- A RESTful interface through which the Docker Client communicates with the Docker Daemon.
- Can be used over the network to control remote Docker hosts.

---

### 3. **Docker Host / Server**
- The system running the **Docker Daemon (`dockerd`)**.
- Manages Docker images, containers, volumes, and networks.
- Executes commands received via Docker CLI or API.

### 🔁 How It Works:
1. Docker Client sends a command to the Docker Daemon.
2. Daemon checks if the required image is available locally.
3. If not found, it pulls the image from the Docker Registry.
4. Docker Daemon creates a running **container** from the image.

---

### 4. **Docker Daemon**
- The **core engine** of Docker.
- Runs in the background on the Docker Host.
- Responsible for managing all container lifecycle operations.

---

### 5. **Docker CLI**
- Command Line Interface for Docker.
- Lets users issue instructions to the Docker Daemon.

---

## 🧱 Docker Objects Managed by Daemon

| Docker Object | Description |
|---------------|-------------|
| **Images**    | Templates used to create containers |
| **Containers**| Running instances of images |
| **Volumes**   | Persistent data storage for containers |
| **Networks**  | Allow communication between containers |

---

## 🐳 Containers and Images

- **Images**: Read-only, lightweight, and portable software packages.
  - Example: Image of App, Image of MySQL
- **Containers**: Runtime instances of images.
  - Example: Container 1 (App), Container 2 (App), MySQL Container

---

## 🌐 Docker Registry

- Used to **store and distribute Docker images**.
- **Docker Hub**: Default public registry.
- **Private Registries**: For custom enterprise-level needs.

---

## 🔄 End-to-End Flow of Docker Architecture

```
  +--------------------+
  |  Docker Client     |
  |  (CLI / REST API)  |
  +--------------------+
           |
           | 1. User sends instruction (e.g., run a container)
           V
  +--------------------+
  |  Docker Daemon     | <----------------------------+
  |  (On Docker Host)  |                              |
  +--------------------+                              |
           |                                           |
           | 2. Daemon checks image locally           |
           | 3. If not found, pulls from Registry      |
           V                                           |
  +--------------------+                              |
  |  Docker Registry   |  <--- Docker Hub / Private ---+
  +--------------------+
           |
           | 4. Daemon creates a container from image
           V
  +-----------------------------+
  | Containers Running on Host |
  | - App Container 1          |
  | - App Container 2          |
  | - MySQL Container          |
  +-----------------------------+
```

---

## 📝 Summary Table

| Component           | Role |
|---------------------|------|
| **Docker Client**   | Sends commands via CLI or REST API |
| **Docker Remote API** | Allows client-server communication |
| **Docker Daemon**   | Builds, manages, and runs containers |
| **Docker Host**     | Machine running the Docker daemon |
| **Images**          | Blueprint for containers |
| **Containers**      | Executable instances of images |
| **Docker Registry** | Stores and distributes images (e.g., Docker Hub) |

Here is a **detailed and well-organized explanation of the 3 commonly used approaches to generate Docker images** from microservices — ideal for your notes:

---
### 📦 **Docker Images — Detailed Notes**

---

## 🔹 **What is a Docker Image?**
A **Docker image** is a **read-only template** used to create containers. It includes:
- The application code
- Runtime (e.g., Java, Python)
- System libraries & dependencies
- Configuration files

Images are **immutable**, **versioned**, and **portable** — like a snapshot of a filesystem with an application pre-installed.

---

## 🔹 **How Docker Images Work**
- Images are made up of **layers**.
- Each instruction in a `Dockerfile` (like `RUN`, `COPY`, etc.) creates a new **layer**.
- Layers are cached and reused across builds to save time and disk space.

**Example of layered image:**
```Dockerfile
FROM openjdk:17          # Base image
COPY target/app.jar /app.jar  # App layer
ENTRYPOINT ["java", "-jar", "/app.jar"] # Runtime
```

---

## 🔹 **Common Commands for Docker Images**

| Command | Description |
|--------|-------------|
| `docker images` | Lists all local Docker images |
| `docker build -t myapp:latest .` | Builds an image from a Dockerfile |
| `docker image inspect <image-id>` | Shows metadata about the image |
| `docker rmi <image-id>` | Removes a Docker image |
| `docker pull <image>` | Downloads an image from Docker Hub or registry |
| `docker push <image>` | Uploads an image to Docker Hub or registry |

---

## 🔹 **Image Tags**
Images are often tagged as:  
```bash
eazybytes/accounts:s4
```
Where:
- `eazybytes/accounts` is the repository name
- `s4` is the tag (e.g., version)

If no tag is specified, **`latest`** is used by default.

---

## 🔹 **Image Naming Best Practices**
- Use clear, versioned tags: `v1.0`, `dev`, `prod`, etc.
- Use your Docker Hub username or org as a prefix:  
  `yourname/project:tag`

---

## 🔹 **Dockerfile → Image → Container Flow**
1. Write a `Dockerfile`
2. Build the image: `docker build -t app:1.0 .`
3. Run a container from the image:  
   `docker run -p 8080:8080 app:1.0`

---

## 🔹 **Where are Images Stored?**
- Locally: `/var/lib/docker`
- Remotely: Docker Hub, AWS ECR, Google GCR, GitHub Container Registry, etc.

---

Would you like a **diagram** showing the Dockerfile → Image → Container flow or the **layered structure** of a Docker image?
# 🛠️ Generating Docker Images for Microservices

To containerize microservices, Docker images must be created. There are **three commonly used methods** for generating Docker images:

---

## **01. Using Dockerfile (Manual Approach)**
### 🔹 Example Service: `accounts`

A **Dockerfile** is a text document containing **step-by-step instructions** to build a Docker image. This is the most widely used and traditional approach.

### ✅ Key Features:
- Full control over image structure
- Requires knowledge of Docker commands and best practices
- Most flexible and customizable method

### 📄 Sample `Dockerfile` for a Spring Boot application:
```dockerfile
# Use a base image with Java installed
FROM openjdk:17-jdk-alpine

# Set working directory
WORKDIR /app

# Copy JAR file into container
COPY target/accounts.jar accounts.jar

# Command to run the app
ENTRYPOINT ["java", "-jar", "accounts.jar"]
```

### 📦 Build Command:
```bash
docker build -t accounts-service:latest .
```

---

## **02. Using Buildpacks (Cloud-Native Buildpacks)**
### 🔹 Example Service: `loans`

**Buildpacks** are a higher-level abstraction for container image creation, created by **Heroku** and **Pivotal**, now a **CNCF project**.

### ✅ Key Features:
- No need to write a Dockerfile
- Automatically detects language/runtime
- Useful for rapid development and consistent builds

### 🔧 Tools: [buildpacks.io](https://buildpacks.io), [Pack CLI](https://buildpacks.io/docs/tools/pack/)

### 📦 Build Command:
```bash
./mvnw spring-boot:build-image -Dspring-boot.build-image.imageName=<image-name>:<vesrion>
```

This will:
- Detect the app type (e.g., Java, Node.js)
- Download appropriate dependencies
- Package it into a Docker image

---

## **03. Using Google Jib**
### 🔹 Example Service: `cards`

**Jib** is an open-source Java tool maintained by **Google** that builds optimized Docker images for **Java applications** without a Docker daemon or Dockerfile.

### ✅ Key Features:
- Integrates directly into Maven or Gradle
- No Dockerfile or Docker installed needed
- Builds layered images optimized for caching

### 🔧 Integration with Maven:
```xml
<plugin>
  <groupId>com.google.cloud.tools</groupId>
  <artifactId>jib-maven-plugin</artifactId>
  <version>3.4.0</version>
</plugin>
```

### 📦 Build Command (Maven):
```bash
mvn compile jib:dockerBuild -Dimage=cards-service
```

---

## 📊 Summary Comparison Table

| Feature / Tool      | Dockerfile      | Buildpacks           | Google Jib              |
|---------------------|------------------|----------------------|--------------------------|
| Use Case Example     | `accounts`        | `loans`               | `cards`                  |
| Dockerfile Needed    | ✅ Yes             | ❌ No                 | ❌ No                    |
| Tool Type            | Manual build     | High-level builder   | Java-specific builder    |
| Language Support     | All               | Multiple              | Java only                |
| Control & Flexibility| High              | Medium                | Medium                   |
| Docker Required      | ✅ Yes             | ✅ Yes (via pack)     | ❌ No                    |
| Integration          | CLI               | Pack CLI              | Maven/Gradle             |



# 🔀 What is Port Mapping / Port Forwarding / Port Publishing?

By default, **Docker containers run in an isolated network** inside the Docker host. This means their internal ports are not directly accessible from your local machine or the internet.

**Port mapping** is a mechanism that **binds a port on the Docker host to a port inside the container**, enabling external access to services running inside the container.

---

## 🧱 Syntax of Port Mapping

```bash
docker run -p <host_port>:<container_port> <image>
```

- `host_port`: The port on your **local machine (or Docker host)** that you want to expose.
- `container_port`: The port inside the **Docker container** where the application is actually running.

---

## 📦 Example: Running `accounts-service`

```bash
docker run -p 8081:8080 accounts-service
```

- The **Spring Boot app** runs on port `8080` inside the container.
- Port `8081` on the **host** is mapped to port `8080` inside the **container**.
- You can now access the application via `http://localhost:8081`.

---

## 📊 Visual Explanation

```
        +-------------------+          Port 8081          +-------------------------+
        |    Local Machine  | -------------------------> |  Docker Host            |
        |  Browser / cURL   |                            |                         |
        +-------------------+                            |  +-------------------+  |
                                                         |  |  Docker Container |  |
                                                         |  |  Spring Boot App  |  |
                                                         |  |  LISTENING ON     |  |
                                                         |  |     PORT 8080     |  |
                                                         |  +-------------------+  |
                                                         +-------------------------+
```

---

## ✅ Key Points

- Port mapping enables external systems (e.g., browsers or APIs) to **communicate with containerized services**.
- You can map multiple containers to different external ports even if they all run on the same internal port.
- Useful in **local development**, **testing**, and **deployment scenarios**.


# 🧩 **Docker Compose: Managing Multiple Containers**

---

## ❓ Why Not Just Use the Docker CLI?

Running multiple containers (e.g., app, database, cache) using Docker CLI:

- Requires **multiple long and complex commands**
- Can lead to **errors and inconsistencies**
- Is **hard to maintain** and manage in version control
- Lacks **built-in orchestration** for dependencies and networking

👉 Therefore, **Docker Compose** is a better alternative when working with multi-container setups.

---

## 🚀 What is Docker Compose?

**Docker Compose** is a **Docker tool** that lets you define, run, and manage multi-container applications using a **single YAML configuration file (`docker-compose.yml`)**.

It lets you:
- Define each service (e.g., app, DB, message queue)
- Set up shared networks and volumes
- Specify environment variables, ports, dependencies, etc.

---

## ⚙️ Docker Compose File Example

A basic `docker-compose.yml` for a Spring Boot app and MySQL:

```yaml
version: '3.8'

services:
  app:
    image: accounts-service
    ports:
      - "8081:8080"
    depends_on:
      - db

  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: accountsdb
    ports:
      - "3307:3306"
```

---

## ✅ Advantages of Docker Compose

| Feature                     | Benefit                                                                 |
|-----------------------------|-------------------------------------------------------------------------|
| 📦 Centralized Config       | Manage all services in a **single `docker-compose.yml`** file           |
| 🚀 One Command Setup        | `docker-compose up` brings up all containers at once                    |
| 🔗 Built-in Networking      | Containers automatically **communicate by service name** (e.g., `db`)   |
| 📈 Easy Scaling             | Scale services with `--scale` flag                                      |
| 🔁 Lifecycle Management     | Commands like `start`, `stop`, `restart`, and `down` simplify workflows |
| 📂 Volume & Env Support     | Define **volumes**, **networks**, and **env variables** per service     |
| 📝 Version Controlled Infra | YAML file can be committed to Git for reproducibility                   |

---

## 🧪 Common Commands

```bash
# Start all services in the background
docker-compose up -d

# Stop all containers
docker-compose down

# View logs from all services
docker-compose logs

# Restart specific service
docker-compose restart app

# Scale a service (e.g., run 3 instances of 'app')
docker-compose up --scale app=3
```

## ✅ **Maven Commands**

| Command | Description |
|--------|-------------|
| `mvn clean install -Dmaven.test.skip=true` | Generates a JAR file in the `target` folder while skipping tests |
| `mvn spring-boot:run` | Runs the Spring Boot application directly |
| `mvn spring-boot:build-image` | Creates a Docker image using Buildpacks (no Dockerfile needed) |
| `mvn compile jib:dockerBuild` | Creates a Docker image using Google Jib (no Dockerfile needed) |

---

## 🐳 **Docker Commands**

### 🔨 **Image Management**

| Command | Description |
|---------|-------------|
| `docker build . -t eazybytes/accounts:s4` | Build Docker image from Dockerfile with a tag |
| `docker images` | List all Docker images |
| `docker image inspect <image-id>` | Show detailed info about an image |
| `docker image rm <image-id>` | Remove Docker image(s) |
| `docker image push docker.io/eazybytes/accounts:s4` | Push image to Docker registry |
| `docker image pull docker.io/eazybytes/accounts:s4` | Pull image from Docker registry |

---

### 🚀 **Container Lifecycle**

| Command | Description |
|---------|-------------|
| `docker run -p 8080:8080 eazybytes/accounts:s4` | Run container from image and map ports |
| `docker ps` | List running containers |
| `docker ps -a` | List all containers, including stopped ones |
| `docker container start <container-id>` | Start a stopped container |
| `docker container stop <container-id>` | Gracefully stop a running container |
| `docker container kill <container-id>` | Force stop a container |
| `docker container restart <container-id>` | Restart a container |
| `docker container rm <container-id>` | Remove container(s) |
| `docker container prune` | Remove **all** stopped containers |

---

### 📝 **Container Logs & Info**

| Command | Description |
|---------|-------------|
| `docker container inspect <container-id>` | View container details |
| `docker container logs <container-id>` | View logs from a container |
| `docker container logs -f <container-id>` | Follow live logs from a container |
| `docker container pause <container-id>` | Pause processes in a container |
| `docker container unpause <container-id>` | Resume paused container processes |

---

### 🧱 **Docker Compose**

| Command | Description |
|---------|-------------|
| `docker compose up` | Create and start services defined in docker-compose.yml |
| `docker compose down` | Stop and remove services |
| `docker compose start` | Start existing containers from the compose file |

---

### 💾 **Creating Specific Containers**

| Command | Description |
|---------|-------------|
| `docker run -p 3306:3306 --name accountsdb -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=accountsdb -d mysql` | Create MySQL container |
| `docker run -p 6379:6379 --name eazyredis -d redis` | Create Redis container |
| `docker run -p 8080:8080 -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin quay.io/keycloak/keycloak:22.0.3 start-dev` | Run Keycloak container |




