# Broadlink Server Runtime Log

This snapshot shows the backend workflow of the Broadlink control layer:
- configuration loading
- IR code loading
- Flask server lifecycle
- Broadlink discovery + authentication
- IR command execution (VOL_UP / VOL_DOWN)

<br>

![Broadlink Server Log](https://raw.githubusercontent.com/AdBusterOfficial/Adbuster--WinApp/main/broadlink_server_log.png)


### Message Types in Broadlink Server Log

Each log entry contains two fields:

{"time": "...", "msg": "..."}

The **msg** field describes the specific event that occurred inside the Broadlink–Flask backend.  
Below is a breakdown of all message types visible in the log and what they represent.

---

### 1. Server Start / Stop Events
- **"Flask server started on port 5000"** — The HTTP backend is running and listening on port 5000.  
- **"Stopping server..."** — A shutdown request was triggered.  
- **"Flask server stopped"** — The server was successfully terminated.

These messages confirm that the Flask lifecycle is functioning correctly.

---

### 2. Configuration Handling
- **"Configuration loaded from config.json"** — Broadlink settings (IP, MAC, port, etc.) were successfully loaded.  
- **"IR codes loaded from ir_codes.json"** — IR command definitions (VOL_UP, VOL_DOWN, etc.) were loaded.  
- **"Configuration saved to config.json"** — Updated settings were written back to disk.

This confirms that the backend correctly manages its configuration files.

---

### 3. Application Initialization
- **"Application started. Set IP/MAC/port, then START SERVER."**  
  The application is ready but requires Broadlink parameters before starting the server.

---

### 4. Network Scanning & Device Discovery
- **"Scanning network for Broadlink device..."** — The backend is searching for a Broadlink device on the local network.  
- **"Broadlink device found: 0x5f36"** — A Broadlink device was detected (model code shown).

These messages confirm that device discovery is working.

---

### 5. Device Connection
- **"Connected to Broadlink (discover + auth)."**  
  The backend successfully:
  - discovered the device  
  - performed handshake  
  - authenticated  
  - initialized the IR session  

This means the device is ready to receive IR commands.

---

### 6. IR Command Execution
- **"Command: VOL_UP, time: ..."**  
- **"Command: VOL_DOWN, time: ..."**

Each entry indicates that the backend transmitted an IR command to the Broadlink device.  
These messages confirm that the control layer is functioning and capable of executing AdBuster/CEPA decisions.

---

### Summary

The `msg` field provides a clear, step‑by‑step trace of the Broadlink control layer:

- configuration loading  
- server lifecycle  
- device discovery  
- authentication  
- IR command execution  

Together, these logs confirm that the Broadlink backend is operational and able to execute volume‑control commands triggered by AdBuster.

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**
