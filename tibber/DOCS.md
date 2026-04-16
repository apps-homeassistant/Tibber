# Tibber Add-on

View Tibber consumption data in Home Assistant: log in with your Tibber account and see the last year of data from the Tibber API.

## MQTT settings

The app can auto-detect MQTT connection details from Home Assistant Supervisor.

When the app starts with missing MQTT fields, it will keep using the detected Supervisor values and also save those missing values back into the add-on options so they become visible in the Home Assistant add-on configuration UI.

If needed, you can optionally set `mqtt_host`, `mqtt_port`, `mqtt_user`, and `mqtt_password` in the app configuration to override those detected values. Leave any field empty to keep using the Supervisor-provided value.
