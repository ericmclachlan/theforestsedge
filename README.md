# theforestsedge

A configuration for our home server.

### Prerequisites


## Docker

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

## Flashing the SD Card with the WIFI details.

Create a file called my-network under `/CONFIG/network` with the following content:

```
[connection]
id=my-network
uuid=3d9f1a7e-d9b3-4e4e-9c36-d1f543f1a6f0
type=wifi

[wifi]
mode=infrastructure
ssid=SSID_NAME

[wifi-security]
auth-alg=open
key-mgmt=wpa-psk
psk=YOUR_PASSWORD

[ipv4]
method=auto

[ipv6]
method=ignore
```

Replace the SSID_NAME and YOUR_PASSWORD with the SSID and password of your WIFI network.
