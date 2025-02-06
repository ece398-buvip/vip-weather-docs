# Overview

The website is written using the Next.js web development framework, primarily using the typescript language. Primarily, the website is designed to be a showcase of what a client can do with the data available at the API. Currently, the Weather Station website is available at:

[weather.jacobsimeone.net](https://weather.jacobsimeone.net)

# Maintenance Mode

The website has a "maintenance mode" feature that is enabled by the presence of a `under-maintenance.txt` file in the root website directory (`/website` in the repository). 

When a request to the server is made, a check is performed to determine if this file exists. If the file exists, a maintenance mode page is displayed. 

A maintenance log feature is also available through the presence of a file called `maintenance.log`. The contents of this file will be parsed line-by-line and displayed as a maintenance log. It is recommended to use this format:

```txt
[2025-01-24T14:00:00-06:00] Log entry 3
[2024-12-02T10:30:00-06:00] Log entry 2
[2024-11-21T14:00:00-06:00] Log entry 1
```