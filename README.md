
# 🐳 Learn Docker — Roadmap & Notes

A structured **Docker learning roadmap with detailed notes and practical commands** designed to help beginners understand Docker step-by-step.

This repository documents a **phase-wise learning journey**, covering Docker fundamentals, containers, images, networking, and Docker resource management.

---

# 📑 Table of Contents

- [Docker Installation](#docker-installation)
- [Windows (CLI Method)](#windows-cli-method)
- [Linux — Debian / Ubuntu](#linux--debian--ubuntu)
- [Linux — Arch / Arch-based (Manjaro, Garuda)](#linux--arch--arch-based-manjaro-garuda)
- [macOS (CLI using Homebrew)](#macos-cli-using-homebrew)
- [How to Start Learning](#-how-to-start-learning)
- [Repository Structure](#-repository-structure)
- [Author](#-author)
- [Learning Notes Series](#-learning-notes-series)
- [About This Project](#-about-this-project)

---

# Docker Installation

Before starting the roadmap, install Docker on your system.

Follow the instructions below based on your operating system.

---

# Windows (CLI Method)

Install Docker Desktop using **Winget**:

```bash
winget install -e --id Docker.DockerDesktop
````

After installation start Docker Desktop and verify:

```bash
docker --version
```

Test Docker installation:

```bash
docker run hello-world
```

---

# Linux — Debian / Ubuntu

Update packages:

```bash
sudo apt update
```

Install required dependencies:

```bash
sudo apt install ca-certificates curl gnupg
```

Add Docker GPG key:

```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

Add Docker repository:

```bash
echo \
"deb [arch=$(dpkg --print-architecture) \
signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker:

```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io \
docker-buildx-plugin docker-compose-plugin
```

Verify installation:

```bash
docker --version
```

Test Docker:

```bash
sudo docker run hello-world
```

---

# Linux — Arch / Arch-based (Manjaro, Garuda)

Install Docker:

```bash
sudo pacman -S docker
```

Start Docker service:

```bash
sudo systemctl start docker
```

Enable Docker at boot:

```bash
sudo systemctl enable docker
```

Verify installation:

```bash
docker --version
```

Test Docker:

```bash
sudo docker run hello-world
```

---

# macOS (CLI using Homebrew)

Install Docker Desktop:

```bash
brew install --cask docker
```

Start Docker Desktop and verify installation:

```bash
docker --version
```

Test Docker:

```bash
docker run hello-world
```

---

# 🚀 How to Start Learning

Once Docker is installed and working correctly, begin learning using the roadmap.

➡ **Start from here**

[Path/Roadmap](Learn_docker_From_hire_roadmap.md)

The roadmap will guide you through Docker **phase by phase**, helping you understand concepts and practice commands step-by-step.

---

# 📂 Repository Structure

```
Docker-Learning
│
├── Learn_docker_From_hire_roadmap.md   # Docker roadmap
├── docker_notes.md                     # Detailed notes
└── README.md                           # Project overview
```

---

# 👨‍💻 Author

**Kunal H Patil**

📧 Email
[kkunalhpatil.8670@gmail.com](mailto:kkunalhpatil.8670@gmail.com)

🔗 LinkedIn
[https://www.linkedin.com/in/kunal-patil-8733b528a/](https://www.linkedin.com/in/kunal-patil-8733b528a/)

💻 GitHub
[https://github.com/kunal8670](https://github.com/kunal8670)

---

# 📚 Learning Notes Series

This repository is part of my **personal technical learning notes**.

### Upcoming Notes

* 🐍 Python (for Beginners)
* 🧰 Git & GitHub
* 🌐 Full Stack Development

---

# 📌 About This Project

This Docker learning project currently covers concepts from **Phase 1 → Phase 7**, including:

* Docker fundamentals
* Images & containers
* Trusted images
* Building custom images
* Managing Docker resources
* Docker networking

More phases and notes will be added as the learning journey continues.

---

## ⭐ If you found this helpful, feel free to connect on LinkedIn or explore my GitHub for future learning resources.

```

✅ Now the **Table of Contents links will work correctly** because they match GitHub’s automatic anchor format.

---

