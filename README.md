# Ollama-with-WebUI-Docker-Setup
A Docker Compose solution for running Ollama with Open WebUI, with support for both GPU and non-GPU environments.


# Ollama & Open-WebUI Docker Compose

This repository provides Docker Compose setups to run [Ollama](https://ollama.com/) alongside [Open-WebUI](https://github.com/open-webui/open-webui), with versions both with and without GPU support. Ollama offers a simple way to deploy and serve language models locally, while Open-WebUI provides an interactive web interface to interact with these models seamlessly.

## Components

- **[Ollama](https://ollama.com/)**: An easy-to-use tool for running local Large Language Models (LLMs).
- **[Open-WebUI](https://github.com/open-webui/open-webui)**: A web-based UI to interact with your Ollama-hosted language models.


## What is Ollama?
Ollama is an AI model inference engine that allows you to deploy and run AI models efficiently. For more details, visit the official website: [Ollama](https://ollama.ai/)

## What is WebUI?
WebUI provides a graphical user interface to interact with Ollama easily. For more information, check out its GitHub repository: [Open WebUI](https://github.com/open-webui/open-webui)



## Prerequisites

Before starting, ensure you have Docker and Docker Compose installed on your system:

- [Install Docker](https://docs.docker.com/get-docker/)
- [Install Docker Compose](https://docs.docker.com/compose/install/)


## 🚀 Quickstart Usage

### 🔹 Choosing your Docker Compose file


- `docker-compose.yml`: Runs Ollama and Open-WebUI **without GPU support**.
- `docker-compose.yml-gpu`: Runs Ollama and Open-WebUI **with GPU support**.

### Start the Containers

Depending on your Docker installation, you might use either of the following commands:

```bash
docker-compose up -d
```
or

```bash
docker compose up -d
```
#### _Note: Some versions of Docker require docker-compose up, while others use docker compose up._

- docker-compose (with a hyphen) is used in legacy Docker versions (before v2).
- docker compose (without a hyphen) is used in Docker versions 2.x and above.
- Run `docker --version` to check your version. If you're using Docker v2+, use docker compose.

#### Once running, Open-WebUI will be accessible at:

```bash
http://localhost:8080
```

### GPU Version Only: Verifying GPU Access
If you are running the GPU-supported version, follow these steps to ensure GPU access inside the container.

#### 1️⃣ Check GPU Usage in Docker
Run the following command to verify if your container has GPU access:

```bash
docker inspect *name_of_the_container* | grep -i "capabilities"
```
If you see:

![image](https://github.com/user-attachments/assets/4dfd2c90-187f-4535-8d19-a84bc0c31d13)

then your container has GPU access.

or 

#### 2️⃣ Check GPU Processes Running Inside Containers
To see if any processes are using the GPU, run:

```bash
docker exec -it *name_of_the_container* nvidia-smi
```
or

```bash
docker exec -it *name_of_the_container*  /bin/bash
nvidia-smi
```
If `nvidia-smi` runs successfully inside the container, then GPU access is enabled.

### Storage
The Docker Compose files create persistent volumes for both Ollama and Open WebUI:

- ollama: Stores models and Ollama configuration
- open-webui: Stores WebUI data and settings
