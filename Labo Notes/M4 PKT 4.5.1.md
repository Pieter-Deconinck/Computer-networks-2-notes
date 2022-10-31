31-10-2022

# Module 3 Packet tracer 3.5.1 - Pieter Dc

### Addressing table

![image](https://user-images.githubusercontent.com/100133263/198980241-9fd7400e-e8ed-429d-8f8d-301c341c628c.png)

### Topology

![image](https://user-images.githubusercontent.com/100133263/198980196-038e5954-8fd6-415f-a7e4-4a1c226ecc76.png)


# Instructions

- Assign IP addressing to R1 and S1 based on the Addressing Table. + configure inter VLAN routing

        (R1 in global config)
        interface g0/0
        ip address 172.17.25.2 255.255.255.252
        no shutdown

        interface g0/1.10
        description Default Gateway for VLAN 10
        encapsulation dot1Q 10
        ip address 172.17.10.1 255.255.255.0
        (repeat for other interfaces)
        
        interface g0/1
        description Trunk link to s1
        no shutdown
        exit

- Configure the default gateway on S1.

        (S1 in global config)
        interface vlan 99
        ip address 172.17.99.10 255.255.255.0
        no shutdown
        ip default-gateway 172.17.99.1

- Create, name, and assign VLANs on S1 based on the VLAN and Port Assignments Table. Ports should be in access mode. Your VLAN names should match the names in the table exactly.

        (S1 in global config)
        vlan 10
        name Faculty/Staff
        exit
        (repeat for each vlan)

        show vlan
        (to verify vlans have been created)

        (S1 in global config)
        interface range f0/11 - 17
        switchport mode acces
        switchport acces vlan 10
        exit
        (repeat for other interfaces)

- Configure G0/1 of S1 as a static trunk and assign the native VLAN.

        (S1 in global config)
        interface g0/1
        switchport mode trunk
        switchport trunk native vlan 88
        switchport trunk allowed vlan 10,20,30,88,99
        switchport nonegotiate

-  All ports that are not assigned to a VLAN should be disabled.

        (S1)
        show ip interface
        (to check which ports are open)
        
        conf t
        interface range f0/1-5
        shutdown
        exit

        interface range g0/2
        shutdown
        exit

