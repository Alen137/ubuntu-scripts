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


### 

```bash
sudo apt update
sudo apt install python3-venv -y
```

### Verify the Installation

```bash
python3 --version
```

### Create virtual env

```bash
python3 -m venv myenv
```

### Activate

```bash
source myenv/bin/activate
```

### Install required Python package

```bash
pip3 install -r requirements.txt
```

### Activate

```bash
python3 -m venv myenv
```

### If you get a "command not found" error for pip3, install it with:

```bash
sudo apt update
sudo apt install python3-pip
```

### Run python application

```bash
sudo apt update
python3 app.py

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
