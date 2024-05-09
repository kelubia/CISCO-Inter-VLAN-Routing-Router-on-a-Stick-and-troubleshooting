# CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting
In the Router on a Stick configuration, a single physical router interface routes traffic between multiple VLANs. 

CISCO Inter-VLAN Routing (Router on a Stick) and troubleshooting
DESCRIPTION
In this lab, I configure a Cisco router and switch to enable communication between devices in different VLANs using a single router interface. I create subinterfaces on the router corresponding to each VLAN, configure IP addresses for inter-VLAN routing, and ensure proper VLAN tagging.

Troubleshooting in this lab involves identifying and resolving common issues that may arise during the configuration process or in the operation of the inter-VLAN routing setup. This includes verifying configurations, checking connectivity between VLANs, ensuring correct VLAN tagging, checking routing tables, and troubleshooting VLAN membership on the switch.

-1 router
-SW1 -10.0.0.2/25, 10.0.0.130/25
-SW2 -10.0.0.3/25, 10.0.0.131/25
-Subnet 1- 10.0.0.2/25, 10.0.0.3/25
-Subnet 2- 10.0.0.130/25, 10.0.0.131/25

ping between pcs to confirm proper connectivity,

1![Screenshot (31)](https://github.com/kelubia/CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting/assets/98921903/d43775ae-c89d-41cb-a890-3630c3bd64ec)

2![Screenshot (32)](https://github.com/kelubia/CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting/assets/98921903/08862530-1142-4c8d-bdae-521f1523a020)


Assign PC1 and 3 to VLAN 13
3![Screenshot (33)](https://github.com/kelubia/CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting/assets/98921903/bb11ddf7-c63a-4402-a4be-26ee3ae81fa4)


Assign PC2 and 4 to VLAN 24
4![Screenshot (34)](https://github.com/kelubia/CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting/assets/98921903/fb1d7453-037a-415e-90a6-5e1ee71257db)


Configure a trunk between VLANs to carry data from one VLAN to another.
We cannot transfer data because our PCs are not in the default VLAN as our switches.
SW1
5![Screenshot (35)](https://github.com/kelubia/CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting/assets/98921903/361d4167-8ec1-4130-9039-62d0da1f7357)


SW2
6![Screenshot (36)](https://github.com/kelubia/CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting/assets/98921903/b3a91f39-9787-4003-826f-88b3e05fd59c)

 ping btw devices to be sure of proper trunk connectivity 
7![Screenshot (37)](https://github.com/kelubia/CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting/assets/98921903/c958da52-7840-4dac-b786-ecdf08242899)


configure 2 sub-interfaces between connection
Configure R1
open G0/0 
configure the default gateway for -VLAN13 to be Ip address 10.0.0.1 mask 255.255.255.0 VLAN24 ip address 10.0.0.129 255.255.255.128
encapsulation dot1q 13 and 24

8![Screenshot (38)](https://github.com/kelubia/CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting/assets/98921903/264b774f-d934-42db-abba-45e38431db84)

9![Screenshot (39)](https://github.com/kelubia/CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting/assets/98921903/e2b66ebe-a0ad-4306-ba8a-f60982ae6e28)


in other, for the Router to connect to VLAN 13 and 24, we need to remove G0/1 from the default VLAN 1.
 
10![Screenshot (42)](https://github.com/kelubia/CISCO-Inter-VLAN-Routing-Router-on-a-Stick-and-troubleshooting/assets/98921903/a7bf3145-561b-405f-b92c-1cf5bca96a30)


now, all PCs should be able to ping each other. Even though they are in separate VLANS, they are now interconnected 

