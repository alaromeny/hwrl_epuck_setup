# hwrl_epuck_setup
Directions on setting up your ubuntu laptop with the epucks we have in the lab


# BLUETOOTH SETUP FOR THE EPUCK
===============================

These instructions are based on the original by Thomas Lochmatter which I found at (https://github.com/awoody/e-puck)


BLUEZ should be installed which you can check by running


```
dpkg --status bluez | grep '^Version:'
```

If it's not download from (http://www.bluez.org)

within the scripts folder you need to set the permission for each pearl script 

```
cd scripts
chmod +x btepucksetup*
```

Then run the scripts (which I have modified slightly) in the following order with these parameters I have added. You can copy and paste the following:

'''You need to run these with root privileges'''

```
./btepucksetup1_bdaddr.pl ../epuck_bdaddr_hwrl
./btepucksetup2_udev.pl
./btepucksetup3_rfcomm.pl 2104
./btepucksetup4_minirc.pl 2104
```

epuck_bdaddr_hwrl is a list of all the mac addresses and IDs of the epucks in the lab
2104 is the smallest ID so it let's the script know where to start from

### BLUETOOTH SETUP FOR THE EPUCK
===============================