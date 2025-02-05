![alt text](screen/logo.png)
# Homework 11 | `Deadline 5 February` | [Presentation](https://github.com/iPlugin/EDUC/blob/main/os_network/pres/GlobalLogic%20Lec3%20Networking%20Tools.pdf)
## Topics in this lecture:
- Configuration of the operating system:
    - hostname
    - ifconfig / iproute2
    - route / iproute2
    - netstat
    - dhcp
- Debugging OS configuration:
    - ping
    - traceroute / mtr
    - host
    - dig
- System network services:
    - ifup
    - connman
    - netplan
    - NetworkManager

## Description of the homework
- There are 3 computers in the physical network: A, B, C. There is a dedicated IP addresses range that can be used 10.10.10.0 up to 10.10.10.255. Please explain a network configuration that need to be done in order to achieve following results:
    - Computer A can directly communicate to B
    - Computer B can directly communicate with C
    - Computer A can not communicate directly with C
    - Each computer shall have a hostname and FQDN (hosta, hostb, hostc and domain name can be testdomain.exemple)
    - Every computer shall be able to resolve both hostname and FQDN into proper IP address
- Please provide all required commands to configure all three computers

## Work in Progress