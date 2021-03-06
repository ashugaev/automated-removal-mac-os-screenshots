# Setting up automatic screenshots removal on Mac OS
Stop making a mess on your desktop!

⚠️ Before executing commands, you need to give a cron full disk access [instruction is here](https://osxdaily.com/2020/04/27/fix-cron-permissions-macos-full-disk-access/)

## Just execute this line into your Terminal

```bash
FOLDER_NAME=screenshots; FILES_MAX_AGE=14; mkdir ~/Desktop/$FOLDER_NAME && defaults write com.apple.screencapture location ~/Desktop/$FOLDER_NAME && (crontab -l 2>/dev/null; echo "0 0 * * * /usr/bin/find ~/Desktop/$FOLDER_NAME -type f -mtime +$FILES_MAX_AGE -exec rm -f '{}' +;") | crontab -
```

What the command does:
- Makes folder `~/Desktop/screenshots` as default for screenshots
- Adds a job in crontab to remove files in `screenshots` folder older than 14 days

## Add also automatic cleaning of the downloads folder

```bash
FILES_MAX_AGE=14; (crontab -l 2>/dev/null; echo "0 0 * * * /usr/bin/find ~/Downloads -type f -mtime +$FILES_MAX_AGE -exec rm -f '{}' +;") | crontab -
```
