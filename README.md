# vlan-lab
We must locate the misconfiguration for the lab troubleshooting:
1/ G0/1.10 subinterface is administratively down.
2/PC3 is configured with the wrong default gateway address.
3/On S1, Interface G0/1 is set up as an access port rather than a trunk port.
4/Subinterface  VLAN assignments on R1 are changed. There are mismatches between the configured assignments and those in the Addressing Table.


We need to follow these steps in order to correct the misconfiguration :
1/R1(config)#interface g0/1.10
R1(config-subif)#no shutdown
R1(config-subif)#exit
R1(config)#interface g0/1.10
R1(config-subif)#no encapsulation dot1Q 
R1(config-subif)#int g0/1.30
R1(config-subif)#no encapsulation dot1Q 
R1(config-subif)#exit
R1(config)#int g0/1.10
R1(config-subif)#encapsulation dot1Q 10
R1(config-subif)#ip address 172.17.10.1 255.255.255.0
R1(config-subif)#
R1(config-subif)#int g0/1.30
R1(config-subif)#encapsulation dot1Q 30
R1(config-subif)#ip address 172.17.30.1 255.255.255.0


2/S1(config)#interface g0/1
S1(config-if)#switchport mode trunk
