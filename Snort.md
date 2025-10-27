# Exploring Snort

In this lab i will install and cnfigure Snort for my virtual machine.

## System Update 

Before initilazing and configuring Snort we need to update the system. Using **Command: sudo apt update**

![sudo apt update](./Images%20Snort/sudo%20apt%20update.png)

## Installing Snort 

By using **Command: sudo apt install snort -y** we can install Snort.

![sudo apt install snort -y](./Images%20Snort/sudo%20apt%20install%20snort%20-y.png)

It will be installed to /etc/snort/ with default configurations and rules.

By using **Command: ip a** we can fid the network interface.

![ip a](./Images%20Snort/ip%20a.png)

With all this information we can set network interface to any network we want to monitor and the HOME_NET to define our home network
