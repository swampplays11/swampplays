---
description: Learn how to customize DBots with this all-in-one customization guide.
---

# Customize

## Main Customization

### Configure Environment Files

Environment files allow you to configure global variables, specific to your website. It is easier to keep things like public keys, and specific URLs in one place, and this is what environment files are for.

**environment.ts** - used for development, by default  
**environment.prod.ts** - used for production, by default

{% embed url="https://github.com/DBots-co/Website/tree/stable/src/environments" caption="src/environments" %}

## Common Questions

### How do I change the logo?

Images can be changed with the [website repository](https://github.com/dbots-co/website). In the `assets/img` directory, all you need to do is replace the image content, while keeping the file names the same.

### How do I edit themes?

By default, the website uses the **Next Gen** theme. The process is the same as 2PG, as both website projects are quite similar. Make sure to edit the CSS variables to match your preferences.

{% embed url="https://github.com/DBots-co/Website/blob/stable/src/theme.scss" caption="theme.scss" %}

{% embed url="https://www.youtube.com/watch?v=9QtFdxpVqIc&list=PLGfT2ttRbfixMStpAhPD4pKBQN9wjJmbP&index=3" caption="" %}

