

# 🐳 Phase 6 — Managing Docker Resources

📅 Learning Date: 2026-03-04

Goal of this phase:

Learn how to **organize Docker images and control containers properly**.  
As projects grow, there may be many images and containers, so management becomes important.

Topics covered:

- Tagging images
- Using labels
- Organizing image versions
- Managing container lifecycle

---

# 1️⃣ Tagging Images

Docker images use **tags** to represent different versions.

Structure:

```

image_name:tag

```

Example:

```

nginx:latest
python:3.10
mywebapp:v1

````

Tags help manage **multiple versions of the same application**.

Example build with tag:

```bash
docker build -t mywebapp:v1 .
````

Check images:

```bash
docker images
```

Example output:

```
mywebapp   v1
nginx      latest
```

---

# 2️⃣ Creating Another Image Version

When the project updates, create a new version.

Example:

```bash
docker build -t mywebapp:v2 .
```

Now two versions exist:

```
mywebapp:v1
mywebapp:v2
```

This helps track **application releases**.

---

# 3️⃣ Retagging Images

Docker allows assigning additional tags to the same image.

Example:

```bash
docker tag mywebapp:v1 mywebapp:stable
```

Now the image has two references:

```
mywebapp:v1
mywebapp:stable
```

---

# 4️⃣ Using Labels

Labels store **metadata information** about images or containers.

They help teams track:

* author
* project
* version
* description

Example in Dockerfile:

```dockerfile
LABEL maintainer="Kunal Patil"
LABEL project="docker-learning"
LABEL version="1.0"
```

Labels improve **image organization in large systems**.

---

# 5️⃣ Viewing Image Metadata

You can inspect images and containers.

```bash
docker inspect mywebapp:v1
```

This command displays:

* labels
* environment variables
* configuration details
* networking info

---

# 6️⃣ Container Lifecycle

Containers move through different states.

Lifecycle:

```
Created
↓
Running
↓
Stopped
↓
Removed
```

Understanding this lifecycle helps manage containers properly.

---

# 7️⃣ Create and Run Container

Example container creation:

```bash
docker run -d --name web_container nginx
```

Explanation:

| Option | Meaning                        |
| ------ | ------------------------------ |
| -d     | run container in background    |
| --name | assign container name          |
| nginx  | image used to create container |

---

# 8️⃣ View Running Containers

```bash
docker ps
```

View all containers (including stopped):

```bash
docker ps -a
```

---

# 9️⃣ Stop Container

```bash
docker stop web_container
```

Container state becomes **stopped**.

---

# 🔟 Start Container Again

```bash
docker start web_container
```

Container returns to **running state**.

---

# 1️⃣1️⃣ Remove Container

A container must be stopped before removal.

```bash
docker rm web_container
```

---

### Back to path 
- [Back_to_Roadmap](Learn_docker_From_hire_roadmap.md)
---

# 📊 Commands Learned in Phase 6

| Phase   | Command                                    | Purpose                      |
| ------- | ------------------------------------------ | ---------------------------- |
| Phase 6 | `docker build -t mywebapp:v1 .`            | Build image with version tag |
| Phase 6 | `docker build -t mywebapp:v2 .`            | Build new version of image   |
| Phase 6 | `docker tag mywebapp:v1 mywebapp:stable`   | Assign additional tag        |
| Phase 6 | `docker inspect mywebapp:v1`               | View image metadata          |
| Phase 6 | `docker run -d --name web_container nginx` | Create and run container     |
| Phase 6 | `docker ps`                                | Show running containers      |
| Phase 6 | `docker ps -a`                             | Show all containers          |
| Phase 6 | `docker stop web_container`                | Stop running container       |
| Phase 6 | `docker start web_container`               | Restart container            |
| Phase 6 | `docker rm web_container`                  | Remove container             |

---

# 🧠 Key Concepts Learned

Image tags → manage versions of images
Labels → store metadata about images
Inspect → view configuration and metadata
Container lifecycle → manage container states

Management Flow:

```
Build Image
↓
Tag Image
↓
Run Container
↓
Stop / Start Container
↓
Remove Container
```

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


