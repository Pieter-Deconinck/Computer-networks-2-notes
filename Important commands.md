# Switch

## Basics
``enable``
``configure terminal``  
``hostname S1``  
``enable secret class``  
``line console 0``  
``password cisco``  
``login``  
``exit``  
``line vty 0 4``  
``password cisco``  
``login``  
``exit``  
``service password-encryption``  
``banner motd "Authorized Access Only!"``
``exit``
``copy running-config startup-config``

## Configure management interface
Enter global config: ``configure terminal``  
Enter switch virtual interface: ``interface vlan 99``  
configure management interface ipv4: ``ip address 192.168.0.10 255.255.255.0``  
configure management interface ipv6: ``ipv6 address 2001:db8:acad:99::1/64``  
enable management interface: ``no shutdown``  
copy running to startup: ``copy running-config startup-config``  

## Configure Default gateway
configure default gateway: ``ip default-gateway 192.168.0.1`` in global config  

## Enable ipv6
Enable ipv6:  ``sdm prefer dual-ipv4-and-ipv6 default`` in global config, then reload the switch  

## Verify config
``show ip interface brief``  
``show ipv6 interface brief``  

## Configure switch ports
``interface FastEthernet 0/1`` in global config  
set the duplex to full: ``duplex full``  
set interface speed: ``speed 100``  

## Verification commands
Display interface status and config: ``show interfaces [interface-id]``  
``show startup-config``  
``show running-config``  
info flash file system: ``show flash``  
info hardware and software: ``show version``  
show previous commands: ``show history``  
``show ip interface [interface id]``  
``show ipv6 interface [interface id]``  
show macc address table: ``show mac-address-table`` or ``show mac address-table``  

## Configure SSH (Switch needs hostname and correct network settings)
Verify ssh: ``show ip ssh`` if command unrecognized switch doesnt support ssh  
configure ip domain name: ``ip domain-name cisco.com`` in global config  
generate RSA key pairs: ``crypto key generate rsa`` How many bits: ``1024`` in global config  
configure user authentication: ``username admin secret ccna``  in global config  
configure vty lines: ``line vty 0 15``  
``transport input ssh``  
``login local``  
enable ssh version 2: ``ip ssh version 2`` in global config  


# Router

## Basics
see switch basics

## Configure Router interfaces
``interface gigabitethernet 0/0/0`` in global config  
``ip address 192.168.0.1 255.255.255.0``   
``ipv6 address 2001:db8acad:1::1/64``   
``description Link to LAN 1``   
``no shutdown``   

## Configure Loopback interfaces
``interface loopback [number]`` in global config
`` ip address [ip-address] [subnet-mask]``   


## Verification commands
``show ip interface brief``  
``show ipv6 interface brief``  
``show ip route``  
``show ipv6 route``  
``show ip route static``  
``show ip route  [network]``  
``show running-cvonfig | section ip route``

## Pipeline commands/Filtering commands
`` (command) | section``  
`` (command) | include``  
`` (command) | exclude``  
`` (command) | begin``  

## configure static route
route to network 10.0.4.0/24 via 10.0.3.2:``ip route 10.0.4.0 255.255.255.0 10.0.3.2``

## Configure default static route
ipv4 ``ip route 0.0.0.0 0.0.0.0 [ipadressrouternexthop] | [exitinterface]``  
ipv6 ``ipv6 route ::/0 [ipv6addressrouternexthop] | [exit-intf]``
configuring floating static routes(backup routes)  
same as above but with an administrative distance added at the end
ex: ip route 0.0.0.0 0.0.0.0 10.10.10.2 5 gives it administrative distance of 5

## Static host route
ipv4 ``ip route 209.165.200.238 255.255.255.255 198.51.100.2``  
ipv6 ``ipv6 route 2001:db8:acad:2::238/128 2001:db8:acad:1::2``  
ipv6 link local ``ipv6 route 2001:db8:acad:2::238/128 serial 0/1/0 fe::2``  


# Troubleshooting commands
ping ``ping 192.168.0.1`` verify layer3  
traceroute ``tracert 192.168.0.1`` verify path, uses icmp echo reply messages to determine hops  
``show ip route``  displays routing table
``show ip interface brief``  display status of interfaces 
``show cdp neighbors``  displays list of directly connected cisco devices for layer1 and layer2
