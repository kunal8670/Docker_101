

# 🌐 Phase 7 — Docker Network Management (Chunk 2)

📅 Learning Date: 2026-03-04

Topics covered in this chunk:

- None network mode (isolated containers)
- Container-to-container communication
- Creating custom Docker networks
- Inspecting and managing Docker networks

---

# 1️⃣ None Network Mode (Fully Isolated Container)

The **none network mode** disables networking completely for a container.

When a container runs with this mode:

- it has **no network connectivity**
- it cannot communicate with:
  - other containers
  - the host machine
  - the internet
- it only has the **loopback interface (`lo`)**

This mode creates a **fully isolated container**.

---

## Example Command

```bash
docker run --network none ubuntu
````

This runs a container with **networking disabled**.

---

## Checking Network Interfaces Inside the Container

Run container interactively:

```bash
docker run -it --network none ubuntu bash
```

Then check network interfaces:

```bash
ip addr
```

Example output:

```
1: lo: <LOOPBACK>
```

Only the **loopback interface** exists.

There will be **no `eth0` interface**, meaning the container has no external network access.

---

## Use Cases for None Network Mode

None networking is useful for:

```
security testing
malware analysis
sandbox environments
isolated workloads
sensitive data processing
```

It ensures **no network communication is possible**.

---

# 2️⃣ Container-to-Container Communication

Many applications require multiple containers to communicate.

Example architecture:

```
User Browser
      ↓
Web Server Container
      ↓
Backend API Container
      ↓
Database Container
```

Docker networking allows containers to communicate **if they belong to the same network**.

---

## Example Containers

Run two containers:

```bash
docker run -dit --name container1 ubuntu
docker run -dit --name container2 ubuntu
```

Both containers connect to the **default bridge network**.

---

## Communication Using Container IP

Find container IP:

```bash
docker inspect container1
```

Example IP:

```
172.17.0.2
```

From another container you could connect using:

```
ping 172.17.0.2
```

However, **IP-based communication is not recommended** because container IPs can change.

---

# 3️⃣ Creating Custom Docker Networks

Custom networks allow containers to communicate **using container names instead of IP addresses**.

This simplifies networking in multi-container applications.

---

## Create Custom Network

```bash
docker network create my_network
```

Verify network creation:

```bash
docker network ls
```

Example output:

```
bridge
host
none
my_network
```

Now `my_network` is a **user-defined network**.

---

## Run Containers Inside Custom Network

Start a web container:

```bash
docker run -dit --network my_network --name web ubuntu
```

Start a database container:

```bash
docker run -dit --network my_network --name db ubuntu
```

Both containers now belong to the same network:

```
my_network
```

---

## Docker Internal DNS

Docker automatically creates **DNS records** for containers within the same custom network.

This allows containers to communicate using **container names**.

Example:

Inside the `web` container:

```bash
docker exec -it web bash
```

Test communication:

```
ping db
```

Docker automatically resolves:

```
db → container IP
```

This feature is called **Docker Internal DNS**.

---

## Example Real Application Architecture

```
Frontend Container
       ↓
Backend Container
       ↓
Database Container
```

Instead of using IP addresses:

```
backend:5000
database:3306
```

Container names act as **hostnames**.

---

# 4️⃣ Inspecting Docker Networks

Docker allows inspection of networks to understand how containers are connected.

---

## Inspect Default Bridge Network

```bash
docker network inspect bridge
```

This command displays:

```
network driver
subnet range
gateway
connected containers
container IP addresses
```

---

## Inspect Custom Network

```bash
docker network inspect my_network
```

Example information shown:

```
container name
container IP
MAC address
network settings
subnet and gateway
```

This helps debug **network communication issues**.

---

# 5️⃣ Removing Docker Networks

When a network is no longer needed, it can be removed.

Example command:

```bash
docker network rm my_network
```

Important rule:

```
The network must not have running containers connected.
```

Otherwise Docker will produce an error.

---

### Back to path 
- [Back_to_Roadmap](Learn_docker_From_hire_roadmap.md)
---

# Docker Network Driver Summary

Docker provides several network drivers.

```
bridge → default container network with isolation
host   → container shares host network
none   → container has no networking
custom → user-created networks for container communication
```

Custom networks are commonly used for **multi-container applications**.

---

# Example Production Architecture

```
Internet
   ↓
Nginx Container
   ↓
Backend API Container
   ↓
Database Container
```

All containers run inside a **custom Docker network** to enable communication.

---

# 📊 Commands Learned in This Chunk

| Phase   | Command                                                  | Purpose                                       |
| ------- | -------------------------------------------------------- | --------------------------------------------- |
| Phase 7 | `docker run --network none ubuntu`                       | Run container with networking disabled        |
| Phase 7 | `docker network create my_network`                       | Create a custom Docker network                |
| Phase 7 | `docker run -dit --network my_network --name web ubuntu` | Run container inside a custom network         |
| Phase 7 | `docker run -dit --network my_network --name db ubuntu`  | Run another container inside the same network |
| Phase 7 | `docker network inspect my_network`                      | Inspect network configuration                 |
| Phase 7 | `docker network rm my_network`                           | Remove a Docker network                       |

---

# 🧠 Key Concepts Learned

* None network mode creates **fully isolated containers**
* Containers can communicate only when connected to the **same network**
* Custom networks allow communication using **container names**
* Docker automatically provides **internal DNS resolution**
* Network inspection helps troubleshoot container connectivity issues

---

# 📝 Personal Notes

```
(write your notes here)
```

---

##### © 2026 Kunal Harshad Patil  
For more learning resources and updates, connect with me:  
[GitHub](https://github.com/kunal8670) • [LinkedIn](https://www.linkedin.com/in/kunal-patil-8733b528a/)

---


