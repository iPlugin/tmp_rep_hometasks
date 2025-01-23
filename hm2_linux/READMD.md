![alt text](screen/logo.png)
# Homework 2 | `Deadline 18 Dec` | [Presentation](https://github.com/iPlugin/EDUC/blob/main/os_linux/pres/GlobalLogic%20Lec2%20Booting%20Linux.pdf)
## Topics in this lecture:
- GNU/Linux overview,
- What is an Operating System boot,
- CPU and ROM code, how it starts
- 1st stage - BIOS, CSM, MBR, (U)EFI,
- 2nd stage - BIOS, Grub, U-Boot, ntloader.exe
- 3rd stage - Linux Kernel, initrd, drivers,
- System boot stage:
    - GUI, userspace processes
    - Processes vs daemons
    - Background processes
- Linux distributives and their core parts
    - Init
    - Basic libraries set (GNU vs non-GNU)

## Description of the homework
### Remove the bootloader from the command line
### Recover using install cd screen/image

## Work in Progress
### Remove the bootloader from the command line
``` Bash
sudo dd if=/dev/sda bs=446 count=1 | hexdump -C | grep -i grub
```

![alt text](screen/image.png)

``` Bash
sudo dd if=/dev/sda of=/home/student/backup_boot.img bs=446 count=1
```

![alt text](screen/image-1.png)

``` Bash
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```

![alt text](screen/image-2.png)


``` Bash
reboot
```

![alt text](screen/image-3.png)

## Recover using install cd screen/image

![alt text](screen/image-4.png)

``` Bash
sudo dd if=back_boot.img of=/dev/sda bs=446 count=1
```

![alt text](screen/image-6.png)

``` Bash
reboot
```

![alt text](screen/image-7.png)