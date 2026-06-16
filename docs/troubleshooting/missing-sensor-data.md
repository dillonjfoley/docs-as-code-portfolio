# Troubleshoot missing sensor data

Use this article to troubleshoot a sensor that is not showing new readings in SensorHub Cloud.

A sensor may stop showing data when the sensor, gateway, network, or account setup has a problem.

## What missing sensor data means

Missing sensor data means SensorHub Cloud has not received a new reading from the sensor.

This can happen when:

* The sensor battery is low or dead.
* The sensor is too far from the gateway.
* The sensor is blocked by walls, metal, or equipment.
* The sensor is assigned to the wrong location.
* The gateway is offline.
* The sensor ID was entered incorrectly.
* The sensor reading interval is longer than expected.
* The sensor is damaged.

## Before you begin

Make sure you have:

* Access to SensorHub Cloud.
* Permission to view devices.
* The sensor ID.
* The gateway ID, if known.
* Physical access to the sensor, if possible.
* Physical access to the gateway, if possible.

## Step 1: Check the sensor status

First, check the sensor in SensorHub Cloud.

1. Sign in to SensorHub Cloud.
2. From the left menu, select **Devices**.
3. Select **Sensors**.
4. Find the sensor.
5. Check the **Status** column.
6. Check the **Last reading** time.
7. Check the **Last check-in** time.

If the last reading is recent, refresh the page.

The dashboard may take a few minutes to update.

## Step 2: Check the sensor ID

Make sure the sensor ID in SensorHub Cloud matches the ID printed on the sensor label.

To check the sensor ID:

1. Open the sensor details page.
2. Find the **Sensor ID** field.
3. Compare it to the ID on the sensor label.
4. If the ID is wrong, remove the incorrect sensor.
5. Add the sensor again with the correct ID.

An incorrect sensor ID can make the sensor appear missing even when the physical sensor is working.

## Step 3: Check the gateway status

Sensors send data through a gateway.

If the gateway is offline, SensorHub Cloud may not receive sensor readings.

To check the gateway:

1. From the left menu, select **Devices**.
2. Select **Gateways**.
3. Find the gateway for the sensor location.
4. Check the **Status** column.
5. Check the **Last check-in** time.

If the gateway shows **Offline**, fix the gateway first.

For more help, see [Troubleshoot an offline gateway](gateway-offline.md).

## Step 4: Check the sensor location

Make sure the sensor and gateway are assigned to the correct location.

To check the sensor location:

1. Open the sensor details page.
2. Find the **Location** field.
3. Confirm that the location is correct.
4. If the location is wrong, select **Edit**.
5. Choose the correct location.
6. Select **Save**.

If the sensor is assigned to the wrong location, it may not appear where users expect to see it.

## Step 5: Check the sensor battery

A sensor may stop reporting when the battery is low or dead.

To check the battery level:

1. Open the sensor details page.
2. Find the **Battery** field.
3. Review the battery level.
4. Replace the battery if the battery is low.

After replacing the battery, wait for the next reading.

Some sensors may need several minutes to report again.

## Step 6: Move the sensor closer to the gateway

A sensor may stop reporting if it is too far from the gateway.

To test the signal:

1. Move the sensor closer to the gateway.
2. Wait for the next reading interval.
3. Refresh SensorHub Cloud.
4. Check the **Last reading** time.

If the sensor reports after being moved closer, the original location may have a weak signal.

## Step 7: Check for signal blockers

Walls, metal, and equipment can block sensor signals.

Common signal blockers include:

* Metal cabinets
* Freezer walls
* Concrete walls
* Large machines
* Electrical panels
* Storage racks
* Elevators
* Thick doors

For best results:

* Place the sensor away from large metal objects.
* Keep the sensor within range of the gateway.
* Place the gateway in a central location.
* Avoid placing sensors inside sealed metal spaces.

## Step 8: Check the reading interval

Some sensors do not report every minute.

A sensor may report every few minutes, every 15 minutes, or on a set schedule.

