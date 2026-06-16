# API error codes

Use this article to understand SensorHub API error codes and how to fix common API problems.

When an API request fails, SensorHub Cloud returns an HTTP status code and an error response.

## Error response format

Most API errors use this format:

```json
{
  "error": {
    "code": "invalid_parameter",
    "message": "The startTime value must use ISO 8601 format.",
    "requestId": "req_20491"
  }
}
```

## Error response fields

| Field       | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| `code`      | A short error code that describes the problem.               |
| `message`   | A short explanation of what went wrong.                      |
| `requestId` | A unique ID for the request. Support may ask for this value. |

## HTTP status codes

The SensorHub API uses standard HTTP status codes.

| Status code                 | Meaning                                      | Common cause                                             |
| --------------------------- | -------------------------------------------- | -------------------------------------------------------- |
| `200 OK`                    | The request worked.                          | The request was valid.                                   |
| `201 Created`               | The item was created.                        | A new item was created successfully.                     |
| `400 Bad Request`           | The request is not valid.                    | A required value is missing or a parameter is wrong.     |
| `401 Unauthorized`          | The request is not authenticated.            | The API key is missing or invalid.                       |
| `403 Forbidden`             | The request is not allowed.                  | The API key does not have access.                        |
| `404 Not Found`             | The item was not found.                      | The sensor, gateway, location, or alert does not exist.  |
| `409 Conflict`              | The request conflicts with an existing item. | An item already exists or cannot be changed right now.   |
| `429 Too Many Requests`     | Too many requests were sent.                 | The rate limit was reached.                              |
| `500 Internal Server Error` | Something went wrong in SensorHub Cloud.     | An unexpected server error occurred.                     |
| `503 Service Unavailable`   | The service is not available.                | The API is under maintenance or temporarily unavailable. |

## Common error codes

| Error code            | Status code | Meaning                                                 | How to fix it                                  |
| --------------------- | ----------- | ------------------------------------------------------- | ---------------------------------------------- |
| `missing_api_key`     | `401`       | The request does not include an API key.                | Add the `Authorization` header.                |
| `invalid_api_key`     | `401`       | The API key is not valid.                               | Check the API key and try again.               |
| `expired_api_key`     | `401`       | The API key has expired.                                | Create a new API key.                          |
| `access_denied`       | `403`       | The API key does not have access to the requested data. | Check the key permissions and location access. |
| `invalid_request`     | `400`       | The request is not formatted correctly.                 | Check the request URL, headers, and body.      |
| `missing_parameter`   | `400`       | A required parameter is missing.                        | Add the missing parameter.                     |
| `invalid_parameter`   | `400`       | A parameter has the wrong value or format.              | Check the parameter name, value, and format.   |
| `invalid_date_range`  | `400`       | The start date and end date are not valid.              | Make sure `startTime` is before `endTime`.     |
| `not_found`           | `404`       | The requested item does not exist.                      | Check the ID and try again.                    |
| `duplicate_resource`  | `409`       | An item with the same value already exists.             | Use a different name or ID.                    |
| `rate_limit_exceeded` | `429`       | Too many requests were sent.                            | Wait before sending more requests.             |
| `server_error`        | `500`       | SensorHub Cloud had an unexpected error.                | Try again later.                               |
| `service_unavailable` | `503`       | The API is temporarily unavailable.                     | Wait and try again later.                      |

## Authentication errors

Authentication errors happen when the API cannot confirm who is making the request.

### Missing API key

This error happens when the request does not include the `Authorization` header.

Example response:

```json
{
  "error": {
    "code": "missing_api_key",
    "message": "The Authorization header is required.",
    "requestId": "req_10291"
  }
}
```

To fix this error:

1. Add the `Authorization` header.
2. Make sure the header uses `Bearer`.
3. Send the request again.

Example:

```bash
curl "https://api.sensorhub.example.com/v1/readings" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Accept: application/json"
```

### Invalid API key

This error happens when the API key is wrong, deleted, or not recognized.

Example response:

```json
{
  "error": {
    "code": "invalid_api_key",
    "message": "The API key is not valid.",
    "requestId": "req_10292"
  }
}
```

To fix this error:

1. Check that the API key was copied correctly.
2. Check for extra spaces before or after the key.
3. Make sure the key is active.
4. Create a new key if needed.

### Expired API key

This error happens when the API key is past its expiration date.

Example response:

```json
{
  "error": {
    "code": "expired_api_key",
    "message": "The API key has expired.",
    "requestId": "req_10294"
  }
}
```

To fix this error:

1. Sign in to SensorHub Cloud.
2. Go to **Admin**.
3. Select **API access**.
4. Create a new API key.
5. Update your application to use the new key.
6. Disable or delete the old key.

## Permission errors

Permission errors happen when the API key is valid, but it does not have access to the requested data.

### Access denied

This error happens when the API key does not have the right access level or location access.

Example response:

```json
{
  "error": {
    "code": "access_denied",
    "message": "The API key does not have access to this location.",
    "requestId": "req_10293"
  }
}
```

To fix this error:

