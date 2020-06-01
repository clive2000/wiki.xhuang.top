# Caddy + Docker + Trojan 部署梯子

1. [https://github.com/chiakge/Linux-NetSpeed](https://github.com/chiakge/Linux-NetSpeed) 一键脚本BBRPlus内核
2. Caddy 安装时设置cloudflare插件
3. Caddyfile 范例:

```text
t.lightsailjp.zb8.stream {
  gzip
  tls {
      dns cloudflare
  }
  log /var/log/caddy/caddy.trojan.log
  proxy / https://baidu.com
  proxy /leet 127.0.0.1:13338 {
    websocket
    header_upstream -Origin
  }
}


embyjp.zb8.stream {
  gzip
  tls {
      dns cloudflare
        }
  log /var/log/caddy/caddy.emby.log
  proxy / 127.0.0.1:8096 {
   header_upstream -Origin
  websocket
        }
}
```

caddy运行时，需要在dns处设置txt设置解析, 同时需要设置

为caddy添加systemd 服务 （[https://github.com/caddyserver/caddy/blob/master/dist/init/linux-systemd/caddy.service](https://github.com/caddyserver/caddy/tree/master/dist/init/linux-systemd)）注意设置里的CADDYPATH，caddy申请的ssl证书保存在这里，后面使用v2ray或者trojan会用到。同时要设置CLOUDFLARE\_EMAIL 和 CLOUDFLARE\_API\_KEY 两个环境变量，Caddy运行时获取证书会用到:

```text
Environment=CADDYPATH=/etc/ssl/caddy
Environment=CLOUDFLARE_EMAIL="EMAIL"
Environment=CLOUDFLARE_API_KEY="CLOUDFLARE GLOBAL API"
```

部署trojan

新建/etc/trojan 目录，在目录下新建config.json文件

Trojan 配置

```text
{
    "run_type": "server",
    "local_addr": "0.0.0.0",
    "local_port": 443,
    "remote_addr": "127.0.0.1",
    "remote_port": 80,
    "password": [
        "PASSWORD"

    ],
    "log_level": 1,
    "ssl": {
        "cert": "/crt/t.lightsailjp.zb8.stream.crt",
        "key": "/crt/t.lightsailjp.zb8.stream.key",
        "key_password": "",
        "cipher": "ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256",
        "prefer_server_cipher": true,
        "alpn": [
            "http/1.1"
        ],
        "reuse_session": true,
        "session_ticket": false,
        "session_timeout": 600,
        "plain_http_response": "",
        "curves": "",
        "dhparam": ""
    },
    "tcp": {
        "prefer_ipv4": false,
        "no_delay": true,
        "keep_alive": true,
        "fast_open": false,
        "fast_open_qlen": 20
    },
    "mysql": {
        "enabled": false,
        "server_addr": "127.0.0.1",
        "server_port": 3306,
        "database": "trojan",
        "username": "trojan",
        "password": ""
    }
}
```

运行docker，把/etc/ssl/sites 映射到容器的/crt目录下

```text
docker run -d --name trojan -v /etc/trojan:/config -v /etc/ssl/acme:/crt -p 32400:443 trojangfw/trojan
```



