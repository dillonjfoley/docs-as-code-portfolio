# Troubleshoot an offline gateway

Use this article to troubleshoot a gateway that shows **Offline** in SensorHub Cloud.

A gateway is offline when SensorHub Cloud has not received a check-in from the gateway for a set amount of time.

## What offline means

A gateway may show **Offline** when:

* The gateway has no power.
* The gateway lost internet access.
* The gateway was moved out of range.
* The gateway ID was entered incorrectly.
* The local network is blocking the connection.
* The gateway is restarting or updating.
* The gateway has a hardware issue.

When a gateway is offline, sensors may still record readings, but SensorHub Cloud may not receive them until the gateway reconnects.

## Before you begin

Make sure you have:

* Access to SensorHub Cloud.
* Permission to view gateways.
* Physical access to the gateway, if possible.
* The gateway ID.
* Access to the network, Wi-Fi, or cellular connection used by the gateway.

## Step 1: Confirm the gateway status

First, confirm that the correct gateway is offline.

1. Sign in to SensorHub Cloud.
2. From the left menu, select **Devices**.
3. Select **Gateways**.
4. Find the gateway.
5. Check the **Status** column.
6. Check the **Last check-in** time.

If the gateway checked in recently, refresh the page.

The status may take a few minutes to update.

## Step 2: Check the gateway ID

Make sure the gateway ID in SensorHub Cloud matches the ID printed on the gateway label.

To check the gateway ID:

1. Open the gateway details page in SensorHub Cloud.
2. Find the **Gateway ID** field.
3. Compare it to the ID on the gateway label.
4. If the ID is wrong, remove the incorrect gateway.
5. Add the gateway again with the correct ID.

An incorrect gateway ID can make the gateway appear offline even if the physical gateway is working.

## Step 3: Check power

Make sure the gateway has power.

1. Check that the power adapter is plugged into the gateway.
2. Check that the power adapter is plugged into an outlet.
3. Check that the outlet works.
4. Look for the power light on the gateway.
5. If the gateway is plugged into a power strip, make sure the power strip is turned on.

If there is no power light, try another outlet.

## Step 4: Restart the gateway

Restarting the gateway can fix short connection issues.

To restart the gateway:

1. Unplug the gateway from power.
2. Wait 30 seconds.
3. Plug the gateway back in.
4. Wait 5 minutes.
5. Refresh SensorHub Cloud.
6. Check the gateway status again.

Do not restart the gateway many times in a row. Give it time to reconnect.

## Step 5: Check the internet connection

The gateway must have internet access to send data to SensorHub Cloud.

Use the steps for your gateway connection type.

## Ethernet gateway

An Ethernet gateway uses a network cable.

To check an Ethernet connection:

1. Make sure the Ethernet cable is connected to the gateway.
2. Make sure the other end is connected to a network port.
3. Check the network light on the gateway.
4. Try a different Ethernet cable.
5. Try a different network port.
6. Ask your IT team if the network port is active.

If the network port is not active, the gateway cannot connect.

## Wi-Fi gateway

A Wi-Fi gateway uses a wireless network.

To check a Wi-Fi connection:

1. Make sure the Wi-Fi network is working.
2. Move the gateway closer to the Wi-Fi router.
3. Check that the Wi-Fi name is correct.
4. Check that the Wi-Fi password is correct.
5. Restart the gateway.
6. If needed, run Wi-Fi setup again.

A weak Wi-Fi signal can cause the gateway to go offline.

## Cellular gateway

A cellular gateway uses a cellular network.

To check a cellular connection:

1. Make sure the antenna is attached.
2. Move the gateway near a window.
3. Move the gateway away from metal walls or cabinets.
4. Check the cellular signal light.
5. Restart the gateway.
6. Wait a few minutes for the gateway to reconnect.

A cellular gateway may go offline if the signal is weak or the local network is down.

## Step 6: Check for network blocks

Some networks block device traffic.

Ask your IT team to check whether the gateway is allowed to connect to SensorHub Cloud.

Common network issues include:

* The network blocks unknown devices.
* The firewall blocks outbound traffic.
* The network requires a login page.
* The network requires device approval.
* The network port is disabled.
* The Wi-Fi network changed.

Gateways may not work on networks that require a web browser login page.

## Step 7: Check the gateway location

The gateway should be placed where it can keep a strong network connection.

For best results:

* Keep the gateway away from metal cabinets.
* Keep the gateway away from thick concrete walls.
* Keep the gateway away from high heat.
* Keep the gateway dry.
* Place the gateway where it has a strong Wi-Fi or cellular signal.
* Do not place the gateway where the power cord can be pulled loose.

If the gateway was recently moved, move it back to a known working location and check the status again.

## Step 8: Check for maintenance or updates

A gateway may go offline for a short time during a restart or firmware update.

To check for recent activity:

1. Open the gateway details page.
2. Check the **Event history** section.
3. Look for restart, update, or connection events.
4. Wait a few minutes if an update is in progress.

If the gateway does not come back online after 15 minutes, continue troubleshooting.

## Step 9: Check connected sensors

If the gateway is offline, sensors connected through that gateway may stop showing new readings.

To check affected sensors:

1. Open the gateway details page.
2. Select **Connected sensors**.
3. Review the sensor list.
4. Check the **Last reading** time for each sensor.

If all sensors stopped reporting at the same time, the gateway or network connection is likely the issue.

If only one sensor stopped reporting, see [Troubleshoot missing sensor data](missing-sensor-data.md).

## Step 10: Contact support

Contact support if the gateway is still offline after you complete the checks above.

Include this information:

* Gateway ID
* Gateway name
* Location name
* Connection type: Ethernet, Wi-Fi, or cellular
* Last check-in time
* Power light status
* Network light status
* Steps you already tried

Do not send passwords or API keys to support.

## Common causes and fixes

| Problem                           | Possible cause                | What to do                                      |
| --------------------------------- | ----------------------------- | ----------------------------------------------- |
| Gateway has no lights             | No power                      | Check the power adapter and outlet.             |
| Gateway shows offline after setup | Wrong gateway ID              | Compare the ID in SensorHub Cloud to the label. |
| Ethernet gateway is offline       | Bad cable or inactive port    | Try another cable or network port.              |
| Wi-Fi gateway is offline          | Weak signal or wrong password | Move the gateway closer or run setup again.     |
| Cellular gateway is offline       | Weak cellular signal          | Move the gateway near a window.                 |
| Gateway goes offline often        | Unstable network or power     | Check the outlet, cable, and network signal.    |
| Sensors stopped reporting         | Gateway is offline            | Restore the gateway connection first.           |

## Troubleshooting checklist

Use this checklist before contacting support.

* [ ] The gateway ID is correct.
* [ ] The gateway has power.
* [ ] The gateway was restarted.
* [ ] The internet connection was checked.
* [ ] The Ethernet cable, Wi-Fi, or cellular signal was checked.
* [ ] The gateway was moved away from metal or signal blockers.
* [ ] The local network was checked for blocks.
* [ ] The gateway details page was reviewed.
* [ ] The last check-in time was recorded.
* [ ] Affected sensors were reviewed.

