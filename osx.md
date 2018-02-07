# Various Tips regarding using os x devices

## tweeking spotlight

1. disable it

```bash
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.metadata.mds.plist
```

2. enable it
```bash
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.metadata.mds.plist
```

Taken from [RecomHub](http://recomhub.com/blog/how-to-turn-off-and-on-spotlight-in-mac-os-x-el-capitan/) - thx
