# ubnt qos config

```text
traffic-policy {
    shaper client-down {
        bandwidth 80mbit
        class 2 {
            bandwidth 30%
            ceiling 40%
            description filetransfer
            match pc_client {
                ip {
                    destination {
                        address 192.168.1.238/32
                    }
                }
            }
            priority 5
        }
        default {
            bandwidth 50%
            ceiling 70%
            priority 4
        }
    }
}

set interfaces switch switch0 traffic-policy out client-down
```



