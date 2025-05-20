# Ubuntu VM Setup Guide

## Network Configuration

- **Make the network connection bridge in image OS setting**

## Create a New SSH User (without superuser access)

```bash
sudo adduser newuser
```

## Provide Admin Permissions

```bash
sudo usermod -aG sudo newuser
```

---

## SSH into Ubuntu VM (VMware)

### 1. Install and Enable SSH Server on Ubuntu VM

Open a terminal in your Ubuntu VM and run:

```bash
sudo apt update
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh
```

### 2. Verify SSH is Running

```bash
sudo systemctl status ssh
```

### 3. Find the Ubuntu VM’s IP Address

```bash
ifconfig
```

### 4. Connect from Windows

```bash
ssh newuser@<IP>
```

- You can also use **WinSCP** for file transfers.

---

## Installing Python 3.11 on Ubuntu

### Add the Deadsnakes PPA

```bash
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
```

### Install Python 3.11

```bash
sudo apt install python3.11
```

### Verify the Installation

```bash
python3.11 --version
```

> You can configure Python 3.11 as the default `python` command if desired, but Ubuntu typically keeps the system Python separate.

---

## Installing Node.js on Ubuntu (Using NVM)

### Install NVM (Node Version Manager)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

### Activate NVM

```bash
source ~/.bashrc
```

> You may need to restart your terminal.

### Install the Latest LTS Version of Node.js

```bash
nvm install --lts
```

### Verify Installation

```bash
node -v
npm -v
```
