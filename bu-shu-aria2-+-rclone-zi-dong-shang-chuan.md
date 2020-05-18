# 部署Aria2 + Rclone 自动上传

{% embed url="https://github.com/P3TERX/docker-aria2-pro" %}

使用Buyvm LAS 挂载slab部署aria

```text
docker run -d \
    --name aria2-pro \
    --restart unless-stopped \
    --log-opt max-size=1m \
    --network host \
    -e PUID=$UID \
    -e PGID=$GID \
    -e RPC_SECRET=P3TERX \
    -e RPC_PORT=6800 \
    -e LISTEN_PORT=6888 \
    -v ~/aria2-config:/config \
    -v ~/rclone-downloads:/downloads \
    -e SPECIAL_MODE=rclone \
    p3terx/aria2-pro
```

把rclone.conf复制到 aria的config,修改autoupload.sh  




