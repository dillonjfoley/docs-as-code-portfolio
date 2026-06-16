# Configure alert rules

Use this article to create and manage alert rules in SensorHub Cloud.

An alert rule tells SensorHub Cloud when to notify users about a problem. For example, an alert rule can send a message when a temperature is too high, a door is open too long, or a sensor stops reporting data.

## Before you begin

Make sure you have:

* A SensorHub Cloud account.
* Permission to create alert rules.
* At least one location.
* At least one gateway.
* At least one sensor.
* The email addresses or phone numbers for users who should get alerts.

Only owners and administrators can create or change alert rules.

## What is an alert rule?

An alert rule is a set of conditions.

The rule tells SensorHub Cloud:

* Which sensor to watch.
* What value is allowed.
* How long the value can stay outside the allowed range.
* Who should receive the alert.
* How the alert should be sent.

## Example alert rule

A temperature sensor is installed in a walk-in cooler.

The cooler should stay at or below 40°F.

You can create this rule:

Send an alert when the temperature is above 40°F for more than 10 minutes.

This helps the facilities team respond before food or equipment is damaged.

## Alert rule parts

Most alert rules include these parts:

| Rule part       | Description                                               |
| --------------- | --------------------------------------------------------- |
| Name            | The name of the alert rule.                               |
| Location        | The place or site the rule applies to.                    |
| Sensor          | The sensor the rule checks.                               |
| Condition       | The value that causes the alert.                          |
| Delay           | How long the condition must last before an alert is sent. |
| Recipients      | The users who receive the alert.                          |
| Delivery method | How the alert is sent.                                    |

## Common alert types

SensorHub Cloud supports several common alert types.

| Alert type            | Example                                      |
| --------------------- | -------------------------------------------- |
| High value            | Temperature is above 40°F.                   |
| Low value             | Temperature is below 32°F.                   |
| Open or closed status | Door is open for more than 5 minutes.        |
| No data               | Sensor has not reported data for 30 minutes. |
| Low battery           | Sensor battery is below 15%.                 |
| Weak signal           | Sensor signal is too weak.                   |

## Step 1: Open alert rules

To open alert rules:

1. Sign in to SensorHub Cloud.
2. From the left menu, select **Alerts**.
3. Select **Alert rules**.

The alert rules page shows all rules for your account.

## Step 2: Create a new rule

To create a new rule:

1. Select **Create rule**.
2. Enter a rule name.
3. Choose a location.
4. Choose a sensor or sensor group.
5. Select **Next**.

Use a clear rule name.

Good rule names include:

* Walk-In Cooler High Temperature
* Server Room High Humidity
* North Door Open Too Long
* Pump Station Sensor Offline

## Step 3: Choose the condition

The condition tells SensorHub Cloud what to check.

To choose a condition:

1. In the **Condition** field, choose the reading type.
2. Choose an operator.
3. Enter the value.
4. Choose the unit of measure.

Common operators include:

| Operator      | Meaning                              | Example                           |
| ------------- | ------------------------------------ | --------------------------------- |
| Greater than  | The reading is too high.             | Temperature is greater than 40°F. |
| Less than     | The reading is too low.              | Temperature is less than 32°F.    |
| Equal to      | The reading matches a value.         | Door status is Open.              |
| Not reporting | The sensor has stopped sending data. | No reading for 30 minutes.        |

## Step 4: Set the alert delay

The alert delay controls how long the condition must last before SensorHub Cloud sends an alert.

A delay can help prevent false alerts.

For example, a cooler door may open for a few minutes during normal use. You may not want an alert every time the door opens.

To set the delay:

1. In the **Delay** field, enter a number.
2. Choose a time unit.
3. Select **Next**.

Example delays:

| Alert type                 | Suggested delay |
| -------------------------- | --------------- |
| Cooler temperature is high | 10 minutes      |
| Door is open               | 5 minutes       |
| Sensor is not reporting    | 30 minutes      |
| Low battery                | No delay        |
| Weak signal                | 15 minutes      |

## Step 5: Add recipients

Recipients are the people who receive the alert.

To add recipients:

1. In the **Recipients** section, select **Add recipient**.
2. Enter a user name, email address, or phone number.
3. Choose a delivery method.
4. Select **Add**.

Common delivery methods include:

* Email
* Text message
* In-app notification

Add every person or team that should respond to the alert.

## Step 6: Choose alert actions

Alert actions tell SensorHub Cloud what to do when the rule is triggered.

Common actions include:

* Send an email.
* Send a text message.
* Create an in-app alert.
* Add the alert to the event history.

