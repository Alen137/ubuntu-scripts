Installing Python 3.11 on Ubuntu
Add the deadsnakes PPA repository which contains the latest Python versions:

bash
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
Install Python 3.11:

bash
sudo apt install python3.11
(Optional) Install additional Python 3.11 support packages for development, virtual environments, and other utilities:

bash
sudo apt install python3.11-dev python3.11-venv python3.11-distutils python3.11-gdbm python3.11-tk python3.11-lib2to3 -y
Verify the installation:

bash
python3.11 --version
You can configure Python 3.11 as the default python command if desired, but Ubuntu typically keeps the system Python separate.

Installing Node.js on Ubuntu
There are multiple methods to install Node.js; the recommended way for flexibility is using NVM (Node Version Manager):

Install NVM by running:

bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
Activate NVM (you may need to restart your terminal or run):

bash
source ~/.bashrc
Install the latest LTS version of Node.js with NVM:

bash
nvm install --lts
Verify the installed Node.js and npm versions:

bash
node -v
npm -v
Alternatively, you can install Node.js from Ubuntu's default repository (may be older version):

bash
sudo apt update
sudo apt install nodejs npm
nodejs -v
npm -v
Or use NodeSource PPA to get a specific newer version:

bash
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install nodejs
node -v
npm -v



Steps to SSH into Ubuntu VM in VMware
Install and enable SSH server on Ubuntu VM:

Open a terminal in your Ubuntu VM and run:

bash
sudo apt update
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh
Verify SSH is running:

bash
sudo systemctl status ssh
Find the Ubuntu VM’s IP address:

Run:

bash
ip a
or

bash
ifconfig
Note the IP address assigned to the VM’s network adapter.

Configure VMware network mode:

For easier SSH access from your host, set the VM’s network adapter to Bridged mode. This way, the VM gets an IP on the same network as your host PC.

Alternatively, use NAT mode but you may need to configure port forwarding on VMware to forward port 22 to the VM.

From your host machine (Windows):

Use an SSH client like PuTTY.

Connect to the VM’s IP address on port 22:

text
ssh username@vm-ip-address
or in PuTTY, enter the IP and port 22, then connect.

Optional: Configure firewall on Ubuntu VM

If you have ufw enabled, allow SSH:

bash
sudo ufw allow ssh
sudo ufw enable


Confirm the VM’s IP address (e.g., using ip a) and ensure the VM network is set to Bridged mode in VMware so that the VM is on the same network as your Windows host. This allows your host to reach the VM via its IP address.

Disable or configure any firewalls on Ubuntu that might block SSH (e.g., allow port 22 in ufw):

bash
sudo ufw allow ssh
In WinSCP, use the following settings to connect:

File protocol: SFTP (or SCP)

Host name: IP address of the Ubuntu VM

Port number: 22

User name: Your Ubuntu username

Password: Your Ubuntu password (or use SSH key authentication if configured)

If you face "connection refused" or timeout errors, check network settings, firewall, and confirm SSH is running on the VM.

This setup lets you securely transfer files between your Windows host and Ubuntu VM using WinSCP over SSH