# MALWARE TRAFFIC ANALYSIS

Analysis date: 9-08-2026

### Source of PCAP:

Malware-Traffic-Analysis.net

### File Name:

2022-03-21-traffic-analysis-exercise.pcap

### Zip file password:

infected_20220321

### SCENARIO

- LAN Segment range:
  10.0.19.0/24 (10.0.19.0 through 10.0.19.255)

- Domain:
  burnincandle.com

- Domain Controller:
  10.0.19.9 - BURNINCANDLE-DC

- LAN Segment gateway:
  10.0.19.1

- LAN segment broadcast address:
  10.0.19.255

### OBJECTIVES

1. Malware Name:

2. What is the IP of the infected Windows client?
   10.0.19.14

3. What is the Hostname of the infected windows client?
   DESKTOP-5QS3D5D

4. What is the MAC address of the infected windows client?
   00:60:52:b7:33:0f

5. What is the user account name of the infected windows client?
   patrick.zimmerman

6. What is the full name of the user from the infected windows user account?
   Patrick Zimmerman

- Indicators Of Compromise

7. Data exfil ip : <>

8. Malicious URL : <http: url>

9. Malware Source: ip : <>

10. TCP port: src port <>

11. Infection Time:?

### ANALYSIS

- Infected windows client

To identify the IP of the infected windows client we analyze the conversation and suspiciously identify the host with the ip " 10.0.19.14" has alot of conversations with external ips

![img](Case7_img1.png)

IP: _10.0.19.14_

- MAC Address of the infected windows host

Now that we have the IP of the Infected Windows Host,we need to identify its Mac address which we do so by filtering with its ip address "ip.addr == 10.0.19.14" and find it in the Ethernet II, under src mac address.

![img](Case7_img2.png)

Mac addr: _00:60:52:b7:33:0f_

- Hostname of the infected windows client

To identify the hostname of the infected windows client we use the filter "nbns && ip.addr == 10.0.19.14 "

Hostname:

![img](Case7_img3.png)

- User Account Name

To identify the user account name we need to analyze Kerberos traffic to identify any username used for ticket granting,we use the filter

filter: "ip.addr == 10.0.19.14 && kerberos.CNameString"

![img](Case7_img4)

We identify the user account to be:

The user account: patrick.zimmerman

- Full Username of the user

To identify the full name of the the user of the compromised host we need to use the find option. "Ctrl + F" the filter for "packet details" + [String + case sensitive + multiple occurrences + backwards] and by trancating the user account name to "immerm"

Full Username: Patrick Zimmerman

![img](Case7_img5.png)
