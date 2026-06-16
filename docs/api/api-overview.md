# API overview

Use the SensorHub API to retrieve sensor readings, check device status, and connect SensorHub Cloud data to other systems.

The SensorHub API is a REST API. It uses standard HTTP methods, JSON request and response bodies, and API key authentication.

## Base URL

All API requests use the following base URL:

```text
https://api.sensorhub.example.com/v1
```

For example, the full URL for sensor readings is:

```text
https://api.sensorhub.example.com/v1/readings
```

## Common use cases

You can use the SensorHub API to:

* Retrieve sensor readings.
* Check gateway and sensor status.
* Send sensor data to another system.
* Build custom dashboards.
* Create reports from sensor history.
* Connect SensorHub Cloud to a ticketing, monitoring, or business system.

## Data format

The SensorHub API sends and receives data in JSON format.

Include this header with requests that send JSON:

```http
Content-Type: application/json
```

Most API responses also return JSON:

```http
Content-Type: application/json
```

## Authentication

The SensorHub API uses API keys.

Send your API key in the `Authorization` header with each request.

```http
Authorization: Bearer YOUR_API_KEY
```

Example:

```bash
curl https://api.sensorhub.example.com/v1/readings \
  -H "Authorization: Bearer YOUR_API_KEY"
```

Do not share your API key. Anyone with your API key may be able to access your SensorHub Cloud data.

For setup steps, see [Authenticate with the SensorHub API](authentication.md).

## HTTP methods

The SensorHub API uses standard HTTP methods.

| Method   | Use                     |
| -------- | ----------------------- |
| `GET`    | Retrieve data.          |
| `POST`   | Create a new item.      |
| `PATCH`  | Update part of an item. |
| `DELETE` | Delete an item.         |

This documentation sample focuses on `GET` requests for sensor readings.

## Common endpoints

| Endpoint     | Description               |
| ------------ | ------------------------- |
| `/readings`  | Retrieve sensor readings. |
| `/sensors`   | Retrieve sensor details.  |
| `/gateways`  | Retrieve gateway details. |
| `/locations` | Retrieve locations.       |
| `/alerts`    | Retrieve alert history.   |

## Example request

The following example retrieves the latest sensor readings.

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
    }
  ],
  "pagination": {
    "limit": 10,
    "nextCursor": "eyJwYWdlIjoyfQ"
  }
}
```

## Request headers

Most requests use these headers.

| Header          | Required                 | Description                                  |
| --------------- | ------------------------ | -------------------------------------------- |
| `Authorization` | Yes                      | Sends your API key.                          |
| `Accept`        | No                       | Tells the API to return JSON.                |
| `Content-Type`  | For requests with a body | Tells the API that the request body is JSON. |

## Query parameters

Some endpoints support query parameters.

Query parameters are added to the end of a URL after a question mark.

Example:

```text
/readings?sensorId=sns_2481&limit=10
```

Common query parameters include:

| Parameter    | Description                                 |
| ------------ | ------------------------------------------- |
| `sensorId`   | Filters results by sensor.                  |
| `gatewayId`  | Filters results by gateway.                 |
| `locationId` | Filters results by location.                |
| `startTime`  | Returns readings after this date and time.  |
| `endTime`    | Returns readings before this date and time. |
| `limit`      | Sets the number of results to return.       |
| `cursor`     | Gets the next page of results.              |

## Dates and times

The SensorHub API uses UTC time.

Dates and times use ISO 8601 format.

Example:

```text
2026-06-12T15:42:00Z
```

In this format:

* `2026-06-12` is the date.
* `T` separates the date and time.
* `15:42:00` is the time.
* `Z` means the time is in UTC.

## Pagination

Some requests may return many results.

When this happens, the API returns one page of results at a time.

The response includes a `nextCursor` value when more results are available.

Example:

```json
{
  "pagination": {
    "limit": 10,
    "nextCursor": "eyJwYWdlIjoyfQ"
  }
}
```

To get the next page, send another request with the `cursor` value.

```bash
curl "https://api.sensorhub.example.com/v1/readings?limit=10&cursor=eyJwYWdlIjoyfQ" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

If `nextCursor` is `null`, there are no more results.

## Rate limits

The SensorHub API limits how many requests you can send in a short time.

The default limit is:

```text
600 requests per minute
```

If you send too many requests, the API returns a `429 Too Many Requests` error.

When this happens, wait before sending more requests.

## Status codes

The SensorHub API uses HTTP status codes to show whether a request worked.

| Status code                 | Meaning                                                              |
| --------------------------- | -------------------------------------------------------------------- |
| `200 OK`                    | The request worked.                                                  |
| `201 Created`               | The item was created.                                                |
| `400 Bad Request`           | The request is missing required information or has an invalid value. |
| `401 Unauthorized`          | The API key is missing or invalid.                                   |
| `403 Forbidden`             | The API key does not have access to the requested data.              |
| `404 Not Found`             | The requested item was not found.                                    |
| `429 Too Many Requests`     | Too many requests were sent.                                         |
| `500 Internal Server Error` | Something went wrong in SensorHub Cloud.                             |

For more information, see [API error codes](error-codes.md).

## Error response format

When an error happens, the API returns an error object.

Example:

```json
{
  "error": {
    "code": "invalid_request",
    "message": "The sensorId value is not valid.",
    "requestId": "req_78945"
  }
}
```

| Field       | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| `code`      | A short error code.                                          |
| `message`   | A short explanation of the problem.                          |
| `requestId` | A unique ID for the request. Support may ask for this value. |

## API versioning

The current API version is `v1`.

The version appears in the base URL:

```text
https://api.sensorhub.example.com/v1
```

If a new version is released, the version number in the URL may change.

Example:

```text
https://api.sensorhub.example.com/v2
```

## Security tips

Follow these tips when you use the SensorHub API:

* Store API keys in a secure place.
* Do not add API keys to public code.
* Do not share API keys in email or chat.
* Create a separate API key for each integration.
* Remove API keys that are no longer used.
* Give each API key only the access it needs.

## Next steps

To start using the API, see:

* [Authenticate with the SensorHub API](authentication.md)
* [Retrieve sensor readings](sensor-readings-endpoint.md)
* [API error codes](error-codes.md)
