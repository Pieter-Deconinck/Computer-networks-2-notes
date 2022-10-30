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

<details>
        conf t
        interface vlan 10
        ip address 192.168.10.10 255.255.255.0
        no shutdown  

        (repeat for other VLANs and interfaces)
        (this also makes the Vlans visible with show interface vlan 10)
        (instead of only show vlan brief)
</details>



# Part 3: Configure Static Trunking

# Part 4: Configure Dynamic Trunking

