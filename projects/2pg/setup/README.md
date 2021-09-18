---
description: How to setup 2PG for local development.
---

# Setup

This guide will show you how to setup 2PG, and the Dashboard for local development.

{% embed url="https://www.youtube.com/watch?v=rYpR0CiEGgk" caption="" %}

{% hint style="info" %}
The written guide below is more up-to-date, and is mainly command based.
{% endhint %}

## Developing with 2PG

The **Bot** project is used for managing data for the bot, and contains the API, which by default serves the built dashboard files on `http://localhost:3000`. It is used as a foundation for the Website project.

{% embed url="https://github.com/twopg/bot" caption="" %}

The **Dashboard** project is used for _customizing_ the actual website and dashboard. It uses Angular, which is a front-end framework that makes navigation seem fast and responsive.

{% embed url="https://github.com/twopg/dashboard" caption="" %}

## Requirements

{% embed url="https://www.mongodb.com/try/download/community" caption="MongoDB Community Server" %}

{% embed url="https://git-scm.com/" caption="Git CLI" %}

## API Setup

### Clone the Repository

The Bot project requires cloning, which basically downloads the project from GitHub. This can be done with the Git CLI.

```text
git clone https://github.com/twopg/bot.git
cd bot
```

{% hint style="info" %}
Node modules are not downloaded with the cloned project and need to be installed manually.
{% endhint %}

### Install Modules

Node modules need to be installed, specified in **package.json**, and **package-lock.json**. Make sure the terminal is at the root director of the project. All you need to do is type a simple command and it will all be done for you.

```text
npm i
```

### Configure Environment Variables

Create a`.env`file in the root project directory. This file is used to securely store private data. See the link below for the up to date template for the `.env` file. _\*\*_

See the link below for a `.env` file template. It contains an explanation to what each environment file does, and why they are used.

{% page-ref page="config.md" %}

{% hint style="warning" %}
**.env** should not be saved with Git. This would expose all of your tokens. By default, this file is added to **.gitignore**, which means Git should not commit this file.
{% endhint %}

### Start the API

If everything is setup correctly, you can start the project with this command.

```text
npm start
```

{% hint style="info" %}
Make sure the `mongod` process is running. The database needs to be online for the app to fully function.
{% endhint %}

By default the API runs on port 3000. You can confirm it is online by connecting to `http://localhost:3000`, in your browser URL bar.

## Website Setup

After the Bot is setup, the website follows a very similar setup, but with a different project URL.

```text
git clone https://github.com/twopg/dashboard.git
cd dashboard
npm i
npm start
```

{% hint style="info" %}
You may also need the Angular CLI to be globally installed to serve the website. This can be done with `npm i -g @angular/cli`
{% endhint %}

## Privileged Intents

The **Server Members Intent** needs to be enabled for 2PG to perform many functions including: reaction roles, guild member events, and more.

![Intents that 2PG uses](../../../.gitbook/assets/image%20%2813%29.png)

## Redirect URIs

**One last thing**...  
Redirect URIs are used for allowing Discord OAuth2 to function correctly. These can also be found in the [Discord Developer Portal](https://discord.com/developers).

![Redirect URIs for Local Development](../../../.gitbook/assets/image%20%2825%29.png)

![Redirect URIs that 2PG.xyz Uses](../../../.gitbook/assets/image%20%284%29.png)

