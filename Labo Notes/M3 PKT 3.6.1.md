30-10-2022

# Module 3 Packet tracer 3.6.1 - Pieter Dc

### Addressing table

![image](https://user-images.githubusercontent.com/100133263/198878575-ee962b04-2f6f-4006-bb45-267c4dbe9229.png)

### Topology

![image](https://user-images.githubusercontent.com/100133263/198879556-c47f3479-cb2b-4c07-93bc-0cb27ab1cf02.png)


# Part 1: Configure VLANs

- Configure VLANs on all three switches. Refer to the VLAN Table. Note that the VLAN names must match the values in the table exactly.

        (in global config)
        vlan 10
        name Admin
        end
        (repeat for all vlans and switches)

# Part 2: Assign Ports to VLANs

- On SWB and SWC, assign ports to the VLANs. Refer to the Addressing Table.

        conf t
        interface f0/1
        Switchport mode access
        Switchport access vlan 10
        end
        (repeat for each vlan)

        show vlan brief
        (to check if the port has been assigned correctly)

- Configure the Voice VLAN port

        conf t
        interface f0/4
        switchport mode access
        switchport access vlan 10
        mls qos trust cos
        switchport access vlan 40
        end

- Configure the virtual management interfaces

        conf t
        interface vlan 99
        ip address 192.168.99.252 255.255.255.0
        no shut
        exit
        (repeat for each switch)

<details>
Ignore this section
        
        conf t
        interface vlan 10
        ip address 192.168.10.10 255.255.255.0
        no shutdown  

        (repeat for other VLANs and interfaces)
        (this also makes the Vlans visible with show interface vlan 10)
        (instead of only show vlan brief)

</details>

# Part 3: Configure Static Trunking

- Configure the link between SWA and SWB as a static trunk. Disable dynamic trunking on this port.

        (on SWA)
        conf t
        interface g0/1
        switchport mode trunk
        switchport trunk native vlan 100
        switchport trunk allowed vlan 10,20,30,40,99,100
        switchport nonegotiate
        
        (on SWB)
        conf t
        interface g0/1
        switchport mode trunk
        switchport trunk native vlan 100
        switchport trunk allowed vlan 10,20,30,40,99,100
        switchport nonegotiate

# Part 4: Configure Dynamic Trunking

- Assume that the trunk port on SWC is set to the default DTP mode for 2960 switches. Configure G0/2 on SWA so that it successfully negotiates trunking with SWC.

        (on SWC)
        conf t
        interface g0/1
        switchport trunk native vlan 100

        (on SWA)
        conf t
        interface g0/2
        switchport trunk native vlan 100
        switchport mode dynamic desirable


# Extra Trunk commands

- Verify trunk config

        show interface g0/1 switchport
        
- Reset trunk config

        interface g0/1
        no switchport trunk allowed vlan
        no switchport trunk native vlan
        end

- Disable nonegotiate

        interface g0/1
        no switchport nonegotiatie