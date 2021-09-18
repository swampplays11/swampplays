---
description: Solutions to common 1PG errors.
---

# Error Help

## { "message":`"You Shall Not Pass" }`

The **Server Members Intent** needs to be enabled for 1PG to perform many functions including: guild member events, and more. It is also used for the music player. This can be enabled in the [Discord Developer Portal](https://discord.com/developers).

![1PG Privilaged Intents](../../.gitbook/assets/image%20%2813%29%20%281%29.png)

## `SyntaxError: Unexpected token =`

```text
on = '';
     ^
SyntaxError: Unexpected token =
```

**Solution**: NodeJS v14 is required for this syntax

## `TypeError: Cannot read property 'access_token' of undefined`

```text
  let token = access['access_token'],
                    ^
  TypeError: Cannot read property 'access_token' of undefined
```

**Solution**: Use [twopg/oauth](https://twopg.github.io/oauth) instead of disco-oauth.

