# Enable autologin on debian buster

Go to  /usr/share/lightdm/lightdm.conf.d folder

Modfiy lightdm.conf.d

```text
[Seat:*]
pam-service=lightdm
pam-autologin-service=lightdm-autologin
autologin-user=username
autologin-user-timeout=0
session-wrapper=/etc/X11/Xsession
greeter-session=lightdm-greeter
```

also you need to add a autologin group

```text
groupadd autologin
usermod -aG autologin xhuang
```

