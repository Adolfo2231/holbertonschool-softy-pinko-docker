# Holberton School Softy Pinko Docker Project

This project demonstrates the implementation of a web application using Docker containers, focusing on containerization, orchestration, and scaling.

## Project Structure

### Task0: Create Your First Docker Image
- Creates a basic Docker image based on Ubuntu
- Updates and upgrades the system
- Outputs "Hello, World!" when run

### Task1: Docker Lifecycle
- Demonstrates the complete lifecycle of Docker images and containers
- Shows how to build, run, and manage Docker containers

### Task2: Front-end Container
- Implements a static website using Nginx
- Serves HTML, CSS, and JavaScript files

### Task3: Back-end Container
- Creates a Flask API container
- Implements basic API endpoints
- Connects with the front-end container

### Task4: Docker Compose
- Orchestrates multiple containers using Docker Compose
- Manages front-end and back-end services together

### Task5: Nginx as Proxy
- Implements Nginx as a reverse proxy
- Routes traffic between front-end and back-end services
- Exposes only port 80 to the outside world

### Task6: Horizontal Scaling
- Demonstrates horizontal scaling of the back-end service
- Implements load balancing using Nginx
- Shows how to scale services using Docker Compose

## Requirements

- Docker
- Docker Compose
- Git

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/holbertonschool-softy-pinko-docker.git
```

2. Navigate to the project directory:
```bash
cd holbertonschool-softy-pinko-docker
```

## Usage

Each task can be run independently. Navigate to the specific task directory and follow the instructions in its README.

### Example (Task0):
```bash
cd task0
docker build -f ./Dockerfile -t softy-pinko:task0 .
docker run -it --rm --name softy-pinko-task0 softy-pinko:task0
```

## Author

[Adolfo Rodriguez]

## License

This project is part of the Holberton School curriculum and is open source. 