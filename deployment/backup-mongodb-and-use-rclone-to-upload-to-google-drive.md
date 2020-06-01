# 部署MongoDB 备份 + Rclone上传

```bash
#!/bin/sh

set -e

DIR=`date +%Y%m%d_%H_%M_%S`
DEST=/mongo_backup/$DIR
mkdir $DEST
mongodump -o $DEST
tar czvf /mongo_backup/"$DIR".tar.gz -C $DEST .
rclone copy --progress /mongo_backup/"$DIR".tar.gz gdrive:dmm_backup
```



