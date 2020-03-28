# rclone

rclone has a limitbw flag, here is a example of using it to make sure you upload less than 750GB a day to Gdrive

```bash
rclone copy --progress -v --bwlimit 8M --size-only --fast-list src:folder dest:folder
```

Rclone mount systemd

```text
[Unit]
Description=RClone Service
After=network-online.target
Wants=network-online.target


[Service]
Type=notify
ExecStart=/usr/bin/rclone mount gcrypt: /gmedia \
   --allow-other \
   --dir-cache-time 48h \
   --vfs-cache-max-age 48h \
   --vfs-read-chunk-size 10M \
   --vfs-read-chunk-size-limit 512M \
   --buffer-size 512M \
   --syslog \
   --umask 002 \
   --rc \
   --log-level INFO
ExecStop=/usr/bin/sudo /usr/bin/fusermount -uz /gmedia
Restart=on-abort
User=felix
Group=felix


[Install]
WantedBy=default.target
```