To check the reading interval:

1. Open the sensor details page.
2. Find the **Reading interval** field.
3. Check how often the sensor should report.
4. Wait for the next expected reading.
5. Refresh the dashboard.

If the reading interval is 15 minutes, wait at least 15 minutes before deciding the sensor is not reporting.

## Step 9: Check sensor events

The sensor event history may show why data is missing.

To check sensor events:

1. Open the sensor details page.
2. Select **Event history**.
3. Look for recent events.

Common events include:

| Event           | Meaning                                      |
| --------------- | -------------------------------------------- |
| Low battery     | The sensor battery is low.                   |
| Missed check-in | The sensor did not report when expected.     |
| Weak signal     | The sensor signal is weak.                   |
| Sensor moved    | The sensor changed location or gateway path. |
| Gateway offline | The sensor gateway stopped checking in.      |

Use these events to decide what to check next.

## Step 10: Restart or reset the sensor

Some sensors can be restarted or reset.

Use this step only if your sensor model supports it.

To restart or reset the sensor:

1. Follow the sensor guide for your model.
2. Wait for the sensor to restart.
3. Wait for the next reading interval.
4. Refresh SensorHub Cloud.
5. Check the **Last reading** time.

Do not remove batteries or press reset buttons unless the sensor guide says it is safe to do so.

## Step 11: Check alert rules

If the issue was found because an alert did not work, check the alert rule.

To check the alert rule:

1. From the left menu, select **Alerts**.
2. Select **Alert rules**.
3. Open the rule for the sensor.
4. Confirm that the rule is turned on.
5. Confirm that the correct sensor is selected.
6. Confirm that the condition is correct.
7. Confirm that recipients are added.

A sensor can be reporting normally even if an alert rule is set up incorrectly.

For more help, see [Configure alert rules](../admin/configure-alert-rules.md).

## Step 12: Contact support

Contact support if the sensor still does not report data after you complete these checks.

Include this information:

* Sensor ID
* Sensor name
* Sensor type
* Location name
* Gateway ID
* Last reading time
* Battery level
* Signal strength
* Steps you already tried

Do not send passwords or API keys to support.

## Common causes and fixes

| Problem                                   | Possible cause               | What to do                                 |
| ----------------------------------------- | ---------------------------- | ------------------------------------------ |
| Sensor has no recent readings             | Sensor battery is dead       | Replace the battery.                       |
| Sensor stopped after gateway went offline | Gateway lost internet access | Restore the gateway connection.            |
| Sensor reports only when moved closer     | Weak signal                  | Move the sensor or gateway.                |
| Sensor does not appear in the dashboard   | Wrong location               | Assign the sensor to the correct location. |
| Sensor never reported data                | Wrong sensor ID              | Check the ID and add the sensor again.     |
| Sensor reports late                       | Long reading interval        | Wait for the next reading interval.        |
| Only one sensor is missing                | Sensor issue                 | Check battery, signal, and sensor ID.      |
| Many sensors are missing                  | Gateway or network issue     | Check the gateway first.                   |

## Example: Temperature sensor missing data

A temperature sensor in a walk-in cooler has not reported data for 45 minutes.

The technician checks:

1. The sensor status in SensorHub Cloud.
2. The last reading time.
3. The gateway status.
4. The sensor battery level.
5. The signal strength.
6. The sensor location.

The gateway is online, but the sensor battery is at 2%.

The technician replaces the battery and waits for the next reading.

The sensor starts reporting again.

## Troubleshooting checklist

Use this checklist before contacting support.

* [ ] The sensor ID is correct.
* [ ] The sensor is assigned to the correct location.
* [ ] The gateway is online.
* [ ] The sensor battery was checked.
* [ ] The sensor was moved closer to the gateway.
* [ ] Signal blockers were checked.
* [ ] The reading interval was checked.
* [ ] Sensor events were reviewed.
* [ ] Alert rules were checked, if needed.
* [ ] The last reading time was recorded.

