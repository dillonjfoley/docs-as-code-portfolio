# Connect a gateway to SensorHub Cloud
Use this article to connect a gateway to SensorHub Cloud.

A gateway collects readings from nearby sensors. Then it sends those readings to SensorHub Cloud through the internet.

## Before you begin
Make sure you have:

- A SensorHub Cloud account.
- Permission to add gateways.
- A supported gateway.
- The gateway ID.
- Power for the gateway.
- Internet access for the gateway.
- A location already created in SensorHub Cloud.

The gateway ID is printed on the gateway label. It may also appear as a QR code.

## Choose a gateway location
Place the gateway where it can reach both the internet and the sensors.

For best results:

- Place the gateway near the sensors.
- Keep the gateway away from large metal objects.
- Do not place the gateway inside a metal cabinet.
- Keep the gateway dry.
- Keep the gateway away from strong heat.
- Place the gateway where the power cord will not be pulled loose.

If the gateway uses Wi-Fi, place it where the Wi-Fi signal is strong.

### Gateway connection options
SensorHub Cloud supports three common gateway connection types.

| Connection type | Description | 
| :-- | :-- |
| Ethernet | Uses a network cable. This is usually the most stable option |
| Wi-Fi | Uses a wireless internet connection. This is useful when no network cable is available |
| Cellular | Uses a cellular network. This is useful for remote sites. | 

Your gateway may not support every connection type. 

## Gateway set up steps

### Step 1: Add the gateway in SensorHub Cloud
1. Sign in to SensorHub Cloud.
2. From the left menu, select **Devices.**
3. Select **Gateways.**
4. Select **Add gateway.**
5. Enter the gateway ID.
6. Enter a gateway name.
7. Choose a location.
8. Select **Add gateway.**

The gateway is added to the account.

The gateway may show **Offline** until it is powered on and connected to the internet.

### Step 2: Connect a gateway to power
1. Connect a power adapter to the gateway.
2. Plug the power adapter into an outlet.
3. Wait for the power light to turn on.

The gateway may take a few minutes to start.

Do not unplug the gateway while it is starting. 

### Step 3: Connect the gateway to the internet
Use the steps for your connection type.

#### Option A: Connect the Ethernet
Use Ethernet when a network cable is available.

1. Connect one end of the Ethernet cable to the gateway.
2. Connect the other end to a network port.
3. Wait for the network light to turn on.
4. In SensorHub Cloud, open **Devices.**
5. Select **Gateways.**
6. Find the gateway.
7. Check the gateway status.

The gateway status should change to Online.

This may take a few minutes.

#### Option B: Connect with Wi-Fi
Use Wi-Fi when the gateway is not near a network port.

1. Connect the gateway to power.
2. Wait for the power light to turn on.
3. Press the Setup button on the gateway.
4. On your computer or phone, open the Wi-Fi settings.
5. Connect to the gateway setup network.
6. Open the setup page shown in the gateway guide.
7. Choose your Wi-Fi network.
8. Enter the Wi-Fi password.
9. Select **Connect.**
10. Wait for the gateway to restart.
11. In SensorHub Cloud, check the gateway status.

The gateway status should change to Online.

If the gateway does not connect, check the Wi-Fi name and password.

#### Option C: Connect with cellular
Use cellular for remote sites or places without local internet.

1. Make sure the cellular antenna is attached.
2. Place the gateway where the cellular signal is strong.
3. Connect the gateway to power.
4. Wait for the cellular light to turn on.
5. In SensorHub Cloud, open **Devices.**
6. Select **Gateways.**
7. Find the gateway.
8. Check the gateway status.

The gateway status should change to **Online.**

If the gateway stays offline, move it closer to a window or a stronger signal area.

### Step 4: Confirm the gateway is online
To confirm the gateway is online:

1. In SensorHub Cloud, open **Devices.**
2. Select **Gateways.**
3. Find the gateway.
4. Check the **Status** column.

The gateway is connected when the status shows Online.

You can also open the gateway details page to check:

- Last check-in time
- Connection type
- Signal strength
- Firmware version
- Assigned location

### Step 5: Add sensors to the gateway location
After the gateway is online, add sensors to the same location.

To add a sensor:

1. From the left menu, select **Devices.**
2. Select **Sensors.**
3. Select **Add sensor.**
4. Enter the sensor ID.
5. Choose the sensor type.
6. Choose the same location as the gateway.
7. Select **Add sensor.**

After the sensor is added, wait for the first reading to appear.

### Step 6: Check for sensor readings
To check for readings:

1. From the left menu, select **Dashboard.**
2. Choose the gateway location.
3. Find the sensor.
4. Check the **Last reading** value.
5. Check the **Last check-in** time.

A recent reading means the sensor data is reaching SensorHub Cloud.
