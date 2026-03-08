
# 🐳 Docker Learning Checklist

A structured learning checklist for mastering Docker step-by-step using trusted sources.

---

# 📚 Phase 1 — Understanding Docker

## 1. Understand What Docker Is

- [x] Learn the concept of **containerization**
- [x] Understand **how Docker differs from virtual machines**
- [x] Learn **why Docker is widely used in modern development**
- [x] Understand the **basic Docker architecture**

🔗 Resource  
- https://www.docker.com/blog/tag/what-is-docker-collection/

📝 Notes  
[Docker_Concept_nots](Docker_Consept.pdf)

# ⚙️ Phase 2 — Installing Docker

## 2. Install Docker Desktop

- [x] Download Docker Desktop
- [x] Install Docker Desktop
- [x] Verify installation using `docker --version`
- [x] Run your **first container**

🔗 Resource  
- https://docs.docker.com/desktop/

🧪 Practice

```bash
docker --version
docker run hello-world
````

📝 Notes
| Phase | Command | Purpose |
|------|--------|--------|
| Phase 2 | `docker --version` | Check Docker installation |
| Phase 2 | `docker run hello-world` | Test Docker installation |

---

# 🧠 Phase 3 — Docker Basics

## 3. Learn Docker Fundamentals

Topics to understand:

* [x] Docker Images
* [x] Docker Containers
* [x] Dockerfile basics
* [x] Basic Docker CLI commands
* [x] Pulling images from Docker Hub

🔗 Resource

* [https://www.docker.com/blog/docker-for-web-developers/](https://www.docker.com/blog/docker-for-web-developers/)

🧪 Practice

```bash
docker pull nginx
docker images
docker run nginx
docker ps
docker stop <container_id>
```

📝 Notes
| Phase | Command | Purpose |
|------|--------|--------|
| Phase 3 | `docker pull centos` | Download the CentOS image from Docker Hub |
| Phase 3 | `docker images` | List all images stored locally |
| Phase 3 | `docker run -d -t --name cant_contain_myself centos` | Create and run a container from the CentOS image |
| Phase 3 | `docker ps` | Show currently running containers |
| Phase 3 | `docker ps -a` | Show all containers (running + stopped) |
| Phase 3 | `docker exec -it cant_contain_myself bash` | Open terminal inside the running container |
| Phase 3 | `docker stop cant_contain_myself` | Stop the running container |
| Phase 3 | `docker start cant_contain_myself` | Start the stopped container again |
| Phase 3 | `docker rm cant_contain_myself` | Remove the container completely |
| Phase 3 | `docker stats` | Show real-time CPU, memory, and network usage of containers |
# 📦 Phase 4 — Using Trusted Images

## 4. Use Trusted Content from Docker Hub

Learn how to identify **secure base images**.

* [x] Docker Official Images
* [x] Docker Hardened Images
* [x] Verified Publisher images

🔗 Resource

* [https://docs.docker.com/docker-hub/image-library/trusted-content/](https://docs.docker.com/docker-hub/image-library/trusted-content/)

🧪 Practice

Search for trusted images:

* [https://hub.docker.com/](https://hub.docker.com/)

Example images:

```bash
docker pull ubuntu
docker pull nginx
docker pull python
```

📝 Notes
| Phase | Command | Purpose |
|------|--------|--------|
| Phase 4 | `docker search nginx` | Search images on Docker Hub |

---

# 🏗️ Phase 5 — Building Your Own Images

## 5. Build and Run Custom Images

Topics:

* [x] Writing Dockerfiles
* [x] Building images
* [x] Running custom containers
* [x] Understanding `ADD` vs `COPY`

🔗 Resource

* [https://www.docker.com/blog/docker-best-practices-understanding-the-differences-between-add-and-copy-instructions-in-dockerfiles/](https://www.docker.com/blog/docker-best-practices-understanding-the-differences-between-add-and-copy-instructions-in-dockerfiles/)

🧪 Example Dockerfile

```dockerfile
FROM python:3.10
WORKDIR /app
COPY . .
RUN pip install flask
CMD ["python", "app.py"]
```

Build image:

```bash
docker build -t myapp .
docker run myapp
```

📝 Notes
[Notes.pdf](phase_5_nots.md)
---

# 📦 Phase 6 — Managing Images and Containers

## 6. Manage Docker Resources

Topics:

* [x] Tagging images
* [x] Using labels
* [x] Organizing image versions
* [x] Managing container lifecycle

🔗 Resource

* [https://www.docker.com/blog/docker-best-practices-using-tags-and-labels-to-manage-docker-image-sprawl/](https://www.docker.com/blog/docker-best-practices-using-tags-and-labels-to-manage-docker-image-sprawl/)

🧪 Practice

```bash
docker tag myapp myapp:v1
docker images
docker ps -a
docker rm <container_id>
```

📝 Notes

[Notes.pdf](phase6_notes.md)

| Phase | Command | Purpose |
|------|--------|--------|
| Phase 6 | `docker build -t mywebapp:v1 .` | Build image with version tag |
| Phase 6 | `docker tag mywebapp:v1 mywebapp:stable` | Create new tag for image |
| Phase 6 | `docker inspect mywebapp:v1` | View image metadata and labels |
| Phase 6 | `docker run -d --name web_container nginx` | Create and start container |
| Phase 6 | `docker stop web_container` | Stop running container |
| Phase 6 | `docker start web_container` | Restart stopped container |
| Phase 6 | `docker rm web_container` | Remove container |

---

# 🌐 Phase 7 — Docker Network Management

Topics:

1. * [x] Docker networking fundamentals
   * [x] Default Docker networks (`bridge`, `host`, `none`)
   * [x] Bridge networking and port mapping
   * [x] Host network mode
---


2. * [x] None (isolated container) network mode
   * [x] Container-to-container communication
   * [x] Creating custom Docker networks
   * [x] Inspecting and managing Docker networks

🔗 Resources

* https://docs.docker.com/network/
* https://docs.docker.com/network/drivers/bridge/
* https://docs.docker.com/network/network-tutorial-standalone/
* https://docs.docker.com/network/drivers/host/
* https://docs.docker.com/network/drivers/none/

📝 Notes  
- [Notes_I.md](Phases_7_1_notes.md)
- [Notes_II.md](Phase_7_2_notes.md)


| Phase | Command | Purpose |
|------|--------|--------|
| Phase 7 | `docker network ls` | List all Docker networks available on the system |
| Phase 7 | `docker network inspect bridge` | Show detailed configuration of the default bridge network |
| Phase 7 | `docker run -d -p 8080:80 --name nginx_web nginx` | Run a container in bridge mode and expose container port 80 to host port 8080 |
| Phase 7 | `docker run --network host nginx` | Run a container using the host network stack |
| Phase 7 | `docker run --network none ubuntu` | Run a container with networking disabled (fully isolated) |
| Phase 7 | `docker network create my_network` | Create a custom Docker network |
| Phase 7 | `docker run -dit --network my_network --name web ubuntu` | Run a container connected to a custom network |
| Phase 7 | `docker run -dit --network my_network --name db ubuntu` | Run another container on the same custom network for communication |
| Phase 7 | `docker network inspect my_network` | View configuration and connected containers of a custom network |
| Phase 7 | `docker network rm my_network` | Remove a custom Docker network |

---

# Advanced Docker Topics:-(optional)

# 🔐 Phase 8 — Docker Security

## 8. Secure Docker Usage

Topics:

* [ ] Docker Hardened Images
* [ ] Vulnerability scanning
* [ ] Software supply chain security
* [ ] Using Docker Scout

🔗 Resources

* [https://www.docker.com/blog/building-trust-into-your-software-with-verified-components/](https://www.docker.com/blog/building-trust-into-your-software-with-verified-components/)
* [https://www.docker.com/products/docker-scout/](https://www.docker.com/products/docker-scout/)

📝 Notes
Security practices learned: `<write here>`

---

# 🚀 Phase 9 — Advanced Security and Management

Topics:

* [ ] Image access management
* [ ] Zero trust in container environments
* [ ] Secure software supply chains

🔗 Resources

* [https://docs.docker.com/security/image-access-management/](https://docs.docker.com/security/image-access-management/)
* [https://www.docker.com/blog/zero-trust-and-docker-desktop-an-introduction/](https://www.docker.com/blog/zero-trust-and-docker-desktop-an-introduction/)
* [https://www.docker.com/blog/software-supply-chain-art-of-continuous-improvement/](https://www.docker.com/blog/software-supply-chain-art-of-continuous-improvement/)

📝 Notes
Advanced concepts: `<write here>`

---

# 🧪 Practice Projects

Complete these mini projects to strengthen your Docker skills.

* [ ] Run a **Python Flask app in Docker**
* [ ] Run **Nginx container**
* [ ] Create a **multi-container setup**
* [ ] Deploy a simple **web app using Docker**

Project ideas:

* `<project link>`
* `<project repo>`
* `<notes>`

---

# 📚 Additional Resources

* [https://docs.docker.com/](https://docs.docker.com/)
* [https://hub.docker.com/](https://hub.docker.com/)
* [https://play-with-docker.com/](https://play-with-docker.com/)

---



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

---

##### © 2026 Kunal Harshad Patil  
For more learning resources and updates, connect with me:  
[GitHub](https://github.com/kunal8670) • [LinkedIn](https://www.linkedin.com/in/kunal-patil-8733b528a/)

---

