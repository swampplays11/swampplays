---
description: A full guide to customizing 2PG.
---

# Customize

2PG can be customized, for your bot's needs. This guide goes in depth to show you how to customize your multipurpose Discord bot.

## Bot on Discord

### **How do I add commands?**

{% embed url="https://www.youtube.com/watch?v=9QtFdxpVqIc%3Flist%3DPLGfT2ttRbfixMStpAhPD4pKBQN9wjJmbP" %}

### **How do I change the default prefix?**

By default, the 2PG prefix is '`.`'. This can be changed in the file below. Simply change the `prefix = '.';` line.

{% embed url="https://github.com/twopg/Bot/blob/stable/src/data/models/guild.ts" caption="" %}

![2PG ping command](../../.gitbook/assets/image%20%2817%29.png)

### How do I customize the bot status?

In the file linked below, change the activity accordingly - `await bot.user?.setActivity('Your custom status');`

{% embed url="https://github.com/twopg/Bot/blob/stable/src/services/handlers/ready.handler.ts" caption="ready-handler.ts" %}

![Example of 2PG&apos;s status](../../.gitbook/assets/image%20%2814%29.png)

