# 🐧 Linux Networking & SSH Setup Notes

---

## 1️⃣ Clone the Machine

*(Make sure both machines are ready — Machine A and Machine B)*

---

## 2️⃣ Assign & Verify IP Addresses 🌐

**On Both Machines (A & B):**
Release old IP and get a new one:

```bash
# dhclient -r     # Release current IP address
# dhclient        # Request and assign a new IP address
```

✅ **Check IP Address**:

```bash
# ip -br -c a     # Colorful & brief IP check (recommended)
OR
# ifconfig        # Traditional command (older but still works)
```

For reference:

* **Machine A** ➡️ `192.168.206.140`
* **Machine B** ➡️ `192.168.206.139`

🖼️ *(Add your image here for IP check visualization)*

---

## 3️⃣ Check Connectivity Between Machines 🔄

**From Machine A ➡️ Machine B**:

```bash
# ping 192.168.206.139 -c 4    # Ping Machine B from A
```

**From Machine B ➡️ Machine A**:

```bash
# ping 192.168.206.140 -c 4    # Ping Machine A from B
```

✅ **Ping Output Explained**:

* `c 4` sends exactly 4 packets (you can increase if needed)
* If you see `0% packet loss`, your machines are connected! 🎯

🖼️ *(Add your ping test screenshots here)*

---

## 4️⃣ Set Up SSH (Secure Shell) 🔒

SSH lets you **remotely access** one machine from another securely.

---

### 🖥️ On Machine A (Server Side)

1. **Install SSH server**:

```bash
# apt install openssh-server -y
```

2. **Start SSH service**:

```bash
# systemctl start ssh     # Starts the SSH server
```

3. *(Optional but good practice)*
   Check SSH status:

```bash
# systemctl status ssh    # See if SSH is active and running
```

---

### 💻 On Machine B (Client Side)

1. **Install SSH client**:

```bash
# apt install openssh-client -y
```

2. **Connect to Machine A**:

```bash
# ssh username@192.168.206.140
```

➡️ Replace `username` with the actual user name of Machine A.

🔐 **First-Time Connection Tip**:
You may see a prompt like:

```
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Just type `yes` and press Enter.
Then, enter the password of the user on Machine A.

---

## ✅ Summary Flow

1. **Assign IPs** ➡️ `dhclient`
2. **Verify IPs** ➡️ `ip -br -c a`
3. **Ping Test** ➡️ Check connectivity
4. **SSH Setup** ➡️ Remote access ready! 🎉

---

### 🔥 Pro Tip:

* If SSH doesn’t connect, make sure firewall (`ufw`) isn’t blocking port 22:

```bash
# ufw allow ssh
# ufw enable
```

---
