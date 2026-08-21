# MALWARE TRAFFIC ANALYSIS

Analysis date: 19/08/2026

### Source of PCAP:

Malware-Traffic-Analysis.net

### File Name:

2021-09-10-traffic-analysis-exercise.pcap

### Zip file password:

infected_20210910

### SCENARIO

- LAN Segment range:
  (10.9.10.0/24 (10.9.10.0 through 10.9.10.255))

- Domain:
  angrypoutine.com

- Domain Controller:
  10.9.10.9 - ANGRYPOUTINE-DC

- LAN Segment gateway:
  10.9.10.1

- LAN segment broadcast address:
  10.9.10.255

### OBJECTIVES

1. Malware Name:
   trojan.kryplod/quantum

2. What is the IP of the infected Windows client?  
   10.9.10.102

3. What is the Hostname of the infected windows client?
   DESKTOP-KKITB6Q

4. What is the MAC address of the infected windows client?
   00:4f:49:b1:e8:c3

5. What is the user account name of the infected windows client? '  
   hobart.gunnarsson

6. What is the full name of the user from the infected windows user account?
   Hobart Gunnarsson

Indicators Of Compromise

7. Data exfil ip :
   // identify it via the malware traffic which seems over tls

8. Malicious URL :
   http[:]//simpsonsavingss[.]com/bmdff/BhoHsCtZ/MLdmpfjaX/5uFG3Dz7yt/date1?BNLv65=pAAS

9. Malware Source: ip :
   194.62.42.206

10. TCP port: src port:
    58131

11. Infection Time:
    2021-09-11 @ 02:17:27

### ANALYSIS

- Infected windows client

To identify the IP of the infected windows client we first identify the host host with the most traffic in "Conversations" and later identify that ip to have dowloaded an octet application from the ip which is later identified to be a trojan:

![img](case8_img1.png)

![img](case8_img2.png)

IP:_10.9.10.102_

- MAC Address of the infected windows host

Now that we have the IP of the Infected Windows Host,we need to identify its Mac address which we do so by filtering with its ip address "ip.addr == 10.9.10.102" and find it in the Ethernet II, under src mac address.

![img](case8_img3.png)

Mac addr:_00:4f:49:b1:e8:c3_

- Hostname of the infected windows client

To identify the hostname of the infected windows client we use the filter "nbns && ip.addr == 10.9.10.102"

![img](case8_img4.png)

Hostname:_DESKTOP-KKITB6Q_

- User Account Name

To identify the user account name we need to analyze Kerberos traffic to identify any username used for ticket granting,we use the filter

filter: "ip.addr == 10.9.10.102 && kerberos.CNameString"

![img](case8_img5.png)

We identify the user account to be:

The user account: _hobart.gunnarsson_

- Full Username of the user

To identify the full name of the the user of the compromised host we need to use the find option. "Ctrl + F" the filter for "packet details" + [String + case sensitive + multiple occurrences + backwards] and by trancating the user account name to "unnar"

Full Username: _Hobart Gunnarsson_

![img](case8_img6.png)

- Indicators of Compromise

During the investigation we identify a suspicious file which was downloaded via http from this ip "_194.62.42.206_" to "_10.9.10.102_" via port 58131 as src port:

![img](case8_img8.png)

![img](case8_img7.png)

which was downloaded _2021-09-11 @ 02:17:27_:

![img](infectiontime.png)

analysing this file it identified to be a windows executable:

![img](case8_img9.png)

Obtaining it md5 hash and performing a lookup on virustotal,its identified to be a windows trojan:

![img](case8_img11.png)
