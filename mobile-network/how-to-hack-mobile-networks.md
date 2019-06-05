# How to Hack Mobile Networks 3G/4G [ part 1 ]

> Mobile telecommunication networks are today one of the most important pillars of modern society

> Hacking these networks is more than an attack is proof that you are one of the best! In hacking or you are 1 or 0


## How mobile networks works?

Mobile telecommunications networks have very intricate infrastructures that require a lot of study time to understand.

But I will try to explain as much as possible in this article.

### Introduction

- 1st Generation Analog Systems
  - Analog Telecommunication
  - No data transmission, only voice transmission
  
- 2nd Generation Digital Systems
  - Purely digital technology
  - Circuit switching: dedicated point-to-point connections during calls
  - TDMA, GSM, CDMA
  - Circuit-switched data services (HSCSD)
  - Very slow data transmission  
  
- 2.5 – 3rd Generation
  - Mix of circuit switching and packet-switching
  - Packet-switched data
  - Allows mobile networks to transmit IP packets to the Internet
  - GPRS, EDGE, CDMA2000
  
- 4th Generation
  - All IP-based secured packet switched network (IPv6 supported)
  - Voice also transmitted over IP
  - LTE, WiMAX
  
### Differences in structure, equipment and protocols  

2G | 3G | 4G/LTE
------------ | ------------- | -------------
BTS | NodeB	| eNodeB
BSC | merged into NodeB | merged into eNodeB
MSC/VLR | RNC | MME, MSC Proxy
HLR | HLR, IMS HSS, HE | LTE SAE HSS, SDR/SDM
STP | STP,SG | Legacy STP
GGSN | GGSN | PDN GW
SGSN | SGSN | MME/SGW
IN | IN/PCRF | PCRF
RAN Firewall | RAN Firewall | SeGW

### LTE and 3G User Connection

![LTE User con](/mobile-network/imgs/userconlte.png)

![LTE System Arch](/mobile-network/imgs/ltesystemarch02.png)

  E-UTRAN consists of eNodeBs (i.e., base
  stations).
  
  It manages the radio communication between
  eNodeB and UE and facilitates communication
  between the UE and EPC
  
  S-GW: All user IP packets are transferred through the S-GW,
  which serves as the local mobility anchor when the UE moves
  between eNodeBs.
  
  P-GW: The PDN (packet data network) Gateway is responsible for
  IP address allocation for the UE, QoS enforcement and flow-based charging.
  
## But how to hack a mobile network?

There are hundreds of possibilities, many flaws, many types of attacks. 

### What i need to hack a mobile network, some hardware?

* A Android smartphone
* The most complete penetration testing platform (**ANDRAX**)

Wait a minute ... just need my smartphone and ANDRAX to do this?

Yeah!

A smartphone is a transceiver, and already comes with all the necessary hardware, thanks to the technology of the new networks and the powerful Linux environment in Android we can access the STACK of the protocols and put these networks in our hands!

### 3G/4G STACK Blocks on Android devices

Everything in Linux is file, to access the interfaces of the modems in Android we have to access the "block devices" located in /dev

![3G/4G Dev blocks](/mobile-network/imgs/andraxdevblocks.jpg)

For example in my device we can see ours TTY to SCOMM with chipset, in pts dir we have our umts modem SCOMM too.

Using these SCOMM blocks we can elevate the STACK to inject protocols flaws.

### The first step to hack a mobile network

First use the "simplest" attack which is very complex, attack based on internal routing failure on NodeB or ENodeB.

To do this we have to disconnect our WiFi network and raise the mobile network interface which in Android is called "rmnet"

![rmnet Android](/mobile-network/imgs/andraxrmnet.jpg)

We can see that in my case I am connected in ENodeB with ip 10.117.200.51 and mask 255.255.255.0, that is, my network block is from 10.117.200.1 to 10.117.200.254

To list the possible breakpoints on this network I have to use nmap. but with very delicate parameters because the SeGW firewall is very violent and one of the best designed structures to identify scanners!

Maybe -T1 can help you!

We will use some of these active devices in the same netblock to jump out of that gateway and enter the SIGTRAN or DIAMETER if you are in a very old (2G) network in the SS7

#### SigPloit Framework

![SigPloit ANDRAX](/mobile-network/imgs/andraxsigploit.jpg)

With SigPloit framewrok we can do some SIGNALING hacks but not something advanced like do it by our hands, SigPloit is included on ANDRAX and it is good to you start learn a bit about SIGNALING hacks. Combined with others attacks this can be very dangerous!

### Major attacks on mobile networks

* Routing failures
* SIGNALING Attacks
* HLR/HSS Injection
* HLR/HSS Poisoning
* PTP Flood
* EPC Hijack
* DIAMETER Fuzzing
* EPC DNS Spoof
* EPC DNS Recache

## What we can do hacking a mobile network?

* Free internet :)
* Control data
* Spoof data
* Hijack data
* Put users in a botnet
* DoS
* Clone clients
* ... The possibilities are endless!

That's all for today! If you would like a series of practical classes on mobile networks hacking enroll in our [Hacking training with ANDRAX](http://androidhacking.thecrackertechnology.com/)

Until next time, bye!
