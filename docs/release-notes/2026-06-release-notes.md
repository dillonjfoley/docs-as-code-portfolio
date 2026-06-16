# June 2026 release notes

These release notes describe new features, improvements, and fixes added to SensorHub Cloud in June 2026.

## Release date

June 2026

## Summary

This release improves gateway setup, alert rule management, sensor data search, and API error messages.

The main changes include:

* A new gateway setup flow.
* Better alert rule testing.
* More filters for sensor readings.
* Clearer API error responses.
* Dashboard performance improvements.
* Fixes for sensor status and user invite issues.

## New features

### Gateway setup guide

SensorHub Cloud now includes a guided setup flow for new gateways.

The setup guide helps users:

* Add a gateway ID.
* Choose a location.
* Select a connection type.
* Confirm that the gateway is online.
* Add sensors after the gateway connects.

This change makes gateway setup easier for new users.

### Alert rule test button

Users can now send a test alert from the alert rule page.

Use the test button to confirm that alert messages are delivered before the rule is used in the field.

A test alert checks message delivery only. It does not create a real sensor alert.

### Sensor reading filters

The sensor readings page now includes more filters.

Users can filter readings by:

* Location
* Gateway
* Sensor
* Sensor type
* Date range
* Alert status

These filters make it easier to find readings for reports and troubleshooting.

### API request ID shown in the dashboard

API request IDs are now easier to find when an API error occurs.

When an API request fails, SensorHub Cloud shows the request ID in the error details.

Support may ask for this request ID when troubleshooting an API issue.

## Improvements

### Faster dashboard loading

The dashboard now loads faster for accounts with many sensors.

This improvement helps large accounts view device health, active alerts, and recent readings with less delay.

### Clearer gateway status messages

Gateway status messages now give more detail.

For example, instead of only showing **Offline**, SensorHub Cloud may show:

* **Offline: No recent check-in**
* **Offline: Network connection lost**
* **Warning: Weak signal**
* **Pending: Waiting for first connection**

These messages help users understand what to check next.

### Improved alert rule labels

Alert rule fields now use clearer labels.

For example:

| Old label | New label       |
| --------- | --------------- |
| Threshold | Alert value     |
| Duration  | Alert delay     |
| Contacts  | Recipients      |
| Method    | Delivery method |

These label changes make the alert setup flow easier to understand.

### Better empty states

Several pages now show clearer messages when no data is available.

For example, if a sensor has no readings, SensorHub Cloud now explains possible reasons, such as:

* The sensor has not reported yet.
* The date range has no readings.
* The sensor may be assigned to another location.
* The gateway may be offline.

## API changes

### New query parameter for readings

The `GET /readings` endpoint now supports the `type` query parameter.

Use `type` to filter readings by sensor type.

Example:

```bash
curl "https://api.sensorhub.example.com/v1/readings?type=temperature&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Accept: application/json"
```

Common values include:

* `temperature`
* `humidity`
* `water`
* `door`
* `pressure`
* `battery`

For more information, see [Retrieve sensor readings](../api/sensor-readings-endpoint.md).

### Improved API error messages

API error messages now include more helpful text.

Example:

```json
{
  "error": {
    "code": "invalid_parameter",
    "message": "The startTime value must use ISO 8601 format.",
    "requestId": "req_20491"
  }
}
```

For more information, see [API error codes](../api/error-codes.md).

### No breaking changes

This release does not include breaking API changes.

Existing API integrations should continue to work without updates.

## Fixed issues

### Gateway status did not always update after restart

Fixed an issue where a gateway could stay marked as **Offline** for several minutes after it reconnected.

Gateway status now updates sooner after a restart.

### User invite email could be delayed

Fixed an issue where some user invite emails were delayed.

Invite emails should now send more reliably.

### Alert history showed duplicate entries

Fixed an issue where some alert history entries appeared more than once.

This issue only affected the alert history view. It did not send duplicate alert messages.

### Sensor battery value sometimes showed as blank

Fixed an issue where the sensor battery field could appear blank even when the sensor reported battery data.

### Date range filter used local time inconsistently

Fixed an issue where date range filters could show different results based on the user's local time zone.

Date range filters now use clearer start and end times.

## Known issues

### Cellular gateways may take longer to reconnect

Some cellular gateways may take longer to reconnect after a power loss.

If a cellular gateway does not reconnect after 15 minutes:

1. Check the gateway power.
2. Check the antenna.
3. Move the gateway near a stronger signal area.
4. Restart the gateway.

For more help, see [Troubleshoot an offline gateway](../troubleshooting/gateway-offline.md).

### Large exports may take longer to complete

Accounts with many sensors may see longer wait times when exporting large date ranges.

To reduce export time:

* Use a shorter date range.
* Filter by location.
* Filter by sensor type.
* Export during lower-use hours.

## Documentation updates

The following documentation was updated for this release:

* [Quickstart: Set up SensorHub Cloud](../getting-started/quickstart.md)
* [Connect a gateway to SensorHub Cloud](../getting-started/connect-a-gateway.md)
* [Configure alert rules](../admin/configure-alert-rules.md)
* [Retrieve sensor readings](../api/sensor-readings-endpoint.md)
* [API error codes](../api/error-codes.md)
* [Troubleshoot an offline gateway](../troubleshooting/gateway-offline.md)
* [Troubleshoot missing sensor data](../troubleshooting/missing-sensor-data.md)

## Recommended actions

After this release, administrators should:

1. Review gateway status messages for offline gateways.
2. Test important alert rules.
3. Review user invites that are still pending.
4. Update API integrations if they can use the new `type` filter.
5. Share the updated troubleshooting articles with support teams.

## Support

If you need help with this release, contact SensorHub Cloud support.

When reporting an issue, include:

* Your account name.
* The affected location.
* The gateway ID or sensor ID, if available.
* The date and time the issue happened.
* The API `requestId`, if the issue is API-related.

Do not send passwords or API keys to support.
