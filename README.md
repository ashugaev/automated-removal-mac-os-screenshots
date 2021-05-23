# Setting up automatic screenshots removal on Mac OS
Stop making a mess on your desktop!

## Just execute this line into your Terminal

```bash
mkdir ~/Desktop/temp && defaults write com.apple.screencapture location  ~/Desktop/temp && (crontab -l 2>/dev/null; echo "0 0 * * * /usr/bin/find ~/Desktop/temp -type f -mtime +5 -exec rm -f '{}' +;") | crontab -
```

What the command does:
- Makes folder `~/Desktop/temp` as default for screenshots
- Adds a job in crontab to remove files in `temp` folder older than 5 days
