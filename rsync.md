# Using rsync to Backup File to NAS 

## What is it?

I use rsync to clone some of my files to a Synology NAS box in my local net.
This is the script i use to perform the backup task.

May it be an inspiration for others struggeling with a similar task.
(To be honest: one of the reasons for sharing it online is backup ;-)
 
```bash
#!/bin/sh
#
# iconv inspired by
#   https://wiki.ubuntuusers.de/rsync/
#
RSYNC=/usr/local/Cellar/rsync/3.1.3_1/bin/rsync
TIMESTAMP=$(date +"%Y_%m_%d_%H_%M")
SRC=~/Documents/FoerderVerein
NAS_SSH_NAME=42
DST=$NAS_SSH_NAME::NetBackup/Documents/FoederVerein/$TIMESTAMP

$RSYNC -av -e ssh \
        $SRC \
        $DST \
        --iconv=CP1252,UTF-8 \
        --human-readable
```

This very system runs rsync v2.*. Most of the files in the backup folder are inherited and contain funny characters, spaces and the like.
Without option `--iconv=CP1252,UTF-8` gibberish is stored on the target system. But this option requires rsync > v3.0 - hence the absolute reference to the correct rsync version.

Data is transferred using ssh and keys - so no passwords are needed.

