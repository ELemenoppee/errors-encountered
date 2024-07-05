# 🏵 Adding Scheduled Cleanup of Unused Docker Images 🏵

## Description

Maintaining an efficient and optimized Docker environment is crucial for performance and security. This guide will walk you through the process of setting up scheduled cleanups to automatically remove unused and obsolete Docker images at regular intervals. By implementing this practice, you can free up disk space, enhance system performance, and reduce potential security risks associated with outdated images.

By this guide, you'll be able to set up a scheduled cleanup of unused Docker images, ensuring a more efficient, secure, and reliable Docker environment. Let's get started!

## Steps 🧷:-

**Step 1** — Login to your Docker Server

**Step 2** — Open Crontab

```
crontab -e
```

**Step 3** — Add a line to schedule the command

```
0 0 * * * /usr/bin/docker system prune -af --filter "until=$((5*24))h"
```

**Note:** This command is scheduled to run the command every day at midnight.

**Explanation:**

* 0 0 * * * runs the command every day at midnight.
* Adjust the path to the docker command if necessary (/usr/bin/docker).

## Final Note

If you find this repository useful for learning, please give it a star on GitHub. Thank you!

**Authored by:** [ELemenoppee](https://github.com/ELemenoppee)
