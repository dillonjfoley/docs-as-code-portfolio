# Quickstart: Set up a SensorHub Cloud
Use this quickstart to set up a new SensorHub Cloud account, add your first location, connect a gateway, add sensors, and create an alert rule.

After you finish, you should be able to view sensor readings in the dashboard.

## Before you begin
Make sure you have:

- A SensorHub Cloud account.
- Permission to add devices and alert rules.
- A supported gateway.
- One or more wireless sensors.
- Internet access for the gateway.
- A location where the sensors will be installed.
- The names or email addresses of users who should get alerts.

## Setup steps
To start using SensorHub Cloud, complete these steps:

1. Sign in to SensorHub Cloud.
2. Create a location.
3. Connect a gateway.
4. Add sensors.
5. Check sensor readings.
6. Create an alert rule.
7. Add alert recipients.
8. Test the setup.

### Step 1: Sign in to SensorHub Cloud
1. Open SensorHub Cloud in your web browser.
2. Enter your email address and password.
3. Select **Sign in.**

If this is your first time signing in, you may be asked to set a new password.

### Step 2: Create a location
A location helps you organize gateways and sensors.

Examples of locations include:

- Main Warehouse
- Walk-In Cooler
- Server Room
- North Building
- Pump Station 2

To create a location:

1. From the left menu, select **Locations.**
2. Select **Add location.**
3. Enter a location name.
4. Optional: Enter a description.
5. Select **Save.**

The new location appears in the location list.

### Step 3: Connect a gateway
A gateway collects data from nearby sensors and sends it to SensorHub Cloud.

To connect a gateway:

1. From the left menu, select **Devices.**
2. Select **Gateways.**
3. Select **Add gateway.**
4. Enter the gateway ID.
5. Choose the location for the gateway.
6. Select **Add gateway.**
7. Connect the gateway to power.
8. Connect the gateway to the internet.

The gateway may take a few minutes to appear online.

To learn more, see Connect a gateway to SensorHub Cloud.

### Step 4: Add sensors
After the gateway is online, add sensors to the same location.

To add a sensor:

1. From the left menu, select **Devices.**
2. Select **Sensors.**
3. Select **Add sensor.**
4. Enter the sensor ID.
5. Choose the sensor type.
6. Choose the location.
7. Select **Add sensor.**

Repeat these steps for each sensor you want to add.

### Step 5: Check sensor readings
After you add a sensor, wait for the first reading to appear.

To check readings:

1. From the left menu, select **Dashboard.**
2. Select the location you created.
3. Find the sensor in the device list.
4. Check the **Last reading** value.
5. Check the **Last check-in** time.

The sensor is working if it shows a recent reading.

### Step 6: Create an alert rule
An alert rule specifies when SensorHub Cloud should notify users.

**Example:** Send an alert when a temperature sensor reports more than 40°F for 10 minutes.

To create an alert rule:

1. From the left menu, select **Alerts.**
2. Select **Alert rules.**
3. Select **Create rule.**
4. Enter a rule name.
5. Choose a location.
6. Choose a sensor or sensor group.
7. Choose a condition.
8. Enter the alert value.
9. Choose how long the condition must last before an alert is sent.
10. Select **Save.**

### Step 7: Add alert recipients
Alert recipients are the people who receive alert messages.

To add recipients:

1. Open the alert rule.
2. Go to **Recipients.**
3. Select **Add recipient.**
4. Enter the user name or email address.
5. Choose the alert method.
6. Select **Save.**

Common alert methods include:

- Email
- Text message
- In-app notification

### Step 8: Test the setup
After the gateway, sensors, and alert rule are set up, test the system.

To test the setup:

1. Confirm that the gateway shows **Online.**
2. Confirm that each sensor shows a recent reading.
3. Confirm that the alert rule is turned on.
4. Confirm that the correct users are listed as recipients.
5. Create a test condition, if safe to do so.
6. Check that the alert is sent.

Do not create a test condition that could damage equipment, products, or property.

#### Example setup
The following example shows a simple setup for a walk-in cooler.

| Item | Example value |
| :-- | :-- |
| Location | Walk-In Cooler |
| Gateway | Gateway-1042 | 
| Sensor type | Temperature | 
| Alert rule | Temperature above 40°F |
| Alert delay | 10 minutes |
| Alert recipients | Facilities team |

With this setup, SensorHub Cloud sends an alert if the cooler temperature stays above 40°F for 10 minutes.
