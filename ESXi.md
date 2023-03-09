# ESXi 7.0
- VMware-VMvisor-Installer-7.0U3g-20328353.x86_64.iso
- ESXi-7.0U3g-20328353-standard

### Update Time & date
> Manage -> System -> Time & date -> Edit NTP Settings
```
us.pool.ntp.org
```

### Enable SSH
> Host -> Actions -> Services -> Enable Secure Shell (SSH)
> Manage -> Services -> TSM-SSH -> Start

### VMware ESXi Profile
```
esxcli software profile get
```
```
esxcli system version get
```


### Update ESXi 7
[VMware Latest Patches](https://customerconnect.vmware.com/patch)
[VMware ESXi Patch Tracker](https://esxi-patches.v-front.de/ESXi-7.0.0.html)

Web Example:
```
esxcli network firewall ruleset set -e true -r httpClient
esxcli software profile update --no-hardware-warning -p ESXi-7.0U3k-21313628-standard -d https://hostupdate.vmware.com/software/VUM/PRODUCTION/main/vmw-depot-index.xml
esxcli network firewall ruleset set -e false -r httpClient
```

Local Example:
```
esxcli system maintenanceMode set -e true
esxcli system maintenanceMode get
esxcli software sources profile list -d /vmfs/volumes/datastore/VMware-ESXi-7.0U3k-21313628-depot.zip
esxcli software profile update --no-hardware-warning -d /vmfs/volumes/datastore/Mware-ESXi-7.0U3k-21313628-depot.zip -p ESXi-7.0U3k-21313628-standard
esxcli system maintenanceMode set -e false
```
```
esxcli software vib update -d /vmfs/volumes/datastore/VMware-ESXi-7.0U3k-21313628-depot.zip
```