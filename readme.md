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
To connect to an MQTT broker using JavaScript, you'll need the `mqtt.js` library. Install it using npm:
```bash
npm install mqtt
```

#### Example using JavaScript (`mqtt.js`):
```javascript
const mqtt = require('mqtt');

// Connect to the broker
const client = mqtt.connect('mqtt://broker.hivemq.com');

// Handle connection
client.on('connect', () => {
    console.log('Connected to broker');
});
```

### ❌ Disconnect
```javascript
client.end(() => {
    console.log('Disconnected from broker');
});
```

---

## 📨 Publishing and Subscribing

### 📤 Publish Message
```javascript
client.publish('home/temperature', '22.5', () => {
    console.log('Message published');
});
```

### 📥 Subscribe to Topic
```javascript
client.subscribe('home/temperature', () => {
    console.log('Subscribed to topic');
});

client.on('message', (topic, message) => {
    console.log(`Received message: ${message.toString()} on topic: ${topic}`);
});
```

---

## 🌐 WebSocket-Based MQTT Workflows

### 1. Publish Messages Using `mqtt.html`
The `mqtt.html` file allows you to publish messages to a topic via a WebSocket connection.

#### Steps:
1. Open `mqtt.html` in a browser.
2. Enter the **topic** (e.g., `test/topic`) and the **message** you want to send.
3. Click the **Send** button to publish the message.

#### Code Overview:
- The file connects to the broker using WebSocket (`wss://push.mozility.com:8084/mqtt`).
- It uses the `mqtt.js` library to handle the connection and publish messages.
- Example:
  ```javascript
  client.publish(topic, message);
  ```

---

### 2. Subscribe to Topics Using `subcribesmqtt.html`
The `subcribesmqtt.html` file allows you to subscribe to a topic and receive messages via a WebSocket connection.

#### Steps:
1. Open `subcribesmqtt.html` in a browser.
2. Enter the **topic** you want to subscribe to (e.g., `test/topic`).
3. Click the **Subscribe** button to start receiving messages.
4. Messages will appear in the "Messages" section of the page.

#### Code Overview:
- The file connects to the broker using WebSocket (`wss://push.mozility.com:8084/mqtt`).
- It uses the `mqtt.js` library to handle the connection and subscription.
- Example:
  ```javascript
  client.subscribe(topic, (err) => {
      if (!err) {
          console.log(`Subscribed to topic: ${topic}`);
      }
  });

  client.on('message', (topic, message) => {
      console.log(`Received message: ${message.toString()} on topic: ${topic}`);
  });
  ```

---

## 🛠 Tools You Can Use
- 🧪 **MQTT.fx** – GUI client
- 🖥 **Mosquitto** – Open-source broker and CLI tools
- 🔧 **Node-RED** – Low-code IoT workflow tool

---

## ✅ Getting Started Checklist
1. Install MQTT client (e.g., `mqtt.js` for JavaScript).
2. Connect to a broker.
3. Publish a message.
4. Subscribe to a topic.
5. Handle received messages.

---

## 🚀 How to Use MQTT in Your Project

### 1. Install Required Libraries
For JavaScript, install the `mqtt.js` library:
```bash
npm install mqtt
```

### 2. Set Up a Broker
- Use a public broker like `broker.hivemq.com` for testing.
- Alternatively, set up a local broker using **Mosquitto**:
  ```bash
  mosquitto
  ```

### 3. Implement MQTT in Your Code
- Use the provided examples to connect, publish, and subscribe to topics.

---

📝 **Tip**: Always make sure to use unique client IDs when connecting multiple clients to the same broker.