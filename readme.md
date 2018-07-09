# Second Drive Utility (macOS)

Mount and eject internal second drive with ease. Unmounted by default to avoid hdd noise.

1. Get disk UUID.
```console
$ diskutil list
Apple_HFS HDD                     499.8 GB   disk1s2
$ diskutil info /dev/disk1s2 | grep UUID
Disk / Partition UUID:    [UUID]
```
2. Replace [UUID] with your own in mount/eject apps (unzip and open with automator), .wakeup and second-drive-utility.plist.
3. Copy second-drive-utility.plist into Library/LaunchAgents.
```console
$ cp  second-drive-utility.plist ~/Library/LaunchAgents
```
4. Load script to launch on boot.
```console
$ sudo launchctl load -w ~/Library/LaunchAgents/second-drive-utility.plist
```
5. Insall sleepwatcher to prevent HDD to activate on wake.
```console
$ brew install sleepwatcher
$ brew services start sleepwatcher
$ cp .wakeup ~/.wakeup
```

You can easily mount and eject the disk manually copying mount/eject apps to Applications/Utilities and using spotlight.