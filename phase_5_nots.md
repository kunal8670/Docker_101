
# 🐳 Phase 5 — Build and Run Custom Images

📅 Learning Date: 2026-03-04

Goal of this phase:

Create your **own Docker image** using a **Dockerfile** and run a container from it.

Full workflow:

```

Download Base Image
↓
Create Dockerfile
↓
Build Docker Image
↓
Create Container
↓
Run Container

```

---

# 1️⃣ Download Base Image

Docker images usually start from an existing **base image**.

Example base image:

```

python:3.10

````

This image already contains:

- Linux environment
- Python 3.10 installed
- Required system libraries

Download the base image.

```bash
docker pull python:3.10
````

Check downloaded images:

```bash
docker images
```
## #Note:

| According to the project requirements, choose and pull the appropriate base image (for example `nginx`, `python`, `node`, etc.). This base image provides the runtime environment needed for the application before building the custom Docker image.

- Static website → nginx image
- Python web app → python image
- Node.js app → node image
- Java app → openjdk image
---


# 2️⃣ Create Project Directory

Create a folder for your Docker project.

```bash
mkdir docker-python-test
cd docker-python-test
```

This directory will contain:

```
docker-python-test
│
├── Dockerfile
└── project files
```
--- 
## #Note:
In the main project directory, create a  `Dockerfile` that defines the environment setup and execution steps. Docker reads this file to build an image. Once the image is built, it can be used to create and run containers for deployment.

---

# 3️⃣ Create Dockerfile

Create a file named:

```
Dockerfile
```

Example content:

```dockerfile
FROM python:3.10

WORKDIR /app

COPY . .

CMD ["python3", "--version"]
```

### Explanation

| Instruction | Purpose                                |
| ----------- | -------------------------------------- |
| FROM        | Select base image                      |
| WORKDIR     | Set working directory inside container |
| COPY        | Copy files from host to container      |
| CMD         | Command executed when container starts |

---

# 4️⃣ Build Docker Image

Docker reads the Dockerfile and builds an image.

Run:

```bash
docker build -t python_test_image .
```

Explanation:

| Part              | Meaning               |
| ----------------- | --------------------- |
| docker build      | build an image        |
| -t                | assign image name     |
| python_test_image | image name            |
| .                 | use current directory |

Docker will process each step:

```
1. Pull python:3.10
2. Create /app directory
3. Copy project files
4. Set startup command
```

After build completes, check images:

```bash
docker images
```

You should see:

```
python_test_image
```

---

# 5️⃣ Create and Run Container

Run a container from the created image.

```bash
docker run python_test_image
```

Docker will:

```
Create container
↓
Start container
↓
Execute CMD
↓
python3 --version
```

Expected output:

```
Python 3.10.x
```

---

# 6️⃣ Run Container Interactively

You can also open a shell inside the container.

```bash
docker run -it python_test_image bash
```

This gives access to the container environment.

Example:

```
root@container:/app#
```

### Back to path 
- [Back_to_Roadmap](Learn_docker_From_hire_roadmap.md)
---

# 📊 Commands Learned in Phase 5

| Phase   | Command                                 | Purpose                             |
| ------- | --------------------------------------- | ----------------------------------- |
| Phase 5 | `docker pull python:3.10`               | Download base image                 |
| Phase 5 | `mkdir docker-python-test`              | Create project folder               |
| Phase 5 | `docker build -t python_test_image .`   | Build image from Dockerfile         |
| Phase 5 | `docker images`                         | Show available images               |
| Phase 5 | `docker run python_test_image`          | Create and run container from image |
| Phase 5 | `docker run -it python_test_image bash` | Start interactive container         |

---

# 🧠 Key Concepts Learned

Dockerfile → instructions for building image

Docker Image → packaged environment

Docker Container → running instance of image

Build Flow:

```
Dockerfile
   ↓
docker build
   ↓
Docker Image
   ↓
docker run
   ↓
Container
```

---

# 🧪 Practice Task

Create a container that prints:

```
Hello from Docker
```

Hint Dockerfile:

```
FROM ubuntu
CMD ["echo", "Hello from Docker"]
```

Build and run it.

---


# Personal Notes

```
(write your notes here)
```

---
##### © 2026 Kunal Harshad Patil  
For more learning resources and updates, connect with me:  
[GitHub](https://github.com/kunal8670) • [LinkedIn](https://www.linkedin.com/in/kunal-patil-8733b528a/)

---



