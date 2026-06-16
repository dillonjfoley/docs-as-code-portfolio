# Retrieve sensor readings

Use the `GET /readings` endpoint to retrieve sensor readings from SensorHub Cloud.

A reading is one data point from a sensor. For example, a temperature sensor may send a reading of `38.7°F`.

## Endpoint

```http
GET /readings
```

## Base URL

```text
https://api.sensorhub.example.com/v1
```

## Full request URL

```text
https://api.sensorhub.example.com/v1/readings
```

## Authentication

This endpoint requires an API key.

Send the API key in the `Authorization` header.

```http
Authorization: Bearer YOUR_API_KEY
```

For setup steps, see [Authenticate with the SensorHub API](authentication.md).

## Request headers

| Header          | Required | Description                   |
| --------------- | -------- | ----------------------------- |
| `Authorization` | Yes      | Sends your API key.           |
| `Accept`        | No       | Tells the API to return JSON. |

## Query parameters

Use query parameters to filter the readings returned by the API.

| Parameter    | Type    | Required | Description                                                           |
| ------------ | ------- | -------- | --------------------------------------------------------------------- |
| `sensorId`   | String  | No       | Returns readings from one sensor.                                     |
| `gatewayId`  | String  | No       | Returns readings from sensors connected through one gateway.          |
| `locationId` | String  | No       | Returns readings from one location.                                   |
| `type`       | String  | No       | Returns readings by sensor type, such as `temperature` or `humidity`. |
| `startTime`  | String  | No       | Returns readings after this date and time.                            |
| `endTime`    | String  | No       | Returns readings before this date and time.                           |
| `limit`      | Integer | No       | Sets the number of readings to return.                                |
| `cursor`     | String  | No       | Gets the next page of readings.                                       |

## Date and time format

Use ISO 8601 format for `startTime` and `endTime`.

Example:

```text
2026-06-12T15:42:00Z
```

SensorHub Cloud uses UTC time for API requests and responses.

## Limit

The `limit` parameter controls how many readings are returned.

Default value:

```text
100
```

Maximum value:

```text
500
```

If you request more than `500` readings, the API returns `500`.

## Example request

This request retrieves the latest 10 readings.

```bash
curl "https://api.sensorhub.example.com/v1/readings?limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Accept: application/json"
```

## Example response

```json
{
  "data": [
    {
      "readingId": "rdg_1001",
      "sensorId": "sns_2481",
      "gatewayId": "gtw_1042",
      "locationId": "loc_3001",
      "type": "temperature",
      "value": 38.7,
      "unit": "F",
      "timestamp": "2026-06-12T15:42:00Z",
      "batteryPercent": 91,
      "signalStrength": -67
    },
    {
      "readingId": "rdg_1002",
      "sensorId": "sns_2482",
      "gatewayId": "gtw_1042",
      "locationId": "loc_3001",
      "type": "humidity",
      "value": 42.4,
      "unit": "%",
      "timestamp": "2026-06-12T15:41:30Z",
      "batteryPercent": 88,
      "signalStrength": -70
    }
  ],
  "pagination": {
    "limit": 10,
    "nextCursor": "eyJwYWdlIjoyfQ"
  }
}
```

## Response fields

| Field            | Type           | Description                                               |
| ---------------- | -------------- | --------------------------------------------------------- |
| `data`           | Array          | A list of sensor readings.                                |
| `readingId`      | String         | The unique ID for the reading.                            |
| `sensorId`       | String         | The unique ID for the sensor.                             |
| `gatewayId`      | String         | The unique ID for the gateway that sent the reading.      |
| `locationId`     | String         | The unique ID for the sensor location.                    |
| `type`           | String         | The type of reading, such as `temperature` or `humidity`. |
| `value`          | Number         | The reading value.                                        |
| `unit`           | String         | The unit of measure.                                      |
| `timestamp`      | String         | The date and time when the reading was recorded.          |
| `batteryPercent` | Integer        | The sensor battery level, shown as a percent.             |
| `signalStrength` | Integer        | The sensor signal strength.                               |
| `pagination`     | Object         | Information used to get more results.                     |
| `limit`          | Integer        | The number of readings requested.                         |
| `nextCursor`     | String or null | The cursor used to get the next page of results.          |

## Retrieve readings for one sensor

Use the `sensorId` parameter to retrieve readings for one sensor.

```bash
curl "https://api.sensorhub.example.com/v1/readings?sensorId=sns_2481&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Accept: application/json"
```

## Retrieve readings for one location

Use the `locationId` parameter to retrieve readings for one location.

