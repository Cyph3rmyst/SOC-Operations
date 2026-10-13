# MALWARE TRAFFIC ANALYSIS

Analysis date:

### Source of PCAP:

Malware-Traffic-Analysis.net

### File Name:

2020-02-21-traffic-analysis-exercise.pcap

### Zip file password:

infected_20200221

### SCENARIO

- LAN Segment range:172.17.8.0/24 (172.17.8.0 through 172.17.8.255)

- Domain: one-hot-mess.com

- Domain Controller: 172.17.8.8 - One-Hot-Mess-DC

- LAN Segment gateway: 172.17.8.1

- LAN segment broadcast address: 172.17.8.255

### OBJECTIVES

1. Malware Name: trojan.dridex/graftor

2. What is the IP of the infected Windows client? 172.17.8.174

3. What is the Hostname of the infected windows client? DESKTOP-TZMKHKC

4. What is the MAC address of the infected windows client? 00:11:75:8c:fd:47

5. What is the user account name of the infected windows client? gabriella.ventura

6. What is the full name of the user from the infected windows user account? Gabriella Ventura

- Indicators Of Compromise

7. Suspicious IPs : 49.51.172.56,205.185.216.42,91.211.88.122

8. Suspicious URL : http[:]//blueflag[.]xyz/nCvQOQHCBjZFfiJvyVGA/yrkbdmt[.]bin

9. Malware Source: ip : 49.51.172.56

10. TCP port: src port : 49731

11. Infection Time:2020-02-21 @ 03:55:06

### ANALYSIS

- Infected windows client

In the alerts some information stands out, an internal system with the ip "172.17.8.174" makes contants which show alerts for .exe download:

![img](case17_img1.png)

The same ip also made a http "GET" request for a .bin file named "yrkbdmt.bin":

![img](case17_img2.png)

Analysing the file we identify that its a windows executable with file hash _64aabb8c0ca6245f28dc0d7936208706_:

![img](case17_img3.png)

![img](case17_img8.png)

IP: _172.17.8.174_

- MAC Address of the infected windows host

Now that we have the IP of the Infected Windows Host,we need to identify its Mac address which we do so by filtering with its ip address "ip.addr == 172.17.8.174 " and find it in the Ethernet II, under src mac address.

![img](case17_img4.png)

Mac addr: _00:11:75:8c:fd:47_

- Hostname of the infected windows client

To identify the hostname of the infected windows client we use the filter "nbns && ip.addr == 172.17.8.174 "

![img](case17_img5.png)

Hostname: _DESKTOP-TZMKHKC_

- User Account Name

To identify the user account name we need to analyze Kerberos traffic to identify any username used for ticket granting,we use the filter

filter: "ip.addr == 172.17.8.174 && kerberos.CNameString != "DESKTOP-TZMKHKC$" && kerberos.CNameString != "desktop-tzmkhkc$""

![img](case17_img6.png)

We identify the user account to be:

The user account: _gabriella.ventura_

- Full Username of the user

To identify the full name of the the user of the compromised host we need to use the find option. "Ctrl + F" the filter for "packet details" + [String + case sensitive + multiple occurrences + backwards] and by trancating the user account name to "Gabriella"

Full Username: _Gabriella Ventura_

![img](case17_img7.png)
