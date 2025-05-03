# 🚀 **Docker Basics Notes**

*(Easy to Learn, Easy to Revise!)*

---

### 📦 **Docker Hub**

Public/private repository server to store images.

🔗 **Link:** [docker hub](https://hub.docker.com/)

---

## ⚙️ **Docker Commands**

### 1️⃣ **Run (Start a Container)**

```
# docker run <image>
# docker run <image>:latest
# docker run <image>:1.1.0
```

Detached Mode (Run in background):

```
# docker run -d <image>:1.1.0
```

➡️ `-d` = detach

🖼️ *Example Images:*

```
httpd, nginx
```

![image: httpd, nginx](https://hub.docker.com/)

---

### 2️⃣ **ps (List Running Containers)**

```
# docker ps               # Running containers only
# docker ps -a            # All (running + stopped)
# docker ps -q            # Only container IDs
# docker ps -aq           # All container IDs
```

---

### 3️⃣ **stop/start/restart (Manage Containers)**

Stop:

```
# docker stop <NAME or CONTAINER ID>
# docker stop $(docker ps -q)  # Stop all running
```

Start:

```
# docker start <CONTAINER_ID>
```

Restart:

```
# docker restart <CONTAINER_ID>
```

---

### 4️⃣ **rm (Remove Containers)**

Remove stopped container:

```
# docker rm <name/container ID>
```

Force remove (even running):

```
# docker rm -f <name/container ID>
```

💡 Remove all containers:

```
# docker rm -f $(docker ps -aq)
```

---

### 5️⃣ **images (List Images)**

```
# docker images
# docker images -q  # Only image IDs
```

#### ⬇️ **Pull (Download Image)**

```
# docker pull <image>
# docker pull <image>:<tag>
```

---

### 6️⃣ **rmi (Remove Images)**

Remove single image:

```
# docker rmi <image_id>
# docker rmi -f <image_id>  # Force
```

💣 Remove all images:

```
# docker rmi $(docker images -q)
# docker rmi -f $(docker images -q)
```

---

### 7️⃣ **pull (Download Only Image)**

```
# docker pull docker/whalesays
```

---

### 8️⃣ **exec (Run Commands Inside Container)**

Read file inside container:

```
# docker exec <name> cat /etc/passwd
```

Interactive bash shell:

```
# docker exec -it <name or id> bash
```

➡️ `-it` = interactive terminal

---

### 9️⃣ **Run (Attach & Detach Mode)**

Attach (default):

```
# docker run <image>
```

Detach (background):

```
# docker run -d <image>
```

Attach again:

```
# docker attach <container_id>
```

---

## 🔎 **PART 2: Inspect & Networking**

---

### 🔍 **Inspect (Get Container Info)**

#### Get IP Address:

```
# docker inspect -f '{{json .NetworkSettings.IPAddress}}' <container_ID or Name>
```

#### Get Gateway:

```
# docker inspect -f '{{json .NetworkSettings.Gateway}}' <container_ID or Name>
```

---

### 🌐 **Port Mapping**

Run **httpd** web app on **port 8080** (host) mapped to **80** (container):

```
# docker run -d --name "web1" -p 8080:80 httpd
```

#### Example:

* **Image:** nginx
* **Container Port:** 80/tcp
* **Mapped Port:** 8080 (host) <-> 80 (container)
* **Name:** webserver1

Access with:

```
curl "http://<VM's IP>:8080"
```

Or run nginx:

```
# docker run -d --name "webserver1" -p 8080:80 nginx:latest
```

---

## 🗂️ **Volume Mapping (Host ↔️ Container)**

➡️ Map host directory **/web1** to container’s **/usr/local/apache2/htdocs**

### Steps:

1. Create folder and add HTML:

   ```
   # mkdir /web1
   # cat > /web1/index.html
   <html><body><h1>ULALA</h1></body></html>
   ```

2. Run container with volume mapping:

   ```
   # docker run -d --name "server1" \
     -v /web1:/usr/local/apache2/htdocs \
     -p 80:80 httpd:latest
   ```

---

## 💡 **Tips for Beginners**

* Always check container status with `docker ps -a` before removing.
* Use `docker images -q` and `docker ps -q` for quick ID lists.
* Detach mode (`-d`) is best for running web apps in background.
* Volume mapping makes files **persistent** outside the container.

---
