# Overview

The Bradley Weather Station web API allows access to weather data collected from the Weather Station. The API is written in Typescript and ran using the Node.js javascript runtime and express.js library. 

Logically, API also acts as the orchestrator between the database, and consumers of the contained data. The API must be installed on the same server as the redis database. The API runs on port `27500`. (The port can be changed by altering source code)

```mermaid
---
title: Logical Block Diagram
---
graph LR
    c[Client]
    r[Redis Db]
    a[API]

    subgraph "Web Server"
    r --> a
    a --> r
    end
    c -->|HTTP GET| a
```

```mermaid
---
title: Client Requesting Data
---
sequenceDiagram
    Client->>API: HTTP GET Request: /api/envdata
    API->>Redis: Request to read data from database
    Redis->>API: Return weather data to API
    API->>Client: Return JSON weather data to client
```

# Requesting Data

Data is requested from the API over a HTTP(S) GET request. The API returns data in the JSON format. Supported endpoints are:

| Endpoint | Supported Methods |
| --- | --- |
| /api/envdata | GET |

## Data Format

The format data from each endpoint is returned in, as well as the contents of the data.

### GET /api/envdata

Data is returned in JSON.

Example:
```json
{
    "weatherData": [
    {
      "timestamp": "1738773402798-0", 
      "temp_c": "3.38", 
      "humid_prcnt": "50.42",
      "pressure_kpa": "100.27",
      "is_raining": "0",
      "light_level": "SUNNY"
    },

    // ...

    ]
}
```

The root object: The `weatherData` array, contains the following members:

| Key | Description
| --- |  --- |
| timestamp | `unix-timestamp-ms`-`sample-num`, Timestamp when sample was taken |
| temp_c | Ambient air temperature, in degrees celsius |
| humid_prcnt | Relative humidity, 0-100% |
| pressure_kpa | Pressure, in kilo-Pascals |
| is_raining | If rain was detected at timestamp. 0 or 1 |
| light_level | Current estimated light level (SUNNY/DARK) |

# Posting Data

Posting data is a privileged operation that is manually added by administrators. Keys submitted by users are checked against a file in the api directory: `api.keys`, which contains hashes of user api keys manually added by admins. 

Users sending data to the `/api/envdata` endpoint over HTTP(S) POST request must define the "Authorization" HTTP header and populate the value with a pre-determined key, provisioned by administrators. The data is posted in the following format:

```JSON
{
    "timestamp" : 123456789,
    "temp_c": 34.32,
    "humid_prcnt": 53.32,
    "pressure_kpa": 99.83,
    "is_raining": 1,
    "light_level": "SUNNY"
}
```

Note that the `light_level` and `is_raining` values are the same here as in the GET request description.

!!! danger "Security"
    It is the responsibility of admins to follow security guidelines listed in this documentation, and other sources, to protect privileged operations like posting data. 