# DD windows on GCP

This may\(will\) violate the TOS. Be careful.



```text
wget windows.vhd.gz
gunzip -bc windows.vhd.gz | dd of=/dev/sda
```

Or you can use the bash script from [https://moeclub.org/2017/11/19/483/](https://moeclub.org/2017/11/19/483/)

```text
wget --no-check-certificate -qO InstallNET.sh 'https://moeclub.org/attachment/LinuxShell/InstallNET.sh'

sudo bash InstallNET.sh --ip-addr X.X.X.X --ip-mask X.X.X.X --ip-gate X.X.X.X -dd "Direct Link of vhd.gz"
```

On GCP, you need to specify --ip-addr \(internal ip\), netmask and internal gateway. Those can be found in the GCP console

