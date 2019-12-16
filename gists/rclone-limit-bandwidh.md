# rclone limit bandwidh

rclone has a limitbw flag, here is a example of using it to make sure you upload less than 750GB a day to Gdrive

```bash
rclone copy --progress -v --bwlimit 8M --size-only --fastlist src:folder dest:folder
```



