# I. Enabling UFW 

1. Checking status of UFW

**Command:**
sudo ufw status

Status: 
![status:inactive](./Images%20UFW/sudo%20ufw%20status.png)

2. Before enabiling UFW we make sure that our connection is allowed to ssh using **command: sudo ufw allow 22/tcp**

Since port 22 is used by SSH it is the protocol that allow remote login. so it is important to allow traffic through the port 22 before enabling UFW.

**Enabling Port 22:**

![Port 22](./Images%20UFW/sudo%20ufw%20allow%2022:tcp.png)

3. Allow other connections like Port 80 and 443 using the following command lines

sudo ufw allow 80

sudo ufw allow 443

![Port 80, Port 443](./Images%20UFW/sudo%20ufw%20allow.png)

we use command **sudo ss -tuln** to check all the network statistics. Here tuld checks all TCP, UDP, Listening n Display addresses in numeric form and Socket Statistics(ss) which is command line utility for checking Network statistics.

![sudo ss -tuln](./Images%20UFW/sudo%20ss%20-tuln.png)

This command list all ports that are active in my virtual machine.I found a which i am unsure of which is port 
By using command: sudo lsof -i :PortNumber we can check specific service.
![sudo lsof -i :portnumber](./Images%20UFW/sudo%20lsof%20-i%20:631.png)

4. To enable UFW we use command: sudo ufw enable
5. Then we can check the status of UFW using command: sudo ufw status

![Ufw enable and Status](./Images%20UFW/sudo%20ufw%20enable.png)

6. The important ports that should be allowed through UFW for a web server are Port 443 and Pot 80 Because:

Port 443 is used for secure and Encrypted Web traffic like HTTPS.

Port 80 is used for regural and unencrypted web like HTTP.

7. To see that the firewall is configyured properly and only the necessary services are open we use **command: sudo ufw status verbose**. 

![sudo ufw status verbose](./Images%20UFW/sudo%20ufw%20status%20verbose.png)

8. To lock someones ip address we can use **command: sudo deny from <ip address>**.
This image shows example on how to block someones ip address.
![sudo ufw deny](./Images%20UFW/sudo%20ufw%20deny%20from%2010.0.0.0.png)

9. To allow Someones ip address we can use the following **command: sudo ufw allow from <ip address> to any <port no>**.

Port 587 is used for SMPT (Simple Mail Transfer Protocol) Submission. This is a default port to send outgoing mails from an email client to mail server.
![sudo ufw allow](./Images%20UFW/sudo%20ufw%20allow%20from%20192.168.1.50%20to%20any%20port%20587.png)

10. Lets check all the rules by checking the status again.
![sudo ufw status verbose](./Images%20UFW/sudo%20ufw%20status%20verbose%2010.png)

# II. Enable UFW Logging 

1. Before checking the logs lets make sure that UFW logging is enabled. To enable logging we can use **Command: sudo ufw logging on** 
2. Setting logging level to high we use **command: sudo ufw logging high** 
By setting logging level to high it includes all blocked packets and connection information.

![sudo ufw logging on](./Images%20UFW/sudo%20ufw%20logging.png)

3. Th UFW logs are stored in /var/log/ufw.log. To view all the logs in our virtual machine we can use **command: sudo tail -f /var/log/ufw.log** this -f allow us to monitor the log in real time.

![Sudo tail -f](./Images%20UFW/sudo%20tail%20-f%20:var:log:ufw.log.png)

4. To check Specific entries we can use grep command. These are powerfull commnd-line utilities in Linux used to search for spefic text patterns within files or command outputs.

- For Allowed Traffic: Sudo grep 'ALLOW' /var/log/ufw.log
- For Denied Traffic: Sudo grep 'DENY' /var/log/ufw.log

![sudo grep](./Images%20UFW/sudo%20grep%20'DENY'%20DENY'%20:var:log:ufw.log.png)

Since there are no unauthorized or blocked connections attempts during logging period ther is no out put for DENY.