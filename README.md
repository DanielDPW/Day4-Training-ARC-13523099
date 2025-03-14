<h1>Day 4 Training ARC - Daniel Pedrosa Wu (13523099)</h1>

# Packet Tracer - Basic Device Configuration

## Topology
You will receive one of three possible topologies.

## Addressing Table

| Device     | Interface     | IP Address         | Default Gateway |
|------------|-------------|--------------------|----------------|
| College    | G0/0        | 172.14.5.1/24      | N/A            |
|            |             | 172.14.10.1/24     |                |
|            | G0/1        | 2001:DB8:CAFE:1::1/64 | N/A           |
|            |             | 2001:DB8:CAFE:2::1/64 |               |
| Class-A    | VLAN 1      | 172.14.5.35/24     | 172.14.5.1     |
| Class-B    | VLAN 1      | 172.14.10.35/24    | 172.14.10.1    |
| Student-1  | NIC        | 172.14.5.50/24     | FE80::1        |
|            |             | 2001:DB8:CAFE:1::50/64 |            |
| Student-2  | NIC        | 172.14.5.60/24     | FE80::1        |
|            |             | 2001:DB8:CAFE:1::60/64 |            |
| Student-3  | NIC        | 172.14.10.50/24    | FE80::2        |
|            |             | 2001:DB8:CAFE:2::50/64 |            |
| Student-4  | NIC        | 172.14.10.60/24    | FE80::2        |
|            |             | 2001:DB8:CAFE:2::60/64 |            |

## Objectives
- Complete the network documentation.
- Perform basic device configurations on a router and a switch.
- Verify connectivity and troubleshoot any issues.

## Scenario
Your network manager is impressed with your performance in your job as a LAN technician. She would like you to demonstrate your ability to configure a router that connects two LANs. Your tasks include configuring basic settings on a router and a switch using the Cisco IOS. You will also configure IPv6 addresses on network devices and hosts. You will then verify the configurations by testing end-to-end connectivity. Your goal is to establish connectivity between all devices.

**Note:** The VLAN1 interfaces on the switches will not be reachable over IPv6.

In this activity, you will configure the **College** router, **Class-B** switch, and the **PC hosts**.

**Note:** Packet Tracer will not score some configured values; however, these values are required to accomplish full connectivity in the network.

## Requirements
- Provide the missing information in the Addressing Table.
- **Use "cisco" as the user EXEC password** for all lines.
- **Use "class" as the encrypted privileged EXEC password**.
- Encrypt all plaintext passwords.
- Configure an appropriate banner.
- Configure **IPv4 and IPv6 addressing** for the College router according to the Addressing Table.
- Configure **IPv4 addressing** for the Class-B switch according to the Addressing Table.
- Configure the **default gateway for Class-B switch**.
- Document interfaces with descriptions, including the **Class-B VLAN 1 interface**.
- Save your configurations.
- The hosts are partially configured. Complete the **IPv4 addressing** and fully configure the **IPv6 addresses** according to the Addressing Table.
- **Verify connectivity** between all devices. All devices should be able to ping all other devices with **IPv4 and IPv6**.
- **Troubleshoot and document** any issues.
- Implement the solutions necessary to enable and verify full end-to-end connectivity.

**Note:** Click **Check Results** to see your progress. Click **Reset Activity** to generate a new set of requirements.

---

# College Configuration
```sh
Current configuration : 1028 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname College
!
!
!
enable secret 5 $1$mERr$9cTjUIEqNGurQiFU.ZeCi1
!
!
!
!
!
!
ip cef
ipv6 unicast-routing
!
no ipv6 cef
!
!
!
!
license udi pid CISCO1941/K9 sn FTX1524PMLM
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 description Link to Class-A
 ip address 172.14.5.1 255.255.255.0
 duplex auto
 speed auto
 ipv6 address FE80::1 link-local
 ipv6 address 2001:DB8:CAFE:1::1/64
!
interface GigabitEthernet0/1
 description Link to Class-B
 ip address 172.14.10.1 255.255.255.0
 duplex auto
 speed auto
 ipv6 address FE80::2 link-local
 ipv6 address 2001:DB8:CAFE:2::1/64
!
interface Vlan1
 no ip address
 shutdown
!
ip classless
!
ip flow-export version 9
!
!
!
no cdp run
!
banner motd ^C Authorized Access Only ^C
!
!
!
!
line con 0
 password 7 0822455D0A16
 login
!
line aux 0
!
line vty 0 4
 password 7 0822455D0A16
 login
line vty 5 15
 login
!
!
!
end
```

# Class B Configuration
```sh
Current configuration : 1342 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname Class-B
!
!
enable secret 5 $1$mERr$9cTjUIEqNGurQiFU.ZeCi1
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 description Class-B VLAN Interface
 ip address 172.14.10.35 255.255.255.0
 ipv6 address 2001:DB8:CAFE:2::1/64
!
ip default-gateway 172.14.10.1
!
banner motd ^CWelcome to Class-B^C
!
!
!
!
!
line con 0
 password 7 0822455D0A16
 login
!
line vty 0 4
 password 7 0822455D0A16
 login
line vty 5 15
 login
!
!
!
!
end
```