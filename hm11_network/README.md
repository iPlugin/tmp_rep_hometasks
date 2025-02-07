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
**Як я зрозумів з опису завдання треба УЯВИТИ що тебе є 3 компютера і просто накидати команди для кофігурації кожного з них. Я вирішив що уявляти не буду, а встановлю 3 віртуальні машини Ubuntu Server. Чому Ubuntu Server? Тому що вона найменше займає памяті, швидше встановиться і процесорів менше треба виділяти і тому ноутбук менше буде нагріватися**

- There are 3 computers in the physical network: A, B, C. There is a dedicated IP addresses range that can be used 10.10.10.0 up to 10.10.10.255. Please explain a network configuration that need to be done in order to achieve following results:

**IP вигляду 10.10.10.Х я не добюсь, так як треба буде DHCP маршрутизатора міняти, тому використаю 192.168.3.[11-13]**

![alt text](screen/image.png)

**Піключення до WiFi всіх одинаковий тому покажу тільки на одному pc**

``` Bash
sudo apt install network-manager
```

![alt text](screen/image-1.png)

``` Bash
nmcli device wifi list
```

![alt text](screen/image-2.png)

``` Bash
nmcli device status
```

![alt text](screen/image-3.png)

``` Bash
nmcli device wifi connect "Osvytzka13" password "61083022"
```

![alt text](screen/image-4.png)

``` Bash
nmcli device status
```

![alt text](screen/image-5.png)

``` Bash
ip a # pc-a: 192.168.3.147
```

![alt text](screen/image-6.png)

``` Bash
ip a # pc-b: 192.168.3.99
```

![alt text](screen/image-7.png)

``` Bash
ip a # pc-c: 192.168.3.148
```

![alt text](screen/image-8.png)


**Тепер задам ip адреси в межах 192.168.3.[11-13]**

``` Bash
# pc-a
cd /etc/netplan/
```

![alt text](screen/image-9.png)

``` Bash
# pc-a
ll
```

![alt text](screen/image-10.png)

``` Bash
# pc-a
sudo nano 50-cloud-init.yaml
sudo cat 50-cloud-init.yaml
```

![alt text](screen/image-14.png)

``` Bash
# pc-a
sudo netplan try
```

![alt text](screen/image-11.png)

``` Bash
# pc-a
sudo netplan apply
```

![alt text](screen/image-12.png)

``` Bash
# pc-a
ip a # 192.168.3.11
```

![alt text](screen/image-13.png)

``` Bash
# pc-b
cd /etc/netplan/
```

![alt text](screen/image-15.png)

``` Bash
# pc-b
ll
```

![alt text](screen/image-16.png)

``` Bash
# pc-b
sudo nano 50-cloud-init.yaml
sudo cat 50-cloud-init.yaml
```

![alt text](screen/image-17.png)

``` Bash
# pc-b
sudo netplan try
```

![alt text](screen/image-18.png)

``` Bash
# pc-b
sudo netplan apply
```

![alt text](screen/image-19.png)

``` Bash
# pc-b
ip a # 192.168.3.12
```

![alt text](screen/image-25.png)

``` Bash
# pc-с
cd /etc/netplan/
```

![alt text](screen/image-20.png)

``` Bash
# pc-с
ll
```

![alt text](screen/image-21.png)

``` Bash
# pc-с
sudo nano 50-cloud-init.yaml
sudo cat 50-cloud-init.yaml
```

![alt text](screen/image-22.png)

``` Bash
# pc-с
sudo netplan try
```

![alt text](screen/image-23.png)

``` Bash
# pc-с
sudo netplan apply
```

![alt text](screen/image-24.png)

``` Bash
# pc-с
ip a # 192.168.3.13
```

![alt text](screen/image-26.png)

- Each computer shall have a hostname and FQDN (hosta, hostb, hostc and domain name can be testdomain.exemple)

``` Bash
# pc-a
hostname
```

![alt text](screen/image-27.png)

``` Bash
# pc-a
sudo hostnamectl set-hostname hosta
```

![alt text](screen/image-28.png)

``` Bash
# pc-a
hostname
```

![alt text](screen/image-29.png)


``` Bash
# pc-a
sudo nano /etc/hosts
sudo cat /etc/hosts
```

![alt text](screen/image-30.png)

``` Bash
# pc-a
hostname
hostname -f
```

![alt text](screen/image-31.png)

``` Bash
# pc-b
hostname
```

![alt text](screen/image-32.png)

``` Bash
# pc-b
sudo hostnamectl set-hostname hostb
```

![alt text](screen/image-33.png)

``` Bash
# pc-b
hostname
```

![alt text](screen/image-34.png)


``` Bash
# pc-b
sudo nano /etc/hosts
sudo cat /etc/hosts
```

![alt text](screen/image-35.png)

``` Bash
# pc-b
hostname
hostname -f
```

![alt text](screen/image-36.png)

``` Bash
# pc-c
hostname
```

![alt text](screen/image-37.png)

``` Bash
# pc-c
sudo hostnamectl set-hostname hostс
```

![alt text](screen/image-38.png)

``` Bash
# pc-c
hostname
```

![alt text](screen/image-39.png)


``` Bash
# pc-c
sudo nano /etc/hosts
sudo cat /etc/hosts
```

![alt text](screen/image-40.png)

``` Bash
# pc-c
hostname
hostname -f
```

![alt text](screen/image-41.png)

- Every computer shall be able to resolve both hostname and FQDN into proper IP address

``` Bash
# pc-a -> pc-b
ping hostb
```

![alt text](screen/image-43.png)

``` Bash
# pc-a -> pc-b
ping hostb.testdomain.exemple
```

![alt text](screen/image-48.png)

``` Bash
# pc-b -> pc-c
ping hostc
```

![alt text](screen/image-45.png)

``` Bash
# pc-b -> pc-c
ping hostc.testdomain.exemple
```

![alt text](screen/image-49.png)

``` Bash
# pc-c -> pc-a
ping hosta
```

![alt text](screen/image-47.png)

``` Bash
# pc-c -> pc-a
ping hosta.testdomain.exemple
```

![alt text](screen/image-50.png)

- Computer A can directly communicate to B

``` Bash
# pc-a -> pc-b
ping 192.168.3.12
```

![alt text](screen/image-42.png)

- Computer B can directly communicate with C

``` Bash
# pc-b -> pc-c
ping 192.168.3.13
```

![alt text](screen/image-44.png)

- Computer A can not communicate directly with C

``` Bash
ping 192.168.3.13 # connect to hostc
sudo iptables -A OUTPUT -d 192.168.3.13 -j DROP
ping 192.168.3.13 # connect to hostc again
# Використав 3 команди в одному скріні щоб максимально показати різницю до і після
# Вам для зручності відокремив їх червоними лініями
```

![alt text](screen/image-51.png)


