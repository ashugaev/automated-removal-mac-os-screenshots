# Setting up automatic screenshots removal on Mac OS
Stop making a mess on your desktop!

```bash
mkdir ~/Desktop/temp && defaults write com.apple.screencapture location  ~/Desktop/temp

find ~/Desktop/temp -type f -mtime +5 -exec rm '{}' +;
```

