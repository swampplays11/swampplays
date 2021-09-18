---
description: >-
  This guide will show you how to setup your own Discord bot list, using the
  DBots project for development purposes.
---

# Setup

## Production

Deployment to Heroku can be done in a few clicks. Refer to the [.env setup](config.md) for an explanation of the different environment variables. This will deploy the actual [DBots API repo](https://github.com/dbots-co/api). You can change the URL to match your own.

{% page-ref page="config.md" %}

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/dbots-co/api)

## Development

The **API** \(application programming interface\) project is used for managing data for the Discord bot list. It is used as a foundation for the Website project.

{% embed url="https://github.com/DBots-co/API" caption="" %}

The **Website** project is used for _customizing_ the actual website. The website uses Angular, which is a front-end framework that makes the website seem fast and responsive.

{% embed url="https://github.com/DBots-co/Website" caption="" %}

### Requirements

{% embed url="https://www.mongodb.com/try/download/community" caption="MongoDB Community Server" %}

{% embed url="https://git-scm.com/" caption="Git CLI" %}

### API Setup

#### Clone the Repository

The API requires cloning, which basically downloads the project from GitHub. This can be done with the Git CLI.

```text
git clone https://github.com/dbots-co/api.git
cd api
```

{% hint style="info" %}
Node modules are not downloaded with the cloned project and need to be installed manually.
{% endhint %}

#### Install Modules

Node modules need to be installed, specified in **package.json**, and **package-lock.json**. Make sure the terminal is at the root director of the project. All you need to do is type a simple command and it will all be done for you.

```text
npm i
```

#### Configure Environment Variables

Create a`.env`file in the root project directory. This file is used to securely store private data. See the link below for the up to date template for the `.env` file. _\*\*_See the link below to setup the environment variables.

{% page-ref page="config.md" %}

#### Start the API

If everything is setup correctly, you can start the project with this command.

```text
npm start
```

{% hint style="info" %}
Make sure the `mongod` process is running. The database needs to be online for the app to fully function.
{% endhint %}

By default the API runs on port 3000. You can confirm it is online by connecting to `http://localhost:3000`, in your browser URL bar.

### Website Setup

After the API is setup, the website follows a very similar setup, but with a different project URL.

```text
git clone https://github.com/dbots-co/website.git
cd website
npm i
npm start
```

{% hint style="info" %}
You may also need the Angular CLI to be globally installed to serve the website. This can be done with `npm i -g @angular/cli`
{% endhint %}

### Enable Bot Intents

Enable both intents in the [Discord Developer Portal](https://discord.com/developers), to allow bots to appear on the website**,** and enable all functionality.

**Presence Intent** - used to show status of bot user on website \(i.e. online / offline etc.\)  
**Server Members Intent** - used to cache bot members in server to display them on the website.

![](../../../.gitbook/assets/image%20%2841%29.png)

### Set Redirect URIs

**One last thing**...  
Redirect URIs are used for allowing Discord OAuth2 to function correctly. These can also be found in the [Discord Developer Portal](https://discord.com/developers).

![Redirect URIs for Local Development](../../../.gitbook/assets/image%20%283%29.png)

![Redirect URIs that dbots.co Uses](../../../.gitbook/assets/image%20%2838%29.png)

