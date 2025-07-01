# Palaemon Control Node

The **Palaemon Control Node** is the central command interface for managing field-deployed devices running the Palaemon emergency communication system. It is designed to support:

* Live map tracking of GPS-enabled field units
* Real-time device connectivity via Tailscale
* Push-to-Talk communication to each device
* SOS alert reception with location info
* Seamless UI for emergency coordination

---

## 🚀 Getting Started

### 🔧 Prerequisites

* Node.js >= 18
* Python >= 3.10
* Tailscale installed on backend host

### 🖥️ Frontend Setup (React + Vite + Chakra UI)

```bash
cd app/frontend
npm install
npm run dev
```

Runs at: [http://localhost:5173](http://localhost:5173)

### 🧠 Backend Setup (FastAPI)

```bash
cd app/backend
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

Runs at: [http://localhost:8000](http://localhost:8000)

---

## 🧭 Features

### Map View

Displays live locations of all field devices using their reported GPS data.

### Device List

Shows a full list of Tailscale-connected devices, their IPs, hostnames, and statuses (online/offline).

### Device Page

Each device has a dedicated view with:

* Large Push-to-Talk button
* Device status info
* Location trace

### Broadcast

Send voice packets to all online field devices simultaneously.

### SOS Alerts

Instantly receive and locate any SOS sent from field devices.

---

## 📁 Project Structure

```
app/
├── backend/        # FastAPI backend
└── frontend/       # React frontend (Vite + Chakra UI)
    └── src/
        ├── pages/              # UI pages: MainPage, DevicePage, etc.
        ├── components/         # DeviceCard, BroadcastButton, etc.
        ├── hooks/              # useOnlinePeers, useGeolocation, etc.
        └── App.tsx, main.tsx   # Root files
```

---

## 🔐 Notes

* All networking runs over Tailscale for end-to-end secure mesh.
* Field devices must call the `/location` endpoint regularly to be shown on the map.
* `voice_sender.py` is used to stream audio packets to a device IP.

---

## 🧪 Testing

To simulate field devices:

* Manually post GPS data to `/location`
* Use `curl` to send SOS
* Simulate online/offline status via Tailscale

---

## 📜 License

MIT License — use, adapt, and deploy freely.

---

## 🧠 Author

**Matt Mitchell / VentrisOdin**
This repo: [palaemon\_controlnode\_main](https://github.com/VentrisOdin/palaemon_controlnode_main)

For field-side device software, see: [palaemon\_fielddevice\_main](https://github.com/VentrisOdin/palaemon_fielddevice_main)

---

> "For when the world burns — Palaemon answers."
