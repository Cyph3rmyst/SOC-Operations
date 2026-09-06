# MALWARE TRAFFIC ANALYSIS

Analysis date:

### Source of PCAP:

Malware-Traffic-Analysis.net

### File Name:

2020-06-12-traffic-analysis-exercise.pcap

### Zip file password:

infected_20200612

### SCENARIO

- LAN Segment range: 10.6.12.0/24 (10.6.12.0 through 10.6.12.255)

- Domain: frank-n-ted.com

- Domain Controller: 10.6.12.12 - Frank-n-Ted-DC

- LAN Segment gateway: 10.6.12.1

- LAN segment broadcast address: 10.6.12.255

### OBJECTIVES

1. Malware Name: <>

2. What is the IP of the infected Windows client? 10.6.12.203

3. What is the Hostname of the infected windows client? LAPTOP-5WKHX9YG

4. What is the MAC address of the infected windows client? 84:3a:4b:6d:fc:e2

5. What is the user account name of the infected windows client? frank.brokowski

6. What is the full name of the user from the infected windows user account? Ted Brokowski

- Indicators Of Compromise

7. Suspicious IPs : 205.185.125.104

8. Suspicious URL : http[:]//205.185.125[.]104/files/june11[.]dll

9. Malware Source: ip : 205.185.125.104

10. TCP port: src port 49739

11. Infection Time:
    2020-06-12 @ 20:15:19

### ANALYSIS

- Infected windows client

The host with ip "10.6.12.203" is seen to make a http "GET" request for a file named "june.dll" from the ip "205.185.125.104":

![img](case20_img1.png)

Exporting this file we identify it to be a windows executable with file hash of _"2545b15483165d00d1b6d63d9fd0821d"_

![img](case20_img2.png)

this confirms that this host is infected.

IP: _10.6.12.203_

- MAC Address of the infected windows host

Now that we have the IP of the Infected Windows Host,we need to identify its Mac address which we do so by filtering with its ip address "ip.addr == 10.6.12.203 " and find it in the Ethernet II, under src mac address.

![img](case20_img3.png)

Mac addr: _84:3a:4b:6d:fc:e2_

- Hostname of the infected windows client

To identify the hostname of the infected windows client we use the filter "nbns && ip.addr == 10.6.12.203"

![img](case20_img4.png)

Hostname: _LAPTOP-5WKHX9YG_

- User Account Name

To identify the user account name we need to analyze Kerberos traffic to identify any username used for ticket granting,we use the filter

filter: "ip.addr == 10.6.12.203 && kerberos.CNameString != "LAPTOP-5WKHX9YG$" && kerberos.CNameString != "laptop-5wkhx9yg$""

![img](case20_img5.png)

We identify the user account to be:

The user account: _frank.brokowski_

- Full Username of the user

To identify the full name of the the user of the compromised host we need to use the find option. "Ctrl + F" the filter for "packet details" + [String + case sensitive + multiple occurrences + backwards] and by trancating the user account name to "rokowski"

Full Username: _Ted Brokowski_

![img](case20_img6.png)
