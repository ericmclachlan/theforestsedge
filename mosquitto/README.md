# Mosquitto

Mosquitto is a message broker that implements the MQTT protocol.

Setting up this mosquitto MQTT broker makes it possible to set up a MQTT client in Home Assistant, and that is useful for a number of things.

In particular, it makes it possible to set up a MQTT client in Home Assistant to control Govee lights from Home Assistant.

## Starting the service

```bash
cd mosquitto
docker compose up -d
```

## Stopping the service

```bash
docker compose down
```
