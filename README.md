# Raspberry PI POE hat Fan control v1.0

## Requirements

The `fan.sh` script requires `bc` to be installed.

Install it with the following command:

`sudo apt-get install bc`

## Setup

### Disable Default fan control

The default POE hat fancontrol will keep the fan turend of till about 50C but will go full speed above that.
To disable this annoying behaviour edit the File:

`/boot/config.txt`

At the bottom of the file add the following:

```
#POE fan config
dtparam=poe_fan_temp0=90000,poe_fan_temp1=95000
```

This will disable the default fan control until the CPU reaches 90C.

### Configure fan.sh

The `fan.sh` will control the fan in a linear fashion. To setup the fancurve the user can set the following variables:

`temp_min` Determines the bottom temperature where the fan will be set to `fan_min`. Default is: **40**
`temp_max` Determines the top temperature where the fan will be set to `fan_max`. Default is: **90**
`fan_min` Determines the minimum speed of the fan, even below the the `temp_min`. Default is: **0**
`fan_max` Determines the maximum speed of the fan, even above the `temp_max`. Default is: **255**

The range of `fan_min` and `fan_max` is **0** to **255**

### Enable fan.sh

Make `fan.sh` executable:

`chmod +x fan.sh`

To run the `fan.sh` add the script in a cronjob to be executed at reboot.

