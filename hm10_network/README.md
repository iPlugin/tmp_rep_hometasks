![alt text](screen/logo.png)
# Homework 10 | `Deadline 4 February` | [Presentation](https://github.com/iPlugin/EDUC/blob/main/os_network/pres/GlobalLogic%20Lec2%20Networking%20Basics.pdf)
## Topics in this lecture:
- Model OSI
- Network subsystem in OS
- Routing
- Traffic encapsulation
- Traffic manipulation, filtering

## Description of the homework
### You’d receive dumped packets from the real internet traffic. The dump is in hex format.
- If packet is an IP packet find source and destination addresses
- If the packet was used for TCP stream find source and destination ports
- If the packet was part of HTTP session find a web page address
- If the packet was Internet Control Message Protocol find sequence number

## Work in Progress
**Для роботи з мережами я встановлю Kali Linux на віртуальну машину і буду працювати з wireshark**
```
File -> Open -> /home/student/GL_BS_capture.pcapng
```
![alt text](image.png)

```
View -> Coloring Rules
```

![alt text](image-1.png)

```
Серед перших 100 пакетів знайти (IP, TCP, HTTP, ICMP) і проаналізувати їх.
wireshark: frame.number <= 100
```

### You’d receive dumped packets from the real internet traffic. The dump is in hex format.
- If packet is an IP packet find source and destination addresses

```
wireshark: frame.number <= 100 && (ip || ipv6)
```

![alt text](image-2.png)

```
File -> Save As -> `pkt-ip.pcapng`
```

![alt text](image-3.png)

``` Bash
# Створив нову папку для файлів щоб воно не було в Downloads
ll
mkdir ~/Homework10/
mv ~/Downloads/* ~/Homework10
cd ~/Homework10
ll
```

![alt text](image-4.png)

**Створимо файл .py для аналізу даних (source and destination addresses). Ідею почерпнув з телеграму одного програміста [посилання](https://t.me/+Js93xt0NFmJiOWZi)**

``` Bash
nano analysis-pkt-ip.py
cat analysis-pkt-ip.py
```

![alt text](image-5.png)

``` Bash
# Завантажуємо залежності
sudo apt update && sudo apt install -y python3-scapy tshark
```

![alt text](image-6.png)

``` Bash
# Завантажуємо залежності 
pip3 install pyshark --break-system-packages
```

![alt text](image-7.png)

``` Bash
python3 ./analysis-pkt-ip.py pkt-ip.pcapng
```

![alt text](image-8.png)

``` Bash
whois 149.154.164.99
```

![alt text](image-9.png)

**Після того як ми переконалися що це НЕ pornhub.com від лектора Андрія 😂, можемо перейти по IP адресу**

![alt text](image-10.png)

**Нас зустрічає батько всіх телеграм ботів 😍, маю з ним проєкт в себе в [github](https://github.com/iPlugin/PROJ/tree/main/py_aiogram_linux)**

**Src addr 192.168.2.201 - Dest addr 149.154.164.99**

- If the packet was used for TCP stream find source and destination ports

```
wireshark: frame.number <= 100 && tcp
```

![alt text](image-11.png)

```
File -> Save As -> `pkt-tcp.pcapng`
```

**Так як TCP пакетів доволі багато я скористаюся тим що ви написали в групі: "Можете подивитись весь трафік і пошукати якісь цікаві вам пакети". Тому я оцінюю це як з перших 100 пакетів знайти TCP цікавий і описати його. Для мене цікавий пакет виявився під номером 87 так як він позначений не стандартним кольором. Якщо судити з Coloring Rules (скрін був десь зверху) то проблема в "Checksum Errors" або "Bad TCP"**

![alt text](image-12.png)

![alt text](image-13.png)

```
Довжина фрейму: 528 біт
Час прибуття: Jan 30, 2025 03:51:49 UTC
Фрейм типу: Bad TCP - проблема можливо в прапорцях або в віконному оновлені
```

![alt text](image-14.png)

```
MAC-адреса відправника: c0:18:03:5e:8b:0c
MAC-адреса отримувача: 2c:79:d7:2c:23:70
Тип протоколу: IPv4 (0x0800)
```

![alt text](image-15.png)

```
Адреса відправника: 192.168.2.201 - приватна ip
Адреса отримувача: 138.199.36.119 - публічна ip
Загальна довжина: 52 байти
Прапорцець: Don't Fragment
Час на життя: 64
Протокол: TCP (6)
```

![alt text](image-16.png)
![alt text](image-17.png)

```
Порт відправника: 41554 - порт згенерований ОС
Порт отримувача: 443 - порт HTTPS
Номер послідовності: 1
Номер підтвердження: 2
Корисного навантаження: 0
Прапорець TCP: ACK
```

**Я прийшов висновку що або пакет реально було втрачено або Wireshark не встиг захопити**

**Src port 41554 - Dest port 443**

- If the packet was part of HTTP session find a web page address

```
wireshark: frame.number <= 100 && http
```

![alt text](image-18.png)
![alt text](image-19.png)

```
Довжина фрейму: 5008 біт
Час прибуття: Jan 30, 2025 03:51:49 UTC
```

![alt text](image-20.png)

```
MAC-адреса відправника: c0:18:03:5e:8b:0c
MAC-адреса отримувача: 2c:79:d7:2c:23:70
Тип протоколу: IPv4 (0x0800)
```

![alt text](image-21.png)

```
Адреса відправника: 192.168.2.201 - приватна ip
Адреса отримувача: 146.190.62.39 - публічна ip якогось вебсерверу
Загальна довжина: 612 байти
Прапорцець: Don't Fragment
Час на життя: 64
Протокол: TCP (6)
```

![alt text](image-22.png)

```
Порт відправника: 57372 - порт згенерований ОС
Порт отримувача: 80 - порт HTTP
Номер послідовності: 1
Номер підтвердження: 561
Корисного навантаження: 560
Прапорець TCP: ACK, PSH
```

![alt text](image-23.png)

```
Хост: httpforever.com
Підключення: keep-alive
Upgrade-Insecure-Requests: 1 - не знав про таке, але тепер знаю. Просить перейти на https, якщо це можливо
User-Agent: Mozilla, Linux
Accept: text/html,application/xhtml+xml... - перелік форматів, які клієнт може обробити
Accept-Encoding: gzip - стиснення файлів в цей формат
Accept-Language: uk-UA - мова інтерфейсу 
```

**Фрейм 71 відповідь на запит 50 фрейм**

![alt text](image-24.png)

**Web page address (146.190.62.39) httpforever.com**


- If the packet was Internet Control Message Protocol find sequence number

```
wireshark: frame.number <= 100 && (icmp || icmpv6)
```

![alt text](image-29.png)
![alt text](image-25.png)

```
Довжина фрейму: 688 біт
Час прибуття: Jan 30, 2025 03:51:49 UTC
```

![alt text](image-26.png)

```
MAC-адреса відправника: 2c:79:d7:2c:23:70
MAC-адреса отримувача: 33:33:00:00:00:01
Тип протоколу: IPv6 (0x86dd)
```

![alt text](image-27.png)

```
Адреса відправника: fe80::1
Адреса отримувача: ff02::1
Traffic Class: 0x00 (DSCP: CS0, ECN: Not-ECT)
Hop Limit: 255 
```

![alt text](image-28.png)

```
Тип повідомлення: 136 - Neighbor Advertisement
Код: 0
Контрольна сума: 0xb285
Прапорці: Router, Override
```

**В ICMP нема "sequence number" його використовують в TCP**