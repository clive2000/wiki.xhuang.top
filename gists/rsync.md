---
description: How to rsync between 2 smb share on FreeNAS
---

# Rsync

{% code title="sync\_between\_smb.sh" %}
```bash
rsync --partial --stats --progress -A -a -r -v --no-perms /mnt/SOURCE /mnt/DEST
```
{% endcode %}

