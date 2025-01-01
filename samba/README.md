
# Samba Service

Samba is a file sharing service that allows you to share files between computers on a network.


## Setting up the Samba server

<details>
<summary>How to set up the Samba server</summary>

We will be using a Docker container to run a Samba service.

You can spin up the docker container with the following command:

```bash
cd samba
docker compose up -d
```

You can check for errors in the Samba service with the following command:

```bash
docker compose logs -f
```

If all goes well, you should see something like the following in the output:

```
samba  | smbd version 4.13.7 started.
samba  | Copyright Andrew Tridgell and the Samba Team 1992-2020
samba  | daemon_ready: daemon 'smbd' finished starting up and ready to serve connections
```


</details>

## Setting up the Samba client

<details>
<summary>How to set up the Samba client</summary>

### Windows

A Windows machine can access the Samba service with File Explorer. (e.g. `\\server.local\backups`)

### Linux

A Linux machine can access the Samba service using the `smbclient` command.

In order to use Samba, you need to install the Samba client which will allow your computer to connect to the Samba service.

```bash
sudo apt install smbclient
```

You should see the Samba service running in the output.

You can connect to the Samba service with the following command:

```bash
smbclient //server.local/backups -U guest
```

You can now request a list of files in the Samba service with the following command:

```bash
ls
```

You should now be able to see the files in the `backups` directory of the Samba service.

</details>
