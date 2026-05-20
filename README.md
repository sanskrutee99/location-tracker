# 📍 Real-Time Location Tracker

A real-time multi-user location tracking web app built with **Node.js**, **Express**, **Socket.io**, and **Leaflet.js**. Every connected user's location appears as a live marker on an interactive map — markers update in real time and are removed automatically when a user disconnects.

---

## ✨ Features

- 🌍 Live map powered by [Leaflet.js](https://leafletjs.com/) + OpenStreetMap
- 📡 Real-time location broadcasting via [Socket.io](https://socket.io/)
- 👥 Multi-user support — track multiple people simultaneously
- 🧹 Auto-removes a user's marker when they disconnect
- 📱 Fully responsive — works on desktop and mobile browsers

---

## 🗂 Project Structure

```
TRACKER/
├── app.js              # Express + Socket.io server
├── package.json        # Project metadata & dependencies
├── package-lock.json   # Locked dependency tree
├── views/
│   └── index.ejs       # Main HTML view (EJS template)
└── public/
    ├── css/
    │   └── style.css   # Full-screen map styles
    └── js/
        └── script.js   # Client-side geolocation + Socket.io + Leaflet
```

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18 or higher
- npm (comes with Node.js)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/TRACKER.git
cd TRACKER

# 2. Install dependencies
npm install

# 3. Start the server
node app.js
```

The server starts on **http://localhost:3000**.

Open it in your browser (it will ask for location permission). Open a second tab or a different device on the same network to see multi-user tracking in action.

> **Tip:** To test on a mobile device, find your machine's local IP (e.g. `192.168.x.x`) and visit `http://192.168.x.x:3000` on the device.

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| Server | Node.js + Express |
| Real-time | Socket.io |
| Templating | EJS |
| Map | Leaflet.js + OpenStreetMap |

---

## 📝 How It Works

1. When a user opens the page, the browser requests **Geolocation permission**.
2. If granted, the client watches the device position with `navigator.geolocation.watchPosition` and emits a `send-location` event to the server via Socket.io.
3. The server receives the coordinates and **broadcasts** a `recieve-location` event to all connected clients, including the sender's socket ID.
4. Each client adds or updates a **Leaflet marker** for that socket ID on the map.
5. On disconnect, the server emits `user-disconnected` and each client removes the corresponding marker.

---
