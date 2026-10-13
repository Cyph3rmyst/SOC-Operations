# MALWARE TRAFFIC ANALYSIS

Analysis date:

### Source of PCAP:

Malware-Traffic-Analysis.net

### File Name:

### Zip file password:

infected\_<year><month><day>

### SCENARIO

- LAN Segment range:
  10.7.31.0/24 (10.7.31.0 through 10.7.31.255)

- Domain: tecsolutions.info

- Domain Controller:
  10.7.31.7 - Tecsolutions-DC

- LAN Segment gateway:10.7.31.1

- LAN segment broadcast address: 10.7.31.255

### OBJECTIVES

1. Malware Name: <>

2. What is the IP of the infected Windows client? <>

3. What is the Hostname of the infected windows client? <>

4. What is the MAC address of the infected windows client? <>

5. What is the user account name of the infected windows client? <>

6. What is the full name of the user from the infected windows user account? <>

- Indicators Of Compromise

7. Suspicious IPs : 201.235.10.215,104.236.52.89,

8. Suspicious URL : http[:]//e-dsm[.]com[.]br/www/ZdJCAB/

9. Malware Source: ip : 67.20.112.81

10. TCP port: src port 80

11. Infection Time:
    2020-07-31 @ 03:25:37

### ANALYSIS

- Infected windows client
  From the alerts some key information stands out and among them we have one of our host with ip "10.7.31.101" is noted to be downloading some suspicious files:

![img](case14_img1.png)

From the conversations we can see that the same host is making alot of traffic with external ips:

![img](case14_img2.png)

Now from the http traffic "filter: ip.addr == 10.7.31.101 && http.request.method == "GET"" we can see that the same host is making a GET request for two files _DYsPb_ and _ZdJCAB_:

![img](case14_img3.png)

Analyzing the first file ZdJCAB is a "Composite Document File V2 Document" for windows OS with hash "_bee97c2cd32806d16640a8c1ed4e080f_": identified as "downloader.w97m/emotet"

![img](case14_img4.png)

![img](case14_img10.png)
The second file DYsPb is a Windows executable with hash _"b7ec256bd8cdb13ec031c4595514666e"_ " trojan.emotet/euig"

![img](case14_img5.png)

![img](case14_img11.png)

Performing a virus total lookup for the two file hashes return the following results:

1. ZdJCAB: The Composite Document File V2 Document

![img]

2.DYsPb: PE32 executable for MS Windows 4.00

[img]

IP: _10.7.31.101_

- MAC Address of the infected windows host

Now that we have the IP of the Infected Windows Host,we need to identify its Mac address which we do so by filtering with its ip address "ip.addr == <> " and find it in the Ethernet II, under src mac address.

![img](case14_img6.png)

Mac addr: _00:0c:6e:12:af:38_

- Hostname of the infected windows client

To identify the hostname of the infected windows client we use the filter "nbns && ip.addr == 10.7.31.101"

![img](case14_img7.png)

Hostname: _DESKTOP-DPHW305_

- User Account Name

To identify the user account name we need to analyze Kerberos traffic to identify any username used for ticket granting,we use the filter

filter: "ip.addr == 10.7.31.101 && kerberos.CNameString"

![img](case14_img8.png)

We identify the user account to be:

The user account: _gregory.simmons_

- Full Username of the user

To identify the full name of the the user of the compromised host we need to use the find option. "Ctrl + F" the filter for "packet details" + [String + case sensitive + multiple occurrences + backwards] and by trancating the user account name to "immons"

Full Username: _Gregory Simmons_

![img](case14_img9.png)
