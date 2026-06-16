# Authenticate with the SensorHub API

Use this article to create an API key and send authenticated requests to the SensorHub API.

The SensorHub API uses API keys. An API key is a secret value that allows another system to access SensorHub Cloud data.

## Before you begin

Make sure you have:

* A SensorHub Cloud account.
* Permission to manage API keys.
* Access to the system or application that will use the API.
* A clear reason for the API key, such as a dashboard, report, or integration.

Only owners and administrators can create API keys.

## How authentication works

Each API request must include an API key.

Send the API key in the `Authorization` header.

```http
Authorization: Bearer YOUR_API_KEY
```

Replace `YOUR_API_KEY` with your real API key.

Do not include the API key in the URL.

## Base URL

All API requests use this base URL:

```text
https://api.sensorhub.example.com/v1
```

Example request URL:

```text
https://api.sensorhub.example.com/v1/readings
```

## Step 1: Open API settings

To open API settings:

1. Sign in to SensorHub Cloud.
2. From the left menu, select **Admin**.
3. Select **API access**.

The API access page shows active API keys for your account.

## Step 2: Create an API key

To create an API key:

1. Select **Create API key**.
2. Enter a name for the key.
3. Choose the access level.
4. Optional: Choose the locations the key can access.
5. Optional: Set an expiration date.
6. Select **Create key**.

SensorHub Cloud creates the API key.

Copy the key and store it in a secure place.

You may not be able to view the full key again after you leave the page.

## API key names

Use a clear name for each API key.

Good API key names include:

* Reporting Dashboard
* Maintenance App Integration
* Cold Storage Data Export
* IT Monitoring System
* Test API Key

Avoid names that are too general, such as:

* Key 1
* Test
* API
* New Key

A clear name helps you know what each key is used for.

## Access levels

Choose the lowest access level the integration needs.

| Access level   | Description                                               |
| -------------- | --------------------------------------------------------- |
| Read-only      | Can retrieve data, such as readings, devices, and alerts. |
| Read and write | Can retrieve data and make changes.                       |
| Admin          | Can manage account-level API settings.                    |

For most reporting and dashboard tools, use **Read-only** access.

## Location access

You can limit an API key to certain locations.

For example, a key for a warehouse dashboard may only need access to the **Main Warehouse** location.

Limiting access helps protect your account.

## Step 3: Store the API key

Store the API key in a secure place.

Do not store an API key in:

* Public GitHub repositories.
* Front-end website code.
* Shared documents.
* Emails.
* Chat messages.
* Screenshots.

Use a secure secret manager when possible.

## Step 4: Send an authenticated request

To authenticate a request, include the API key in the `Authorization` header.

Example:

```bash
curl "https://api.sensorhub.example.com/v1/readings?limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Accept: application/json"
```

If the key is valid, the API returns a response.

Example response:

```json
{
  "data": [
    {
      "readingId": "rdg_1001",
      "sensorId": "sns_2481",
      "type": "temperature",
      "value": 38.7,
      "unit": "F",
      "timestamp": "2026-06-12T15:42:00Z"
    }
  ],
  "pagination": {
    "limit": 10,
    "nextCursor": null
  }
}
```

## Example: Use an environment variable

Do not type your API key directly into scripts.

Instead, store the key as an environment variable.

Example:

```bash
export SENSORHUB_API_KEY="YOUR_API_KEY"
```

Then use the environment variable in the request.

```bash
curl "https://api.sensorhub.example.com/v1/readings?limit=10" \
  -H "Authorization: Bearer $SENSORHUB_API_KEY" \
  -H "Accept: application/json"
```

This helps keep the API key out of your command history and code files.

## Example: JavaScript request

The following example uses JavaScript to request sensor readings.

```javascript
const apiKey = process.env.SENSORHUB_API_KEY;

async function getReadings() {
  const response = await fetch(
    "https://api.sensorhub.example.com/v1/readings?limit=10",
    {
      headers: {
        "Authorization": `Bearer ${apiKey}`,
        "Accept": "application/json"
      }
    }
  );

  if (!response.ok) {
    throw new Error(`Request failed: ${response.status}`);
  }

  return response.json();
}

getReadings()
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

## Successful authentication

A successful request returns a `200 OK` status code.

Example:

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

The response body contains the requested data.

## Authentication errors

If authentication fails, the API returns an error.

| Status code             | Meaning                                       | How to fix it                                              |
| ----------------------- | --------------------------------------------- | ---------------------------------------------------------- |
| `401 Unauthorized`      | The API key is missing or invalid.            | Check that the key is correct and included in the request. |
| `403 Forbidden`         | The API key does not have access to the data. | Check the key permissions and location access.             |
| `429 Too Many Requests` | Too many requests were sent.                  | Wait before sending more requests.                         |

## Missing API key error

If you do not send an API key, the API returns a `401 Unauthorized` error.

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

## Invalid API key error

If the API key is wrong, expired, or deleted, the API returns a `401 Unauthorized` error.

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

## Access denied error

If the API key does not have access to the requested data, the API returns a `403 Forbidden` error.

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

## Rotate an API key

Rotate an API key when you need to replace it with a new key.

You may need to rotate a key when:

* The key may have been shared.
* A team member no longer needs access.
* Your company requires regular key changes.
* An integration is moving from testing to production.

To rotate an API key:

1. Create a new API key.
2. Update your application to use the new key.
3. Test the application.
4. Disable the old key.
5. Delete the old key after you confirm it is no longer used.

## Disable an API key

Disable a key when you want to stop access for a short time.

To disable an API key:

1. Sign in to SensorHub Cloud.
2. From the left menu, select **Admin**.
3. Select **API access**.
4. Find the API key.
5. Select the **Status** switch.
6. Confirm that you want to disable the key.

Disabled keys cannot access the API.

## Delete an API key

Delete a key when it is no longer needed.

To delete an API key:

1. Sign in to SensorHub Cloud.
2. From the left menu, select **Admin**.
3. Select **API access**.
4. Find the API key.
5. Select the **More actions** menu.
6. Select **Delete key**.
7. Review the warning message.
8. Select **Delete** to confirm.

Deleting a key cannot be undone.

## Security best practices

Follow these best practices when you use API keys:

* Create a separate key for each integration.
* Use the lowest access level needed.
* Limit keys to only the needed locations.
* Store keys in a secure secret manager.
* Do not add keys to public code.
* Do not share keys in email or chat.
* Rotate keys on a regular schedule.
* Delete keys that are no longer used.

## Troubleshooting

### Request returns 401 Unauthorized

If a request returns `401 Unauthorized`:

1. Make sure the `Authorization` header is included.
2. Make sure the header uses the word `Bearer`.
3. Check that the API key is correct.
4. Make sure the key is active.
5. Check that the key has not expired.

### Request returns 403 Forbidden

If a request returns `403 Forbidden`:

1. Check the API key access level.
2. Check the key location access.
3. Make sure the requested sensor, gateway, or location belongs to the account.
4. Ask an owner or administrator to update the key if needed.

### Request works in one tool but not another

If the request works in one tool but not another:

1. Compare the full request URL.
2. Compare the request headers.
3. Check for extra spaces in the API key.
4. Make sure both tools use the same API key.
5. Send the request again.

## Check your work

Use this checklist before you finish.

* [ ] The API key has a clear name.
* [ ] The API key has the correct access level.
* [ ] The API key is limited to the correct locations.
* [ ] The API key is stored in a secure place.
* [ ] The request includes the `Authorization` header.
* [ ] The request uses `Bearer YOUR_API_KEY`.
* [ ] The test request returns a successful response.
