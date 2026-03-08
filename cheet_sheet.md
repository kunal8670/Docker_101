# 🐳 Docker Command Cheat Sheet

A practical command reference covering Docker concepts learned from **Phase 1 → Phase 7** including:

- Docker installation
- Images and containers
- Trusted images
- Building custom images
- Managing Docker resources
- Docker networking

This document is designed as a **quick lookup reference while learning and working with Docker**.

---

## 📚 Structure

The commands are organized **phase-wise** based on the learning roadmap.

[Roadmap.md](Learn_docker_From_hire_roadmap.md)

| Phase | Command | Purpose |
|------|--------|--------|
| Phase 2 | `docker --version` | Verify Docker installation |
| Phase 2 | `docker run hello-world` | Test Docker installation by running a sample container |
| Phase 3 | `docker pull nginx` | Download nginx image from Docker Hub |
| Phase 3 | `docker images` | List all images stored locally |
| Phase 3 | `docker run -d -t --name cant_contain_myself centos` | Create and run a container from the CentOS image |
| Phase 3 | `docker ps` | Show currently running containers |
| Phase 3 | `docker ps -a` | Show all containers including stopped ones |
| Phase 3 | `docker exec -it cant_contain_myself bash` | Open an interactive shell inside a running container |
| Phase 3 | `docker stop cant_contain_myself` | Stop a running container |
| Phase 3 | `docker start cant_contain_myself` | Start a stopped container |
| Phase 3 | `docker rm cant_contain_myself` | Remove a container |
| Phase 4 | `docker search nginx` | Search Docker Hub for available images |
| Phase 4 | `docker pull alpine` | Download minimal Alpine Linux image |
| Phase 4 | `docker run -it alpine sh` | Start interactive Alpine container |
| Phase 5 | `mkdir docker-python-test` | Create project directory for Docker build |
| Phase 5 | `docker build -t python_test_image .` | Build a Docker image from a Dockerfile |
| Phase 5 | `docker run python_test_image` | Run container from custom image |
| Phase 5 | `docker run -it python_test_image bash` | Start interactive container from custom image |
| Phase 6 | `docker build -t mywebapp:v1 .` | Build image with version tag |
| Phase 6 | `docker build -t mywebapp:v2 .` | Build updated version of image |
| Phase 6 | `docker tag mywebapp:v1 mywebapp:stable` | Create additional tag for an image |
| Phase 6 | `docker inspect mywebapp:v1` | View detailed metadata of an image |
| Phase 6 | `docker run -d --name web_container nginx` | Run container in background with assigned name |
| Phase 7 | `docker network ls` | List all Docker networks |
| Phase 7 | `docker network inspect bridge` | Inspect configuration of the default bridge network |
| Phase 7 | `docker run -d -p 8080:80 --name nginx_web nginx` | Run container with port mapping using bridge network |
| Phase 7 | `docker run --network host nginx` | Run container using host network mode |
| Phase 7 | `docker run --network none ubuntu` | Run container with networking disabled |
| Phase 7 | `docker network create my_network` | Create a custom Docker network |
| Phase 7 | `docker run -dit --network my_network --name web ubuntu` | Run container connected to a custom network |
| Phase 7 | `docker run -dit --network my_network --name db ubuntu` | Run another container on the same network |
| Phase 7 | `docker network inspect my_network` | View configuration of a custom network |
| Phase 7 | `docker network rm my_network` | Remove a custom Docker network |

---



# 👨‍💻 Author

**Kunal H Patil**

📧 Email  
kkunalhpatil.8670@gmail.com

🔗 LinkedIn  
https://www.linkedin.com/in/kunal-patil-8733b528a/

💻 GitHub  
https://github.com/kunal8670

---

# 📚 Learning Notes Series

This cheat sheet is part of my **personal technical learning notes**.  
More notes will be added as I continue learning.

### Upcoming Notes

- 🐍 Python (for Beginners)
- 🧰 Git & GitHub
- 🌐 Full Stack Development

---

## 📌 About This Document

This Docker cheat sheet covers commands learned from **Phase 1 → Phase 7**, including:

- Docker installation
- Images & containers
- Trusted images
- Building custom images
- Managing Docker resources
- Docker networking

The goal of this document is to serve as a **quick reference while practicing Docker and containerized environments**.

---##### © 2026 Kunal Harshad Patil  
For more learning resources and updates, connect with me:  
[GitHub](https://github.com/kunal8670) • [LinkedIn](https://www.linkedin.com/in/kunal-patil-8733b528a/)

---

