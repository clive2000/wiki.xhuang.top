# Control Supermicro board's fan speed using IPMITool

```text
#Install ipmitool
apt install ipmitool

#Set Fan threshold
ipmitool -I lanplus -H [HOSTNAME] -U [USER] -P [PASSWORD] sensor thresh 'FAN 1' lower 0 0 200

#Send raw command to change fan operation mode
ipmitool -I lanplus -H [HOSTNAME] -U [USER] -P [PASSWORD] raw 0x30 0x45 0x01 0x02
```

