# SensorHub Cloud overview
SensorHub Cloud is a SaaS platform for connecting wireless sensor gateways, monitoring device health, configuring alert rules, and retrieving sensor data through a REST API.

Organizations use SensorHub Cloud to view sensor activity from one central location. The platform helps operations teams monitor equipment, track environmental conditions, respond to alerts, and troubleshoot sensor connectivity issues.

## What you can do with a SensorHub Cloud
Use SensorHub Cloud to:

- Add and organize wireless sensor gateways.
- View sensor readings from connected devices.
- Monitor gateway and sensor health.
- Configure alert rules for readings outside expected ranges.
- Manage users, roles, and account access.
- Retrieve sensor data through the SensorHub API.
- Review event history for troubleshooting and audits.

### Common use cases
SensorHub Cloud can support several monitoring workflows, including:

- **Facility monitoring** — Track temperature, humidity, water detection, door activity, or equipment status across a building.
- **Cold storage monitoring** — Monitor refrigerated areas and receive alerts when temperatures move outside the allowed range.
- **Equipment monitoring** — Watch for changes in vibration, runtime, current, or other equipment conditions.
- **Remote site monitoring** — Use gateways to collect sensor data from locations that are not staffed full-time.
- **Compliance reporting** — Review historical readings and event logs when documentation is required.

## How SensorHub Cloud works
SensorHub Cloud uses gateways, sensors, and cloud-based software to collect and display sensor data.

At a high level, the workflow is:

1. A wireless sensor records a reading.
2. The sensor sends the reading to a nearby gateway.
3. The gateway sends the reading to SensorHub Cloud.
4. SensorHub Cloud stores the reading and updates the dashboard.
5. Alert rules check the reading against configured conditions.
6. Users view the reading, receive alerts, or retrieve the data through the API.

## Key Concepts
### Sensor
A sensor is a device that records a specific type of reading, such as temperature, humidity, water presence, pressure, or door activity.

Each sensor belongs to an account and can be assigned to a location, gateway, or group.

### Gateway
A gateway receives wireless data from sensors and sends that data to SensorHub Cloud.

A gateway must be connected to the internet before it can send readings to the cloud. Depending on the gateway model, the connection may use Ethernet, Wi-Fi, or cellular service.

### Reading 
A reading is a data point reported by a sensor.

A reading usually includes:

- Sensor ID
- Reading value
- Unit of measure
- Timestamp
- Gateway ID
- Signal strength
- Battery status, when available

### Alert rule
An alert rule defines when SensorHub Cloud should notify users about a condition.

For example, an alert rule can notify a facilities team when a temperature sensor reports a value above 40°F for more than 10 minutes.

### User role
A user role controls what a person can view or change in SensorHub Cloud.

Common roles include:

- **Owner** — Manages account settings, billing, users, gateways, sensors, and alerts.
- **Administrator** — Manages users, devices, locations, and alert rules.
- **Operator** — Views dashboards, responds to alerts, and reviews sensor data.
- **Viewer** — Views dashboards and reports but cannot change settings.

## Main areas of the application
### Dashboard
The dashboard shows current device status, recent readings, active alerts, and gateway connectivity.

Use the dashboard to quickly check whether monitored locations are operating normally.

### Devices
The Devices area lists gateways and sensors assigned to the account.

Use this area to add gateways, review sensor status, check battery level, and confirm when each device last reported data.

### Alerts
The Alerts area shows active and historical alerts.

Use this area to configure alert rules, assign notification recipients, and review alert activity.

### Users and roles
The Users area allows account owners and administrators to invite users, assign roles, and remove access when needed.

### API access
The API area provides access to developer settings, including API keys and integration details.

Use the SensorHub API to retrieve readings, check device status, or connect SensorHub Cloud data to another system.

### Example Workflow
A facilities administrator wants to monitor a walk-in cooler.

The administrator completes the following tasks:

1. Creates a location named Kitchen Cooler.
2. Connects a gateway to SensorHub Cloud.
3. Adds temperature sensors to the location.
4. Confirms that the sensors are reporting readings.
5. Creates an alert rule for temperatures above 40°F.
6. Adds the facilities team as alert recipients.
7. Reviews readings from the dashboard or API.

After setup is complete, SensorHub Cloud monitors the cooler and sends an alert if the temperature moves outside the configured range.

## Who uses SensorHub Cloud?
SensorHub Cloud is designed for several types of users.

| User type | Common tasks|
| :-- | :-- |
| Account owner | Manage account settings, users, roles, and subscription details. |
| Administrator | Add devices, configure locations, manage alert rules, and invite users. |
| Operator | Monitor dashboards, respond to alerts, and review device health. |
| Support technician | Troubleshoot gateways, sensors, missing data, and alert behavior. |
| Developer | Use the REST API to retrieve sensor readings and integrate data with other systems. |

## Before you begin
Before setting up SensorHub Cloud, make sure you have:

- Access to a SensorHub Cloud account.
- Permission to add gateways and sensors.
- A supported gateway.
- One or more compatible wireless sensors.
- Internet access for the gateway.
- Location names or site details for organizing devices.
- Alert requirements, such as threshold values and notification recipients.
