# MALWARE TRAFFIC ANALYSIS

Analysis date: 06-08-2026

### Source of PCAP:

    Malware-Traffic-Analysis.net

### File Name:

2024-11-26-traffic-analysis-exercise.pcap

### Zip file password:

Infected_20241126

### SCENARIO

- LAN Segment range:
  (10.11.26.0 - 10.11.26.255)

- Domain:

- Domain Controller:
  10.11.26.3

- AD Environment Name:

- LAN Segment gateway:
  10.11.26.1

- LAN segment broadcast address:
  10.11.26.255

- Malware Source:
  ip : 194.180.191.64

- TCP port:
  src port 53363

- Infection Time:?

### OBJECTIVES

Malware Name:<>

1. What is the IP of the infected Windows client?
   10.11.26.183
2. What is the Hostname of the infected windows client?
   DESKTOP-B8TQK49

3. What is the MAC address of the infected windows client?
   d0:57:7b:ce:fc:8

4. What is the user account name of the infected windows client?
   oboomwald

5. What is the full name of the user from the infected windows user account?
   Oliver Q. Boomwald

6. IoCs

- Data exfil ip : 194.180.191.64
- Malicious URL : http[:]//194[.]180[.]191[.]64/fakeurl.htm
-

### ANALYSIS

- Infected windows client

To identify the IP of the infected windows client we filter "http" traffic to identify any unencrypted traffic and what the contents of the traffic are

![img](Case4_img1.png)

Checking the type of traffic coming from it we see its sending some POST request data which is encoded to this url "http://194.180.191.64/fakeurl.htm" which could be possible data leaks.

![img](Case4_img2.png)

IP: _10.11.26.183_

- MAC Address of the infected windows host

Now that we have the IP of the Infected Windows Host,we need to identify its Mac address which we do so by filtering with its ip address "ip.addr == 10.11.26.183 " and find it in the Ethernet II, under src mac address.

![img](Case4_img3.png)

Mac addr: _d0:57:7b:ce:fc:8b_

- Hostname of the infected windows client

To identify the hostname of the infected windows client we use the filter "nbns && ip.addr == 10.11.26.183"

![img](Case4_img6.png)

Hostname: _DESKTOP-B8TQK49_

- User Account Name

To identify the user account name we need to analyze Kerberos traffic to identify any username used for ticket granting,we use the filter

filter:
"ip.addr == 10.11.26.183 && kerberos.CNameString"

![img](Case4_img4.png)

We identify the user account to be:

The user account: _oboomwald_

- Full Username of the user

To identify the full name of the the user of the compromised host we need to use the find option. "Ctrl + F" the filter for "packet details" + [String + case sensitive + multiple occurences + backwards] and by trancating the user account name to "omwal"

Full Username: _Oliver Q. Boomwald_

![img](Case4_img5.png)
