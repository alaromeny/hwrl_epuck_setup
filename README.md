# hwrl_epuck_setup
Directions on setting up your ubuntu laptop with the epucks we have in the lab


# BLUETOOTH SETUP FOR THE EPUCK


These instructions are based on the original by Thomas Lochmatter which I found at (https://github.com/awoody/e-puck)

### STEP 0: 
BLUEZ should be installed which you can check by running


```
dpkg --status bluez | grep '^Version:'
```

If it's not download from (http://www.bluez.org)

### STEP 1: 

Navigate to the ```scripts/``` folder where you first need to set the permission for each pearl script 

```
cd scripts
chmod +x btepucksetup*
```

Then run the scripts (which I have modified slightly) in the following order with these parameters I have added. You can copy and paste the following:

**You need to run these with root privileges** ( ```sudo su``` )

```
./btepucksetup1_bdaddr.pl ../epuck_bdaddr_hwrl
./btepucksetup2_udev.pl
./btepucksetup3_rfcomm.pl 2104
./btepucksetup4_minirc.pl 2104
```

epuck_bdaddr_hwrl is a list of all the mac addresses and IDs of the epucks in the lab
2104 is the smallest ID so it let's the script know where to start from

### STEP 2: 

Next navigate to the ```bluepin/``` folder and copy the bluepin file into ```/usr/bin/```

```
sudo cp bluepin /usr/bin/ 
```

### STEP 3:

Reboot your computer

### TROUBLESHOOTING :

##### Script 2:
The first script tried to edit a file at location '/etc/udev/permissions.d/50-udev.permissions' if this file doesn't exist it struggles, and will throw the following error:
``` Failed to add the udev configuration for RFCOMM!```

This file + folder combo needs to be created in /etc/udev/ you need to create it whilst in root.

```
sudo mkdir /etc/udev/permissions.d
cd /etc/udev/permissions.d
sudo touch 50-udev.permissions
```