To choose alert actions:

1. In the **Actions** section, choose one or more actions.
2. Review the recipients for each action.
3. Select **Next**.

## Step 7: Review and save the rule

Before you save the rule, review each setting.

Check:

* Rule name
* Location
* Sensor or sensor group
* Condition
* Delay
* Recipients
* Delivery method
* Alert actions

To save the rule:

1. Select **Review**.
2. Check the rule details.
3. Select **Save rule**.

The rule is turned on by default.

## Step 8: Test the rule

After you save the rule, test it if you can do so safely.

To test the rule:

1. Open the alert rule.
2. Select **Test rule**.
3. Choose a test recipient.
4. Select **Send test alert**.
5. Confirm that the alert was received.

A test alert checks the message delivery. It does not mean the sensor has entered an alert condition.

Do not create a real alert condition if it could damage equipment, products, or property.

## Turn a rule on or off

You can turn a rule off without deleting it.

To turn a rule on or off:

1. From the left menu, select **Alerts**.
2. Select **Alert rules**.
3. Find the rule.
4. Use the **Status** switch to turn the rule on or off.

Turn off a rule when it is not needed for a short time.

For example, you may turn off a rule during planned maintenance.

## Edit an alert rule

To edit an alert rule:

1. From the left menu, select **Alerts**.
2. Select **Alert rules**.
3. Find the rule.
4. Select the rule name.
5. Select **Edit**.
6. Make your changes.
7. Select **Save**.

Changes apply to new alerts only. They do not change past alert history.

## Delete an alert rule

Delete a rule only when you no longer need it.

To delete an alert rule:

1. From the left menu, select **Alerts**.
2. Select **Alert rules**.
3. Find the rule.
4. Select the **More actions** menu.
5. Select **Delete rule**.
6. Review the warning message.
7. Select **Delete** to confirm.

Deleting a rule does not delete past alert history.

## Example: High temperature alert

This example creates an alert for a walk-in cooler.

| Setting         | Example value                   |
| --------------- | ------------------------------- |
| Rule name       | Walk-In Cooler High Temperature |
| Location        | Walk-In Cooler                  |
| Sensor          | Cooler Temperature 1            |
| Condition       | Temperature greater than 40°F   |
| Delay           | 10 minutes                      |
| Recipients      | Facilities Team                 |
| Delivery method | Email and text message          |

With this rule, SensorHub Cloud sends an alert if the cooler temperature stays above 40°F for 10 minutes.

## Example: Missing data alert

This example creates an alert when a sensor stops reporting.

| Setting         | Example value                    |
| --------------- | -------------------------------- |
| Rule name       | Server Room Sensor Not Reporting |
| Location        | Server Room                      |
| Sensor          | Server Room Temperature 1        |
| Condition       | No data received                 |
| Delay           | 30 minutes                       |
| Recipients      | IT Support                       |
| Delivery method | Email                            |

With this rule, SensorHub Cloud sends an alert if the sensor does not report data for 30 minutes.

## Best practices

Follow these best practices when you create alert rules:

* Use clear rule names.
* Set alert values that match your site rules.
* Use a delay to reduce false alerts.
* Add the users who can respond.
* Test alert delivery after setup.
* Review alert rules often.
* Turn off rules during planned maintenance.
* Do not send every alert to every user.

## Troubleshooting

### Alert was not sent

If an alert was not sent:

1. Make sure the alert rule is turned on.
2. Check the alert condition.
3. Check the alert delay.
4. Make sure the sensor has recent readings.
5. Make sure recipients were added.
6. Check the delivery method.

### Alert was sent too often

If an alert was sent too often:

1. Check the alert value.
2. Increase the alert delay.
3. Make sure the sensor is installed in the correct place.
4. Check for short events that do not need alerts.
5. Edit the rule if needed.

### User did not receive an alert

If a user did not receive an alert:

1. Check the user's email address or phone number.
2. Check the selected delivery method.
3. Ask the user to check their spam folder.
4. Make sure the user is listed as a recipient.
5. Send a test alert.

### Alert rule cannot be edited

If you cannot edit an alert rule:

1. Check your user role.
2. Make sure you have permission to manage alerts.
3. Ask an owner or administrator for help.

## Check your work

Use this checklist before you finish.

* [ ] The rule has a clear name.
* [ ] The correct location is selected.
* [ ] The correct sensor or sensor group is selected.
* [ ] The condition is correct.
* [ ] The alert delay is correct.
* [ ] Recipients are added.
* [ ] The delivery method is selected.
* [ ] The rule is turned on.
* [ ] A test alert was sent.
