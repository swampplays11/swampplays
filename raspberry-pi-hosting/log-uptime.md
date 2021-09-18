---
description: >-
  Log Your Website Uptime for Free! In this guide, we will use Statuspage to log
  the response time of our app every 3 minutes.
---

# Log Uptime

## In this guide

#### We will ping our website, every 3 minutes, and send the response time to [Statuspage](https://statuspage.io) so we can log it in a graph.

### What we will use

This guide assumes you have access to bash commands, and is intended for use with a Linux web server.

Bash is available on Linux and MacOS. You can also use [Windows Subsystem for Windows](https://www.google.com/search?q=windows%20subsystem%20for%20linux), if you are using Windows.

* **Statuspage API** - for sending data to.
* **Bash** - for the script.
* **Cron** - for task scheduling.

![Example Response Time - Discord \(05/06/21\)](../.gitbook/assets/image%20%2847%29.png)

## 0 - Make a Status Page

Go to [statuspage.io](https://statuspage.io), and follow the instructions to make a status page. This is a prerequisite for the following steps.

## 1 - Create System Metrics

## 2 - Send Metrics to Status Page API

{% code title="metrics.sh" %}
```bash
curl https://api.statuspage.io/v1/pages/{page_id}/metrics/{metric_id} \
  -H "Authorization: OAuth your-api-key-goes-here" \
  -X PATCH \
  -d "metric[name]=string"
```
{% endcode %}

{% embed url="https://developer.statuspage.io/\#operation/patchPagesPageIdMetricsMetricId" %}

## 3 - Automate Script Execution

Execute this script every 5 minutes.

```bash
*/5 * * * * <path>/metrics.sh
```

{% hint style="warning" %}
Guide incomplete.
{% endhint %}

## Further Reading

### How can I know my app goes offline?

#### If you have Cloudflare

If you are using Cloudflare, and the website times out due to no connection with the website server, you may see around[ 30,000ms](https://accord.statuspage.io/#month) in the graph.

[More info on Cloudflare Error 522](https://support.cloudflare.com/hc/en-us/articles/115003011431-Troubleshooting-Cloudflare-5XX-errors#522error).

![An example from the accord.app status page. ](../.gitbook/assets/image%20%2848%29.png)

#### Else, if you don't have Cloudflare

If you don't have Cloudflare, or a similar service, you may see holes in the graph. This indicates that no response was sent to the Statuspage API in time. This may be because the web page is taking longer than 30,000ms to load.

