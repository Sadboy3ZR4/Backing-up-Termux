# Backing-up-Termux
```bash
This page shows an example of backing up your Termux installation. Instructions listed there cover basic usage of archiving utility "tar" as well as show which files should be archived. It is highly recommended to understand what the listed commands do before copy-pasting them. Misunderstanding the purpose of each step may irrecoverably damage your data. If that happened to you - do not complain.
```

## Backing up
```
1. Ensure that storage permission is granted:

 $ termux-setup-storage
 $ tar -zcf /sdcard/termux-backup.tar.gz -C /data/data/com.termux/files ./home ./usr
```

## Restoring
```
1. Ensure that storage permission is granted:

 $ termux-setup-storage
 $ tar -zxf /sdcard/termux-backup.tar.gz -C /data/data/com.termux/files --recursive-unlink --preserve-permissions

Now close Termux with the "exit" button from notification and open it again.
```

## Warning⚠️
```
never store your backups in Termux private directories. Their paths may look like:
• /data/data/com.termux                  - private Termux directory on internal storage

• /sdcard/Android/data/com.termux        - private Termux directory on shared storage

• /storage/XXXX-XXXX/Android/data/com.termux  - private Termux directory on external storage, XXXX-XXXX is the UUID of your micro-sd card.

• ${HOME}/storage/external-1              - alias for Termux private directory on your micro-sd.

Once you clear Termux data from settings, these directories are erased too.
```

# Using supplied scripts
```
These scripts backup and restore scripts will not backup, restore or in any other way touch your home directory.
```

## Using termux-backup
```
Simple backup with auto compression:

$ termux-backup /sdcard/backup.tar.xz
$ termux-backup - | gpg --symmetric --output /sdcard/backup.tar.gpg

Content written to stdout is not compressed.
```

## Using termux-restore
```
Restoring backup is also simple:
$ termux-restore /sdcard/backup.tar.xz

compressed backup:
$ export GPG_TTY=$(tty)
gpg --decrypt /sdcard/backup.tar.gz.gpg | gunzip | termux-restore
```

## [👉 SOURCE 👈](https://wiki.termux.com/wiki/Backing_up_Termux)
