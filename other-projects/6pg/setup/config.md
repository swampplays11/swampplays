---
description: >-
  A guide on how to configure 6PG, a Discord bot maker, for your projects needs,
  and an explanation on what each environment variable means.
---

# Config

## .env Template

{% tabs %}
{% tab title="Development" %}
This template would go in the root project folder, and is used for the main application.

Port 3000 is commonly used by many Node.js applications. Port 4200 is for the dashboard, running on an [Angular development server](../../../projects/2pg/setup/#website-setup).

{% code title=".env" %}
```javascript
API_URL="http://localhost:3000/api"
CLIENT_ID="533947001578979328"
CLIENT_SECRET=""
DASHBOARD_URL="http://localhost:4200"
ENCRYPTION_KEY="something secure"
MONGO_URI="mongodb://localhost/6PG"
PORT=3000
```
{% endcode %}
{% endtab %}
{% endtabs %}

### How do I get these values?

Most [required options](../../../projects/2pg/setup/config.md#required-variables) are linked below as 6PG shares common `.env` values with 2PG.

{% page-ref page="../../../projects/2pg/setup/config.md" %}

## Required Variables

### ENCRYPTION\_KEY

This is used for encrypting and decrypting bot tokens in the database. Make sure you keep this value safe, as it can be used to retrieve bot tokens.

