# 🌐 VPC (Virtual Private Cloud) Setup Guide

VPC lets you create your own isolated network inside AWS. Think of it like building your own mini data center inside the cloud!

---

## 🔍 Step 1: Create a VPC

1. Search for **VPC** in AWS Console.
2. Click **Create VPC**.
3. Provide:

   * **VPC Name**: `myvpc`
   * **IPv4 CIDR block**: `10.0.0.0/16` (This gives you 65,536 IP addresses)
4. Click **Create VPC**.

✅ **Done!** You now have a private cloud network ready.

---

## 🌐 Step 2: Create an Internet Gateway (IGW)

An Internet Gateway connects your VPC to the internet.

1. Go to **Internet Gateways**.
2. Click **Create Internet Gateway**.
3. Name it: `my-gw`
4. Click **Create**.
5. Select `my-gw`, right-click → **Attach to VPC**.
6. Select your `myvpc` and attach.

✅ Your VPC is now capable of internet connectivity (but we still need to route traffic).

---

## 🌍 Step 3: Create Subnets (Public & Private)

Subnets divide your VPC's IP range into smaller networks.

### 🟢 Public Subnet:

1. Go to **Subnets** → **Create Subnet**.
2. Select **myvpc**.
3. Subnet Name: `my_prt_subnet`
4. IPv4 CIDR block: `10.0.1.0/24` (256 IPs)
5. Click **Create Subnet**.

### 🔒 Private Subnet:

1. Again, click **Create Subnet**.
2. Select **myvpc**.
3. Subnet Name: `my-subnet`
4. IPv4 CIDR block: `10.0.2.0/24`
5. Click **Create Subnet**.

✅ Now you have both public and private zones in your VPC.

---

## 📊 Step 4: Create & Configure Route Table

Route Tables control where your network traffic goes.

1. Go to **Route Tables** → **Create Route Table**.
2. Name: `my-public-rt`
3. Select **myvpc**.
4. Click **Create**.

### 🔗 Associate Public Subnet:

1. Select your route table → **Subnet Associations**.
2. Click **Edit subnet associations**.
3. Select **my\_prt\_subnet** (the public one).
4. Save.

---

## 🌐 Step 5: Route Traffic to Internet Gateway

1. In **Route Tables**, select your `my-public-rt`.
2. Go to **Routes** tab → click **Edit Routes**.
3. Click **Add Route**:

   * **Destination**: `0.0.0.0/0` (this means *anywhere on the internet*)
   * **Target**: Choose **Internet Gateway** (`my-gw`)
4. Save changes.

✅ Now your public subnet has internet access!

---

## 🖥️ Step 6: Launch EC2 Instances

We’ll launch 2 servers: one public, one private.

### 🌐 Public EC2 Instance:

1. Search **EC2** → open **EC2 Dashboard**.
2. Click **Launch Instance**.
3. Name: `my_pub_ec2`
4. Choose an OS (e.g., Amazon Linux 2).
5. Select an existing **SSH key pair**.
6. Under **Network Settings**:

   * Choose your VPC (`myvpc`)
   * Select **my\_prt\_subnet** (public)
   * **Enable Auto-assign Public IP** ✅
7. Click **Launch Instance**.

### 🔒 Private EC2 Instance:

1. Repeat **Launch Instance**.
2. Name: `my_priv_ec2`
3. Select same OS & key pair.
4. In **Network Settings**:

   * Choose your VPC.
   * Select **my-subnet** (private)
   * **Disable Auto-assign Public IP** ❌
5. Launch Instance.

✅ Now you have:

* A public EC2 connected to the internet 🌐
* A private EC2 inside your VPC with no internet 🔒

---

## 🗑️ Step 7: Clean Up (Delete Resources)

1. **Terminate** both EC2 instances from **EC2 Dashboard**.
2. Go to **VPC Dashboard**.
3. Select **Internet Gateway (`my-gw`)**:

   * Right-click → **Detach from VPC**.
   * Right-click again → **Delete**.
4. Go to **VPCs**:

   * Select your `myvpc`.
   * Right-click → **Delete**.

✅ Clean up completed! No charges for unused VPC components.

---

## ⚡ Quick Revision Recap:

* **VPC** = Your private network in AWS 🌐
* **Internet Gateway** = Connects VPC to internet 🔗
* **Subnet** = Smaller division of VPC IPs (public/private zones) 📦
* **Route Table** = Traffic rules (public subnet → IGW 🌍)
* **EC2** = Virtual server (public = internet, private = internal) 🖥️

---
