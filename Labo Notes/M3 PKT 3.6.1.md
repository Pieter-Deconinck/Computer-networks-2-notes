30-10-2022

# Module 3 Packet tracer 3.6.1 - Pieter Dc

### Addressing table

![image](https://user-images.githubusercontent.com/100133263/198878575-ee962b04-2f6f-4006-bb45-267c4dbe9229.png)

### Topology

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

# Part 3: Configure Static Trunking

# Part 4: Configure Dynamic Trunking