1. Check the API key access level.
2. Check the API key location access.
3. Make sure the requested sensor, gateway, or location belongs to the account.
4. Ask an owner or administrator to update the key if needed.

## Request errors

Request errors happen when the API cannot understand the request.

### Invalid request

This error happens when the request URL, headers, or body are not formatted correctly.

Example response:

```json
{
  "error": {
    "code": "invalid_request",
    "message": "The request could not be processed.",
    "requestId": "req_20490"
  }
}
```

To fix this error:

1. Check the request URL.
2. Check the HTTP method.
3. Check the request headers.
4. Check the request body, if the request has one.
5. Send the request again.

### Missing parameter

This error happens when a required parameter is missing.

Example response:

```json
{
  "error": {
    "code": "missing_parameter",
    "message": "The sensorId parameter is required.",
    "requestId": "req_20492"
  }
}
```

To fix this error:

1. Read the error message.
2. Add the missing parameter.
3. Send the request again.

### Invalid parameter

This error happens when a parameter has the wrong value or format.

Example response:

```json
{
  "error": {
    "code": "invalid_parameter",
    "message": "The startTime value must use ISO 8601 format.",
    "requestId": "req_20491"
  }
}
```

To fix this error:

1. Check the parameter name.
2. Check the parameter value.
3. Make sure dates use ISO 8601 format.
4. Make sure numbers do not include letters or symbols.
5. Send the request again.

## Date range errors

Date range errors happen when `startTime` and `endTime` are not valid.

### Invalid date range

This error happens when the start time is after the end time.

Example response:

```json
{
  "error": {
    "code": "invalid_date_range",
    "message": "startTime must be before endTime.",
    "requestId": "req_20493"
  }
}
```

To fix this error:

1. Check the `startTime` value.
2. Check the `endTime` value.
3. Make sure `startTime` is before `endTime`.
4. Make sure both values use UTC time.

Correct format:

```text
2026-06-12T15:42:00Z
```

## Not found errors

Not found errors happen when the requested item does not exist or cannot be found.

### Item not found

This error can happen when a sensor, gateway, location, alert, or reading ID is wrong.

Example response:

```json
{
  "error": {
    "code": "not_found",
    "message": "The requested sensor was not found.",
    "requestId": "req_30501"
  }
}
```

To fix this error:

1. Check the ID in the request.
2. Make sure the item still exists.
3. Make sure the item belongs to your account.
4. Make sure the API key has access to the item.

## Conflict errors

Conflict errors happen when the request cannot be completed because of an existing item or current state.

### Duplicate resource

This error happens when you try to create an item that already exists.

Example response:

```json
{
  "error": {
    "code": "duplicate_resource",
    "message": "A location with this name already exists.",
    "requestId": "req_40901"
  }
}
```

To fix this error:

1. Check whether the item already exists.
2. Use a different name or ID.
3. Update the existing item instead of creating a new one, if needed.

## Rate limit errors

Rate limit errors happen when too many API requests are sent in a short time.

### Rate limit exceeded

This error happens when the request limit is reached.

Example response:

```json
{
  "error": {
    "code": "rate_limit_exceeded",
    "message": "Too many requests. Try again later.",
    "requestId": "req_42901"
  }
}
```

To fix this error:

1. Wait before sending more requests.
2. Reduce how often your application sends requests.
3. Use filters to request only the data you need.
4. Use pagination instead of repeated large requests.
5. Avoid retrying failed requests too quickly.

## Server errors

Server errors happen when SensorHub Cloud cannot complete the request.

### Server error

This error means something unexpected happened in SensorHub Cloud.

Example response:

```json
{
  "error": {
    "code": "server_error",
    "message": "An unexpected error occurred.",
    "requestId": "req_50001"
  }
}
```

To fix this error:

1. Wait a short time.
2. Send the request again.
3. If the error continues, contact support.
4. Include the `requestId` when you contact support.

### Service unavailable

This error means the API is temporarily unavailable.

Example response:

```json
{
  "error": {
    "code": "service_unavailable",
    "message": "The API is temporarily unavailable.",
    "requestId": "req_50301"
  }
}
```

To fix this error:

1. Wait and try again later.
2. Check for planned maintenance.
3. Contact support if the problem continues.

## How to use the request ID

Each error response includes a `requestId`.

Example:

```text
req_20491
```

Save the `requestId` when you report an issue to support.

The request ID helps support find the failed request in system logs.

When contacting support, include:

* The `requestId`.
* The date and time of the request.
* The endpoint you called.
* The HTTP status code.
* The error code.
* A short description of what you were trying to do.

Do not send your API key to support.

## Troubleshooting checklist

Use this checklist when an API request fails.

* [ ] Check the full request URL.
* [ ] Check the HTTP method.
* [ ] Check the `Authorization` header.
* [ ] Check that the API key is active.
* [ ] Check the API key access level.
* [ ] Check location access.
* [ ] Check query parameter names.
* [ ] Check query parameter values.
* [ ] Check date and time format.
* [ ] Check whether the item ID is correct.
* [ ] Save the `requestId`.

