---
description: A guide to keep Rasberry Pi online 24/7.
---

# 24/7 Hosting

{% embed url="https://www.youtube.com/watch?v=FFGsDt0EMBE" %}

### Start on Startup

#### With PM2

This will save a PM2 script to boot at startup. This requires root permissions to execute.

```bash
pm2 startup | grep "sudo" | bash
```

#### With Crontab

This will add a system wide event to cron, a task scheduling process, to auto resurrect saved PM2 processes. This will apply for all system users.

```bash
crontab -e
# choose a text editor (i.e. nano)
```

Add the line: `@reboot pm2 resurrect`, at the end. Then save the file and exit.

