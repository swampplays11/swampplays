---
description: >-
  A guide on how to configure DBots - Discord bot list, for your projects needs,
  and an explanation on what each environment variable means.
---

# Config

## `.env`

Environment variables are used to configure your application. Variables are stored in `process.env` with Node.js. Create a `.env` file to get started.

### Template

{% tabs %}
{% tab title="Development" %}
This template would go in the root project folder, and is used for the main application.

Port 3000 is commonly used by many Node.js applications. Port 4200 is for the dashboard, running on an [Angular development server](./#website-setup).

{% code title=".env" %}
```javascript
API_URL="http://localhost:3000/api/v1"
BOT_TOKEN=""
BOT_ROLE_ID=""
CLIENT_ID=""
CLIENT_SECRET=""
DASHBOARD_URL="http://localhost:4200"
DEV_ROLE_ID=""
DOWNTIME_CHANNEL_ID=""
LOG_CHANNEL_ID=""
GUILD_ID=""
MONGO_URI="mongodb://localhost/DBots"
PORT="3000"
```
{% endcode %}
{% endtab %}

{% tab title="Testing" %}
This template would go in the **test/** directory, and is used for testing.

A different port is used for the API to allow the integration tests to work indendently from the main application. A separate database is also used for this purpose.

{% code title="test/.env" %}
```javascript
API_URL="http://localhost:3001/api/v1"
BOT_TOKEN=""
BOT_ROLE_ID=""
CLIENT_ID=""
CLIENT_SECRET=""
DASHBOARD_URL="http://localhost:4200"
DEV_ROLE_ID=""
DOWNTIME_CHANNEL_ID=""
LOG_CHANNEL_ID=""
GUILD_ID="test_guild_123"
MONGO_URI="mongodb://localhost/DBots-Test"
PORT="3001"
```
{% endcode %}
{% endtab %}
{% endtabs %}

### How do I get these values?

Most [required options](../../2pg/setup/config.md#required-variables) are linked below as DBots shares common `.env` values with 2PG.

{% page-ref page="../../2pg/setup/config.md" %}

## Optional Variables

### BOT\_ROLE\_ID

This is the ID of the role that bots get automatically, when they join your guild. The role is intended to restrict the bots to specific channels, and separate them from the possibly human members.

### DEV\_ROLE\_ID

The developer role ID is a role for developers that add a bot to the bot list, and is automatically given.

### DOWNTIME\_CHANNEL\_\_\_ID

This is the channel ID for the DBots bot to log bots that are offline for a specific amount of time. This helps notify the bot owner\(s\) to fix the problem.

### GUILD\_ID

This is ID of the guild for your support server. It's used to contain the bots. Without this guild, the bots would not be able to appear on the bot list.

### LOG\_CHANNEL\_ID

This is the channel ID for the bot logs. For example, if a user adds a bot to the list, or a bot gets approved/declined, it gets logged in this channel by the DBots bot.

