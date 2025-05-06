# MQTT – Message Queuing Telemetry Transport

## 📘 Overview

**MQTT** is a lightweight, publish-subscribe messaging protocol commonly used in IoT (Internet of Things) environments. It allows devices to communicate by sending and receiving messages through a central broker.

---

## 🔧 Core Concepts

### 🔹 Broker
- The **broker** is the central server that receives all messages from clients and forwards them to the correct recipients.
- Popular brokers: **Mosquitto**, **HiveMQ**, **EMQX**.
- Without the broker, publishers and subscribers cannot communicate.

### 🔹 Publisher
- A **publisher** is a device or program that sends messages.
- It sends messages to a **topic** (like a channel).
- It does not care who receives the message.

### 🔹 Subscriber
- A **subscriber** listens to a topic and receives messages published on that topic.
- Multiple subscribers can listen to the same topic.

### 🔹 Topic
- A **topic** is a string that defines the channel of communication, e.g., `home/livingroom/temperature`.

---

## 🔄 How MQTT Works

1. The publisher connects to the broker and sends a message to a topic.
2. The broker receives the message and checks who is subscribed to that topic.
3. All subscribers of that topic receive the message.

---

## 🔌 Connecting and Disconnecting

### ✅ Connect to a Broker
To connect to an MQTT broker, you'll need:
- **Host/IP** (e.g., `broker.hivemq.com`)
- **Port** (default is `1883` for unencrypted, `8883` for encrypted/TLS)

#### Example using Python (`paho-mqtt`):
```python
import paho.mqtt.client as mqtt

client = mqtt.Client("client1")  # Unique client ID
client.connect("broker.hivemq.com", 1883)  # Connect to public broker
client.loop_start()  # Start loop to process callbacks
```

### ❌ Disconnect
```python
client.disconnect()
client.loop_stop()
```

---

## 📨 Publishing and Subscribing

### 📤 Publish Message
```python
client.publish("home/temperature", "22.5")  # Sends string "22.5" to the topic
```

### 📥 Subscribe to Topic
```python
def on_message(client, userdata, message):
    print("Received:", str(message.payload.decode()))

client.subscribe("home/temperature")
client.on_message = on_message
```

---

## 💡 What is a String in MQTT?
In MQTT, messages are usually sent as strings. A string is a sequence of text characters.

Examples:
- `"Hello World"` – plain text
- `"22.5"` – temperature as a string
- `"ON"` / `"OFF"` – status commands

You can also send JSON or binary data, but strings are most common for simple applications.

---

## 🛠 Tools You Can Use
- 🧪 **MQTT.fx** – GUI client
- 🖥 **Mosquitto** – Open-source broker and CLI tools
- 🐍 **paho-mqtt** – Python library
- 🔧 **Node-RED** – Low-code IoT workflow tool

---

## 🧪 Example Flow
1. Device A publishes `"22.5"` to `home/temperature`.
2. Broker receives the message.
3. Device B, subscribed to `home/temperature`, receives `"22.5"`.

---

## 📋 Summary Table

| Term         | Description                              |
|--------------|------------------------------------------|
| **Broker**   | Server that routes messages             |
| **Publisher**| Sends messages to a topic               |
| **Subscriber**| Receives messages from a topic         |
| **Topic**    | Communication channel (e.g., `home/temp`)|
| **String**   | Text message sent via MQTT              |

---

## 🔗 Useful Links
- 🌐 [Official site](https://mqtt.org)
- 📚 [Python client: Eclipse Paho](https://www.eclipse.org/paho/)
- 🧰 [Broker: Mosquitto](https://mosquitto.org/)

---

## ✅ Getting Started Checklist
1. Install MQTT client (e.g., `paho-mqtt` for Python).
2. Connect to a broker.
3. Publish a message.
4. Subscribe to a topic.
5. Handle received messages.

---

📝 **Tip**: Always make sure to use unique client IDs when connecting multiple clients to the same broker.