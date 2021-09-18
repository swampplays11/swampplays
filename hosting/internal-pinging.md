---
description: >-
  Keep your apps alive with some hosting free providers, by preventing them to
  auto sleep after inactivity.
---

# Internal Pinging

{% embed url="https://www.youtube.com/watch?v=Ujpg8FQLg28" caption="" %}

## What is Internal Pinging?

Internal pinging is where the application, keeps itself alive usually at a certain interval, to stop them from sleeping. This is used to **stop apps sleeping** in free hosting services, which can allow for 24/7 hosting, given the right conditions.

* [x] Works on Heroku.com - \(until free dyno hours run out\)
* [x] Works on Glitch.com \(10 hours at a time\)

## 1. Install `node-fetch`

This package is used to send HTTP GET requests to a URL. You can use the package of your choice.

```bash
$ npm i -S node-fetch
```

## 2. Add the Script

This script will send a HTTP GET request to a Heroku app, every 5 minutes. In theory, this will keep it awake until the free dyno hours run out.

{% tabs %}
{% tab title="JavaScript" %}
{% code title="keep-alive.js" %}
```javascript
const fetch = require('node-fetch');

setInterval(() => fetch(`https://<your_app>.herokuapp.com`), 5 * 60 * 1000);
```
{% endcode %}
{% endtab %}

{% tab title="TypeScript" %}
{% code title="keep-alive.ts" %}
```typescript
import fetch from 'node-fetch';

setInterval(() => fetch(`https://<your_app>.herokuapp.com`), 5 * 60 * 1000);
```
{% endcode %}
{% endtab %}
{% endtabs %}

## 3. Connect Script to Main Application

Make sure to connect the script to the bottom of your main file \(e.g. `app.js`\), and it should do the rest.

{% tabs %}
{% tab title="JavaScript" %}
{% code title="keep-alive.js" %}
```javascript
require('./keep-alive');
```
{% endcode %}
{% endtab %}

{% tab title="TypeScript" %}
{% code title="app.ts" %}
```javascript
...
import './keep-alive';
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Now What?

Your application should stay online for longer, or 24/7, depending on your host.

## External Pinging

Unlike internal pinging, external pinging sends requests from the outside - from another application. For example, connecting to [2pg.xyz](https://2pg.xyz), from the browser, would count as an external ping. Doing this from the browser would keep a Heroku application alive, as it would prevent it from auto sleeping.

Below is an entire repository dedicated to this concept. It also works with multiple URLs, and logs when an app is kept alive.

{% hint style="warning" %}
This does not work for all free hosting providers, and could be against their TOS \(terms of service\).
{% endhint %}

{% embed url="https://github.com/theADAMJR/Auto-Ping/blob/master/app.js" caption="Advanced Example" %}

