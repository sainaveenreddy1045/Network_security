# I. Enabling UFW 

1. Checking status of UFW

**Command:**
sudo ufw status

Status: 
![status:inactive]

2. Before enabiling UFW we make sure that our connection is allowed to ssh using command: sudo ufw allow 22/tcp

Since port 22 is used by SSH it is the protocol that allow remote login. so it is important to allow traffic through the port 22 before enabling UFW.

**Enabling Port 22:**

![Port 22]

3. Allow other connections like Port 80 and 443 using the following command lines

sudo ufw allow 80

sudo ufw allow 443

![Port 80, Port 443]

we use command **sudo ss -tuln** to check all the network statistics. Here tuld checks all TCP, UDP, Listening n Display addresses in numeric form and Socket Statistics(ss) which is command line utility for checking Network statistics.

![sudo ss -tuln]

This command list all ports that are active in my virtual machine.I found a which i am unsure of which is port 
By using command: sudo lsof -i :PortNumber we can check specific service