# Source of PCAP:
    Malware-Traffic-Analysis.net
# File Name:

 2026-02-28 EASY as 123

# Zip file password:
infected_20260228

# SCENARIO
- LAN Segment range:
    10.2.28.0/24
    (10.2.28.0 - 10.2.28.255)

- Domain:
    easy123.tech


- Domain Controller:
    EASYAS-DC
    
- AD Environment Name:
    EASYAS123


- LAN Segment gateway:
    10.2.28.1


- LAN segment broadcast address:
    10.2.28.255


- Malware Source:
    45.131.214.85


- TCP port:
    443


- Infection Time:
    2026-02-28
    @ 19:55 UTC


#   OBJECTIVES 

Malware Name:NetSupport Manager RAT


1. What is the IP of the infected Windows client?
    10.2.28.88

2.What is the MAC address of the infected windows client?
    00:19:d1:b2:4d:ad

3.What is the user account name of the infected windows client?
    brolf



4.What is the full name of the user from the infected windows user account?
    Becka Rolf


# ANALYSIS


- Infected  windows Client


To identify the IP of the infected windows client we filter  "http" traffic to identify any unencrypted traffic and what the contents of the traffic are

![img](case1_img1.png)


It seems there is alot of traffic comming from  10.2.28.88

Checking the type of traffic coming from it we see its sending some POST request to "http://45.131.214.85/fakeurl.htm" which could be possible data leaks

![img](case1_img2.png)

IP: 10.2.28.88

- MAC Address of the infected windows host


Now that we have the IP of the Infected Windows Host,we need to identify its Mac address which we do so by filtering with its ip address "ip.addr == 10.2.28.88 "

![img](case1_img3.png)

Mac addr:00:19:d1:b2:4d:ad

- User Account Name

To identify the user account name we need to user Kerberos traffic to identify any username  used for ticket granting,we use the filter "kerberos.CNameString"

Kerberos Traffic

![img](case1_img4.png)

We idetify the CNameString as "brolf" which our client user's account name

- brolf

- Full Username of the user 

Here i used Packet Find option and some port filtering which led me to port "tcp.port == 59988" and in tcp.stream eq 9 i found the full username of the user as

Becka Rolf


![img](case1_img6.png)

















