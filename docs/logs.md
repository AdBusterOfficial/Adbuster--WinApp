
# Runtime Logs – Broadlink Server

This snapshot shows the backend workflow of the Broadlink control layer:
- configuration loading (config.json)
- IR code loading (ir_codes.json)
- Flask server start/stop events
- Broadlink device discovery and authentication
- IR command execution (VOL_UP / VOL_DOWN)

These logs are useful for validating runtime stability, timing, and correct device reactions during prototype testing.

![Broadlink Server Log](broadlink_server_log.png)
