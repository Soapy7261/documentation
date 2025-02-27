# Pruning docker images

This guide provides comprehensive instructions on how to prune docker images on your server automatically using cron.

Due to how Docker works, when pulling new images, the old ones are not removed. This can lead to a large amount of disk space being used up by old images and eventually cause your server to run out of disk space.

## Crontab Configuration

To automatically prune docker images, you'll want to open your crontab using `sudo crontab -e` and then paste the line below.

::: tip
If you want, you can add -a to end of the command to remove all unused images, not just dangling ones.

This may be particularly useful if you remove/change images from your yolks often.

:::

```sh
* * * * * docker image prune -f
```
