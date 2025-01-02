
# Home Assistant

Home Assistant is a home automation platform that provides a way to control and monitor your home.

This service is deployed on a Raspberry Pi 4 using Docker.

## Starting the service

To start the service, use the following command:

```bash
docker compose up -d
```

To stop the service, use the following command:

```bash
docker compose down
```


## Backups

Backups are stored in the `/mnt/raid/backups/homeassistant` directory.

Home Assistant is configured to make weekly backups. These backups are compressed into `.tar` files, which contain a `backup.json` file and a `homeassistant.tar.gz` file.

---

## Restoring a Backup

<details>
  <summary>How to restore a backup</summary>

### Step 1: Extract the Main Backup File

To restore a backup, first extract the main `.tar` file:

```bash
tar -xvf my_backup.tar
```

This command will extract:
- `backup.json` (metadata about the backup)
- `homeassistant.tar.gz` (the compressed Home Assistant configuration)

### Step 2: Extract the Configuration Archive

Next, extract the `homeassistant.tar.gz` file:

```bash
tar -xvzf homeassistant.tar.gz
```

This command will extract a `data` directory that contains your Home Assistant configuration.

### Step 3: Replace the Current Configuration

Rename the extracted `data` directory to `config`:

```bash
mv data config
```

Place the `config` directory in the same location as the `docker-compose.yaml` file. The Docker Compose configuration maps this directory to the Home Assistant container as the `/config` directory.

### Step 4: Start the Home Assistant Service

Spin up the Home Assistant container using Docker Compose:

```bash
docker compose up -d
```

This effectively restores the backup.

---

### Step 5: Monitor the Home Assistant Logs

Monitor the logs for any issues:

```bash
docker compose logs -f
```

Look out for errors. Any devices (phones, tablets, etc. running the Home Assistant app) will need to be re-authenticated with the restored Home Assistant instance.

</details>
