
# 🌐 Phase 7 — Docker Network Management (Chunk 1)

📅 Learning Date: 2026-03-04

Topics covered in this chunk:

- Docker networking fundamentals
- Default Docker networks (`bridge`, `host`, `none`)
- Bridge networking and port mapping
- Host network mode

---

# 1️⃣ Docker Networking Fundamentals

Containers often need to communicate with different systems.

Examples:

```

User Browser
↓
Web Container
↓
Application Container
↓
Database Container

```

Docker networking enables communication between:

- container ↔ container
- container ↔ host machine
- container ↔ internet
- container ↔ external services

Without networking, containers would be **isolated processes**.

---

## How Docker Networking Works

When Docker is installed, it creates a **virtual networking system** inside the host.

Each container receives:

```

Private IP address
Virtual network interface
DNS hostname

```

Example container IP:

```

172.17.0.2

````

Containers communicate through **virtual bridges managed by Docker**.

These bridges act similar to **network switches**.

---

# 2️⃣ Default Docker Networks

Docker automatically creates three default networks.

Check them using:

```bash
docker network ls
````

Example output:

```
NETWORK ID     NAME      DRIVER
xxxxx          bridge    bridge
xxxxx          host      host
xxxxx          none      null
```

These networks define **how containers connect to the host and other containers**.

---

# 3️⃣ Bridge Network (Default Mode)

The **bridge network** is the default networking mode used by Docker.

If no network is specified when running a container:

```bash
docker run nginx
```

Docker automatically connects the container to the **bridge network**.

---

## How Bridge Networking Works

Docker creates a virtual bridge interface on the host:

```
docker0
```

This bridge acts like a **virtual switch**.

Example network layout:

```
Host Machine
     │
docker0 bridge (172.17.0.1)
     │
├── Container A (172.17.0.2)
├── Container B (172.17.0.3)
└── Container C (172.17.0.4)
```

Key idea:

* each container receives a **unique private IP**
* all containers are connected to the **same virtual bridge**
* containers communicate through the bridge

---

## Inspect Bridge Network

View bridge network details:

```bash
docker network inspect bridge
```

This shows:

* connected containers
* container IP addresses
* network gateway
* subnet information

Example subnet:

```
172.17.0.0/16
```

---

# Bridge Network Limitation

Containers inside the bridge network are **not accessible externally by default**.

Example:

```
Browser → container
```

This will fail unless the container port is exposed.

To access a container from outside, **port mapping is required**.

---

# 4️⃣ Port Mapping

Port mapping connects:

```
Host Port → Container Port
```

Example command:

```bash
docker run -d -p 8080:80 --name nginx_web nginx
```

Explanation:

| Option | Meaning                     |
| ------ | --------------------------- |
| -d     | run container in background |
| -p     | map ports                   |
| 8080   | host machine port           |
| 80     | container port              |

This means:

```
Host Port 8080
      ↓
Container Port 80
```

Now the container can be accessed from the host system.

---

## Access the Web Server

Open browser:

```
http://localhost:8080
```

Flow of request:

```
Browser
   ↓
localhost:8080
   ↓
Host Network
   ↓
Docker Bridge (docker0)
   ↓
Container Port 80
   ↓
Nginx Web Server
```

---

# Verify Running Containers

Check running containers:

```bash
docker ps
```

Example output:

```
PORTS
0.0.0.0:8080->80/tcp
```

Meaning:

```
Host port 8080 is mapped to container port 80
```

---

# 5️⃣ Host Network Mode

Host mode removes Docker network isolation.

The container shares the **host machine's network stack**.

Example command:

```bash
docker run --network host nginx
```

In this mode:

* container uses host IP directly
* no virtual bridge is used
* no port mapping required

---

## Host Network Architecture

```
Host Network
     │
Container
```

The container runs as if it is **directly on the host network**.

---

## Example Behavior

If nginx runs on port 80:

```
http://localhost
```

will access the container directly.

No port mapping needed.

---

# Bridge vs Host Networking

| Feature           | Bridge Mode      | Host Mode       |
| ----------------- | ---------------- | --------------- |
| Network Isolation | Yes              | No              |
| Port Mapping      | Required         | Not required    |
| Performance       | Normal           | Faster          |
| Security          | Higher isolation | Lower isolation |

---

# When Host Mode Is Used

Host networking is useful for:

```
high performance applications
network monitoring tools
packet analyzers
system monitoring containers
```

Example:

```bash
docker run --network host nicolaka/netshoot
```

---

### Back to path 
- [Back_to_Roadmap](Learn_docker_From_hire_roadmap.md)
---

# Commands Learned in This Chunk

| Phase   | Command                                           | Purpose                              |
| ------- | ------------------------------------------------- | ------------------------------------ |
| Phase 7 | `docker network ls`                               | List available Docker networks       |
| Phase 7 | `docker network inspect bridge`                   | Inspect bridge network configuration |
| Phase 7 | `docker run -d -p 8080:80 --name nginx_web nginx` | Run container with port mapping      |
| Phase 7 | `docker run --network host nginx`                 | Run container using host network     |

---

# Key Concepts Summary

Docker networking allows containers to communicate with each other and external systems.

Default networks:

```
bridge → default container network with isolation
host   → container shares host network
none   → container has no network access
```

Bridge mode uses **port mapping** to expose services.

Host mode gives **direct network access**.

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


