# Setting up automatic screenshots removal on Mac OS
Stop making a mess on your desktop!

## Just execute this line into your Terminal

```bash
FOLDER_NAME=screenshots; FILES_MAX_AGE=5; mkdir ~/Desktop/$FOLDER_NAME && defaults write com.apple.screencapture location ~/Desktop/$FOLDER_NAME && (crontab -l 2>/dev/null; echo "0 0 * * * /usr/bin/find ~/Desktop/$FOLDER_NAME -type f -mtime +$FILES_MAX_AGE -exec rm -f '{}' +;") | crontab -
```

What the command does:
- Makes folder `~/Desktop/temp` as default for screenshots
- Adds a job in crontab to remove files in `temp` folder older than 5 days

## Add also automatic cleaning of the downloads folder

```bash
FILES_MAX_AGE=14; (crontab -l 2>/dev/null; echo "0 0 * * * /usr/bin/find ~/Downloads -type f -mtime +$FILES_MAX_AGE -exec rm -f '{}' +;") | crontab -
```
