# MALWARE TRAFFIC ANALYSIS

Analysis date: 9-08-2026

### Source of PCAP:

Malware-Traffic-Analysis.net

### File Name:

2024-07-30-traffic-analysis-exercise.pcap

### Zip file password:

infected_20240730

### SCENARIO

- LAN Segment range:
  172.16.1.0/24 (172.16.1.0 through 172.16.1.255)

- Domain:
  wiresharkworkshop.online

- Domain Controller:
  172.16.1.4 - WIRESHARK-WS-DC

- LAN Segment gateway:
  172.16.1.1

- LAN segment broadcast address:
  172.16.1.255

- Malware Source: ip : <>

- TCP port: src port <>

- Infection Time:?

### OBJECTIVES

1. Malware Name:

2. What is the IP of the infected Windows client?
   172.16.1.66

3. What is the Hostname of the infected windows client?
   DESKTOP-SKBR25F

4. What is the MAC address of the infected windows client?
   00:1e:64:ec:f3:08

5. What is the user account name of the infected windows client?
   ccollier

6. What is the full name of the user from the infected windows user account? <>
   Clark Collier

Indicators Of Compromise

7. Data exfil ip : <>

8. Malicious URL : <http: url>

### ANALYSIS

- Infected windows client

  To identify the infected windows client,from conversations we can see that the host with the ip is making alot of converstaions with external ips.

  ![img](Case6_img1.png)

  From its dns traffic we can see that there is potential malicious traffuc to github over port 443

IP: _172.16.1.66_

- MAC Address of the infected windows host

Now that we have the IP of the Infected Windows Host,we need to identify its Mac address which we do so by filtering with its ip address "ip.addr == 172.16.1.66 " and find it in the Ethernet II, under src mac address.

![img](Case6_img3.png)

Mac addr: _00:1e:64:ec:f3:08_

- Hostname of the infected windows client

To identify the hostname of the infected windows client we use the filter "nbns && ip.addr == 172.16.1.66"

![img](Case6_img2.png)

Hostname: _DESKTOP-SKBR25F_

- User Account Name

To identify the user account name we need to analyze Kerberos traffic to identify any username used for ticket granting,we use the filter

filter: "kerberos.CNameString != "DESKTOP-SKBR25F$" &&   kerberos.CNameString != "desktop-skbr25f$""

![img](Case6_img4.png)

We identify the user account to be:

The user account: ccollier

- Full Username of the user

To identify the full name of the the user of the compromised host we need to use the find option. "Ctrl + F" the filter for "packet details" + [String + case sensitive + multiple occurrences + backwards] and by trancating the user account name to "<>"

Full Username: Clark Collier

![img](Case6_img5.png)
