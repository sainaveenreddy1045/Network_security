# Exploding Ubuntu Home Lab

This lab is focused on exploding the **Network Environment** in my ubuntu virtual mahine and identify Vulnarabilities.This is to understand how my server communicate with the network and ensures it is securily configured.

## 1. Identifying Network Interfaces & IP Addresses

**Command:** 
ip a or ifconfig

**Observation:**  
**ip a or ifconfig** It displays all the network interfaces and their assigned IP addresses. Which help me identify the active interfaces and how my virtual machine connects to the network.

**Output:** 
![ip a or ifconfig](./Images%20Home%20Lab/ip.png)

## 2. Check Oprn Ports

**Command:** 
Sudo netstat -tuln or ss -tuln

**Observation:**
**Sudo netstat -tuln or ss -tuln** It lists all open TCP or UDP ports which helps to identify what services are listing on my system.

**Output:**
![Sudo netstat -tuln or ss -tuln](./Images%20Home%20Lab/sudo%20netstat%20tuln%20or%20ss%20-tuln.png)

## 3. Analyze Network Connections

**Command:**
sudo lsof -i -P -n

**Observation:** 
**sudo lsof -i -P -n** It lists all open network connections and the processes that own them.

**Output:**
![sudo lsof -i -P -n](./Images%20Home%20Lab/sudo%20lsof%20-i%20-P%20-n.png)

## 4. Perform Network Scaning with Nmap

**Command:**
sudo nmap -sS -0 localhost

 **Observation:**
 **sudo nmap -sS -0 localhost** It shows all the open and Closed ports where i can see 999 closed ports and two open ports(Port 631).

 **Output:**
 ![sudo nmap -sS -0 localhost](./Images%20Home%20Lab/sudo%20nmap%20-ss%20-0%20localhost.png)

## 5. Check for open ports on server's Network

**Command:**
sudo nmap -sP 192.168.1.0/24

**Observation:**
**sudo nmap -sP 192.168.1.0/24** It detect all live hosts on my local network and also make sure that there are no unauthorized divices connected.

**Output:**
![sudo nmap -sP 192.168.1.0/24](./Images%20Home%20Lab/sudo%20nmap%20-SP%20192.168.1.0:24%202.png)

## 6. Check or Services and Versions

**Command:**
Sudo Nmap -sV localhost

**Observation:**
**Sudo Nmap -sV localhost** It Scans for Open Ports And identifies service versions that are running in them. THis detected CUPS 2.8

**Output:**
![Sudo Nmap -sV localhost](./Images%20Home%20Lab/sudo%20nmap%20-sV%20localhost.png)

## 7. Identify Potential Vulnerabilities

**Command:**
sudo nmap --script vuln localhost

**Observation:**
**sudo nmap --script vuln localhost** This runs Vulnerability Scripts against the local services. Here nmap Detected a potential Slowloris vulnarability.

**Output:**
![sudo nmap --script vuln localhost](./Images%20Home%20Lab/sudo%20nmap%20--script%20vuln%20localhost.png)

## 8. Inspect Network Traffic

**Command:**
sudo tcpdump -i ens160

**Observation:**
**sudo tcpdump -i ens160** It Captured 112 Packets in my Virtual Machine And Zero Dropper by Kernel.

**Output:**
![sudo tcpdump -i ens160](./Images%20Home%20Lab/sudo%20tcpdump%20-i%20ens160.png)

## 9. Monitor Network Connections in Real-Time

**Command:**
sudo watch -n 1 netstat -tulnp

**Observation:**
**sudo watch -n 1 netstat -tulnp** This will Continously Monitor my network connections, Updating every second this helps in observing new connections.

**Output:**
![sudo watch -n 1 netstat -tulnp](./Images%20Home%20Lab/sudo%20watch%20-n%201%20netstat%20-tulnp%20%20.png)

## 10. Check Firewall Rules 

**Command:**
sudo ufw status verbose

**Observation:**
**sudo ufw status verbose** It showes Status of Firwall. Since i didn't setup any firewall its showing Inactive.

**Output:**
![sudo ufw status verbose](./Images%20Home%20Lab/sudo%20ufw%20status%20verbose.png)