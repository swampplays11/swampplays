---
description: 'Setup 6PG, a Discord bot maker, for local development.'
---

# Setup

## Local Development

### Setup API

This will download 6PG from GitHub, install packages, then start the API on port 3000.

```text
git clone https://github.com/theadamjr/6pg.git
cd 6pg
npm i
npm start
```

### Setup Dashboard

This will download the 6PG Dashboard, install packages, then start the website on port 4200. The dashboard project is only intended to be used for local development.

```text
git clone https://github.com/theadamjr/6pg-dashboard.git
cd 6pg-dashboard
npm i
npm start
```

### Configure .env

{% page-ref page="config.md" %}

## Setup Redirect URIs

In the [Discord Developer Portal](https://discord.com/developers), make the your Redirect URIs are set according to your setup.

{% tabs %}
{% tab title="Developement" %}
![Development Redirect URIs](../../../.gitbook/assets/image%20%281%29.png)
{% endtab %}

{% tab title="Production" %}
![Development Redirect URIs](../../../.gitbook/assets/image%20%286%29.png)
{% endtab %}
{% endtabs %}

