---
description: >-
  Log Your Website Uptime for Free! In this guide, we will use Statuspage to log
  the response time of our app every 3 minutes.
---

# Log Uptime

## In this guide...

#### We will ping our website, every 3 minutes, and send the response time to [Statuspage](https://statuspage.io) so we can log it in a graph.

![Example Response Time - Discord \(05/06/21\)](../.gitbook/assets/image%20%2847%29.png)

### How can I know if it goes offline?

#### If you have Cloudflare

If you are using Cloudflare, and the website times out due to no connection with the website server, you may see around[ 30,000ms](https://accord.statuspage.io/#month) in the graph.

[More info on Cloudflare Error 522](https://support.cloudflare.com/hc/en-us/articles/115003011431-Troubleshooting-Cloudflare-5XX-errors#522error).

![An example from the accord.app status page. ](../.gitbook/assets/image%20%2848%29.png)

#### Else if you don't have Cloudflare

If you don't have Cloudflare, or a similar service, you may see holes in the graph. This indicates that no response was sent to the Statuspage API in time. This may be because the web page is taking longer than 30,000ms to load.

