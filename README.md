# The Forest's Edge

This file contains instructions for setting up our home server.

The server is running Ubuntu on a Raspberry Pi 4. This is a low-powered server but it's able to run a lot of the services we need.

**Hardware**: Raspberry Pi 4, 8GB RAM, 128GB SSD

**Operating System**: Ubuntu 24.10

**Software**: Docker, Docker Compose

**Services**:
- **Home Assistant**: Home automation
- **Nextcloud**: Cloud storage
- **Nginx Proxy Manager**: Reverse proxy
- **Photoprism**: Photo management

## Setting up the Raspberry Pi

<details>
  <summary>How to configure the Raspberry Pi</summary>

### Installing the OS

Software can be installed on the Raspberry Pi using the Raspberry Pi Imager tool. Our server has been installed with Ubuntu Server.

After clicking the Next button in the Raspberry Pi Imager tool, you can configure some settings that we will need later.

1. Set the hostname to `server.local`.
2. Set the username to `admin`.
3. Set the password to something you will remember.
4. Set the SSID and password for the WIFI network.

After clicking the Next button, the Raspberry Pi Imager tool will write the settings to the SD card and then boot the Raspberry Pi.

Setting the WIFI details is optional. If you don't set the WIFI details, you can connect the Raspberry Pi to the router using an ethernet cable.

### Powering on the Raspberry Pi

When the device starts up, it will connect to the WIFI network and then boot the operating system: Ubuntu.

If you connect a HDMI-to-Mini HDMI cable to the Raspberry Pi, you can see the login screen.
Now, you can boot the Raspberry Pi and connect to it using SSH.

### Connecting to the Raspberry Pi

Once the Raspberry Pi is booted, you can connect to it using SSH.

```bash
ssh admin@server.local.
```

</details>

## Setting up the Software

<details>
  <summary>How to install Docker and Docker Compose</summary>

### Docker

Run the following commands to install Docker and Docker Compose.

```bash
sudo apt update
sudo apt install -y ca-certificates curl gnupg lsb-release

# Add Docker's official GPG key
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Set up the Docker repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker Engine
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

You can check the installation with `docker --version` and `docker compose --version`.

</details>

## Running the Services

<details>
  <summary>How to run the services</summary>

### Download the repository

This repository contains the Docker Compose files for the services we want to run on the server.

You can download the repository from GitHub.
```bash
git clone https://github.com/ericmclachlan/theforestsedge.git
```

Now, for each service, you can run the Docker Compose file.

For example, to start the Nextcloud service, you can run the following command.

```bash
cd theforestsedge/nextcloud
docker compose up -d
```

And if you ever need to stop a service, you can use the following command from the same directory.

```bash
docker compose down
```

</details>