```bash
curl "https://api.sensorhub.example.com/v1/readings?locationId=loc_3001&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Accept: application/json"
```

## Retrieve readings by date range

Use `startTime` and `endTime` to retrieve readings from a date range.

```bash
curl "https://api.sensorhub.example.com/v1/readings?sensorId=sns_2481&startTime=2026-06-12T00:00:00Z&endTime=2026-06-13T00:00:00Z" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Accept: application/json"
```

This request returns readings from sensor `sns_2481` between June 12, 2026 at 12:00 AM UTC and June 13, 2026 at 12:00 AM UTC.

## Retrieve readings by type

Use the `type` parameter to retrieve readings by sensor type.

```bash
curl "https://api.sensorhub.example.com/v1/readings?type=temperature&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Accept: application/json"
```

Common reading types include:

| Type          | Description                   |
| ------------- | ----------------------------- |
| `temperature` | Temperature readings.         |
| `humidity`    | Humidity readings.            |
| `water`       | Water detection readings.     |
| `door`        | Door open or closed readings. |
| `pressure`    | Pressure readings.            |
| `battery`     | Battery level readings.       |

## Pagination

The API may return only part of the full result set.

If more readings are available, the response includes a `nextCursor`.

Example:

```json
{
  "pagination": {
    "limit": 100,
    "nextCursor": "eyJwYWdlIjoyfQ"
  }
}
```

To get the next page, send another request with the `cursor` parameter.

```bash
curl "https://api.sensorhub.example.com/v1/readings?limit=100&cursor=eyJwYWdlIjoyfQ" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Accept: application/json"
```

If `nextCursor` is `null`, there are no more pages.

## Empty response

If no readings match the request, the API returns an empty `data` array.

Example:

```json
{
  "data": [],
  "pagination": {
    "limit": 100,
    "nextCursor": null
  }
}
```

This response does not always mean there is a problem.

It may mean:

* The sensor has no readings for the selected date range.
* The `sensorId` is wrong.
* The API key does not have access to the location.
* The sensor has not reported data yet.

## Status codes

| Status code                 | Meaning                                                 |
| --------------------------- | ------------------------------------------------------- |
| `200 OK`                    | The request worked.                                     |
| `400 Bad Request`           | A query parameter is missing or invalid.                |
| `401 Unauthorized`          | The API key is missing or invalid.                      |
| `403 Forbidden`             | The API key does not have access to the requested data. |
| `404 Not Found`             | The sensor, gateway, or location was not found.         |
| `429 Too Many Requests`     | Too many requests were sent.                            |
| `500 Internal Server Error` | Something went wrong in SensorHub Cloud.                |

## Error response

When an error happens, the API returns an error object.

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

## Common errors

| Error code            | Meaning                                       | How to fix it                                  |
| --------------------- | --------------------------------------------- | ---------------------------------------------- |
| `missing_api_key`     | The request does not include an API key.      | Add the `Authorization` header.                |
| `invalid_api_key`     | The API key is not valid.                     | Check the API key and try again.               |
| `invalid_parameter`   | A query parameter is not valid.               | Check the parameter name, value, and format.   |
| `access_denied`       | The API key does not have access to the data. | Check the key permissions and location access. |
| `not_found`           | The requested item does not exist.            | Check the sensor, gateway, or location ID.     |
| `rate_limit_exceeded` | Too many requests were sent.                  | Wait before sending more requests.             |

For more information, see [API error codes](error-codes.md).

## Best practices

Follow these best practices when you retrieve sensor readings:

* Use filters to limit the data returned.
* Use `startTime` and `endTime` for reports.
* Use `limit` to control response size.
* Use pagination when you need many readings.
* Store API keys in a secure place.
* Do not request data more often than needed.
* Save the `requestId` when reporting an API issue to support.

## Troubleshooting

### The response has no readings

If the response has no readings:

1. Check the `sensorId`, `gatewayId`, or `locationId`.
2. Check the date range.
3. Make sure the sensor has reported data.
4. Make sure the API key has access to the location.

### The request returns 401 Unauthorized

If the request returns `401 Unauthorized`:

1. Make sure the `Authorization` header is included.
2. Make sure the header uses `Bearer`.
3. Check that the API key is correct.
4. Make sure the API key is active.

### The request returns 400 Bad Request

If the request returns `400 Bad Request`:

1. Check each query parameter.
2. Make sure `startTime` and `endTime` use ISO 8601 format.
3. Make sure `limit` is a number.
4. Remove any unsupported parameters.
