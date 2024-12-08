

| VLAN ID | Name | Subnet |
| ------- | ---- | ------ |
|         |      |        |
|         |      |        |
|         |      |        |

| Vlan ID | Name        | Subnet           |
| ------- | ----------- | ---------------- |
| 1       | Normal      | 192.168.0.1/24   |
| 2       | Hypvervisor | 100.64.0.0/24    |
| 3       | VM_Internet | 100.65.0.0/24    |
| 5       | VM_Intranet | 100.66.0.0/2 4   |
| 8       | Normal_Alt  | 192.168.254.1/24 |
| 10      | CCTV        | 169.254.0.0/24   |
| 11      | Guest       | 172.16.0.0/24    |
| 20      | SW<>FW      | 10.10.10.2/24    |
|         |             |                  |
|         |             |                  |
```
# Enable mode
enable

  

# Configuration mode
configure terminal

  

# VLAN 1

vlan 1

interface ve 1

ip address 192.168.0.1 255.255.255.0

  

# VLAN 2

vlan 2

name Hypvervisor

interface ve 2

ip address 100.64.0.1 255.255.255.0

  

# VLAN 3

vlan 3

name VM_Internet

interface ve 3

ip address 100.65.0.1 255.255.255.0

  

# VLAN 5

vlan 5

name VM_Intranet

interface ve 5

ip address 100.66.0.1 255.255.255.0

  

# VLAN 10

vlan 10

name CCTV

interface ve 10

ip address 169.254.0.1 255.255.255.0

  

# VLAN 11

vlan 11

name Guest

interface ve 11

ip address 172.16.0.1 255.255.255.0

  

# VLAN 9

vlan 9

name SW<>FW

interface ve 9

ip address 10.10.10.1 255.255.255.0

  

# Save configuration

write memory

  

# Exit configuration mode

exit
```