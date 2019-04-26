# Use systemd and /etc/fstab to mount CIFS share

{% code-tabs %}
{% code-tabs-item title="fstab" %}
```text
# SMB Mount
//IP/SHARENAME	/mnt/MOUNTLOCATION	cifs	noauto,nofail,x-systemd.automount,x-systemd.requires=network-online.target,x-systemd.device-timeout=10,_netdev,dir_mode=0755,file_mode=0755,username=USER,password=PWD,vers=3.0 0 0

```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% embed url="https://wiki.archlinux.org/index.php/fstab" caption="fstab on arch wiki" %}



