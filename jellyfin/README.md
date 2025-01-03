
# Jellyfin

Jellyfin is an open-source media server that allows you to stream your media collection across your home network. It provides a user-friendly interface to organize and access your media library on various devices, including your TV.

We use Jellyfin to showcase our media library directly on the TV.

---

## Starting the Jellyfin Service

To start the Jellyfin service, run the following commands:

```bash
cd jellyfin
docker compose up -d
```

Once the service is running, you can access the Jellyfin web interface by navigating to [http://192.168.50.110:8096](http://192.168.50.110:8096) in your browser.

---

## Stopping the Jellyfin Service

To stop the Jellyfin service, use the command:

```bash
docker compose down
```

This will gracefully shut down the service.

---

## Setting Up Jellyfin on Your TV

Follow these steps to set up Jellyfin on your TV:

1. **Access the Web Interface**  
   Open the Jellyfin web interface in your browser.

2. **Add the Server**  
   - Click on the **Add Server** button.  
   - Enter the IP address of your Jellyfin server (e.g., `192.168.50.110`) and click **Add**.

3. **Connect to the Server**  
   - The Jellyfin server should now appear in the list of available servers.  
   - Select your server and click **Connect**.

4. **Grant TV Access**  
   - If prompted, enter the code displayed on your TV into the Jellyfin web interface.  
   - This step authorizes your TV to access the Jellyfin server.

---
