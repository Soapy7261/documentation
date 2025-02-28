# Pruning docker images

This guide provides comprehensive instructions on how to prune docker images on your server automatically using cron.

Due to how Docker works, when pulling new images, the old ones are not removed and are considered "dangling". This will eventually lead to a large amount of disk space being used up by dangling images and eventually cause your server to run out of disk space.

## Crontab Configuration

To automatically prune docker images, you'll want to open your crontab using `sudo crontab -e` and then paste the line below.

You may change the time to whatever you want, but the example below will run the command at midnight (based off your server's time) every day.

::: tip
If you want, you can add -a to end of the command to remove *all* unused images, not just dangling ones.

This may be particularly useful if you remove/change images from your yolks often.

:::

```sh
0 0 * * * docker image prune -f
```
