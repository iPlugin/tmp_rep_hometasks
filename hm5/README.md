![alt text](screen/logo.png)

# Вітаю Yanina Husarevych
## Description of the homework
### Block/Allow file deletion from directory by other users:
- Create test_tmp directory in /home folder from using the root user permissions
- Set rwx permissions for the owner, group and others to /home/test_tmp
- Create test TEXT files in /home/test_tmp folder with testuser1 permissions
- Create test TEXT files in /home/test_tmp folder with testuser2 permissions
- Block file deletion from this directory by other users
- Try deleting files belonging to testuser1 from the testuser2 account
- Allow file deletion from this directory by other users
- Try deleting files belonging to testuser1 from the testuser2 account
- Provide Terminal screenshots of the performed operations.

### Verify that SUID bit does not work for executable Shell scripts.
- Create suid_test.sh script from the testuser1 credentials with the following content: “#!/bin/sh whoami”
- Set execution bit for everyone
- Try executing test_suid.sh script from different users
- Try changing UIDs to the different users to test_suid.sh and repeat Item# 3
- Provide Terminal screenshots of the performed operations.

### Adding/Creating New Storage Devices to the Linux OS:
- Add 3x new Disk controllers to the Virtual Machine: SCSI, SAS and NVME(NOTE: Extension pack to VBox must be added in order to use NVME Controllers).
- Add 2xNew HDDs to each of the Disk Controllers (Select VDI, Dynamic Allocation 1Gb size)
- Verify which device nodes were created in the /dev folder for each of the Drives added.
- Create MBR partition table with a total of 4x partitions similar in size ( 2x Primary and 2x Logical partitions)  for the 1st drive for SCSI and NVME disk controllers using parted utility. (25%, 50%, 75%,100% can be used when specifying partition size)
- Create GPT partition table with a total of 4x partitions similar in size for the 2nd drive for SCSI and NVMEdisk controllers using parted utility. (25%, 50%, 75%,100% can be used when specifying partition size).
- Create MBR partition table with a total of 4x partitions similar in size ( 2x Primary and 2x Logical partitions)  for the 1st drive for SAS disk controller using fdisk utility
- Create GPT partition table with a total of 4x partitions similar in size for the 2nd drive for SAS disk controller using fdisk utiliy.
- Compare Partition Table display information using fdisk and parted utilities.
- Verify how disk device nodes were changed in the /dev folder for each of the drives added.
- Create 24x subfolders in the /mnt directory with the following names: nvme0n[12]_ext4, nvme0n[12]_xfs, nvme0n[12]_reiserfs, nvme0n[12]_btrfs, sd[bcde]_ext4, sd[bcde]_xfs, sd[bcde]_reiserfs, sd[bcde]_btrfs.
- Create 4x different filesystems per each of the Disk Drives: xfs4, xfs, reiserfs, btrfs using mkfs.* utilities (NOTE:Appropriate FS*progs packages would probably need to be installed in order to get desired utilities for FS creation, follow bash hints in order to get them installed quickly). Use default options for creating FSs.
- Investigate each FS creation logs and record them somewhere for the later evaluation.
- Mount created disk node devices with created FS to the appropriate folder.
- Evaluate and investigate the system  mount  table and save output somewhere for the later evaluation.
- Investigate available free disk space for each of the filesystems mounted (Also record output to some file for the later evaluation).

## Work in Progress
### Block/Allow file deletion from directory by other users:
- Create test_tmp directory in /home folder from using the root user permissions
``` Bash
sudo su
mkdir /home/test_tmp
```
![alt text](image.png)

``` Bash
ll /home
```
![alt text](image-1.png)

- Set rwx permissions for the owner, group and others to /home/test_tmp
``` Bash
chmod 777 /home/test_tmp
```
![alt text](image-2.png)

``` Bash
ll /home
```
![alt text](image-3.png)

- Create test TEXT files in /home/test_tmp folder with testuser1 permissions
``` Bash
touch /home/test_tmp/test1.txt
chown testuser1:testgroup1 /home/test_tmp/test1.txt
```
![alt text](image-4.png)

``` Bash
ll /home/test_tmp
```
![alt text](image-5.png)

- Create test TEXT files in /home/test_tmp folder with testuser2 permissions
``` Bash
touch /home/test_tmp/test2.txt
chown testuser2:testgroup2 /home/test_tmp/test2.txt
```
![alt text](image-6.png)

``` Bash
ll /home/test_tmp
```
![alt text](image-7.png)

- Block file deletion from this directory by other users
``` Bash
chmod 775 /home/test_tmp
```
![alt text](image-8.png)

``` Bash
ll /home/test_tmp
```
![alt text](image-9.png)

- Try deleting files belonging to testuser1 from the testuser2 account
``` Bash
su testuser2
rm -f /home/test_tmp/test1.txt
```
![alt text](image-10.png)

- Allow file deletion from this directory by other users
``` Bash
chmod 777 /home/test_tmp
```
![alt text](image-11.png)

``` Bash
ll /home/test_tmp
```
![alt text](image-12.png)

- Try deleting files belonging to testuser1 from the testuser2 account
``` Bash
su testuser2
rm -f /home/test_tmp/test1.txt
```
![alt text](image-13.png)

``` Bash
ls -l /home/test_tmp
```
![alt text](image-14.png)

### Verify that SUID bit does not work for executable Shell scripts.
- Create suid_test.sh script from the testuser1 credentials with the following content: “#!/bin/sh whoami”
``` Bash
su testuser1
```
![alt text](image-15.png)

``` Bash
nano /home/test_tmp/suid_test.sh
# Ctrl+O -> Enter -> Ctrl+X
chmod u+s /home/test_tmp/suid_test.sh
```
![alt text](image-16.png)

``` Bash
ls -l /home/test_tmp/
```
![alt text](image-17.png)

``` Bash
cat /home/test_tmp/suid_test.sh
```
![alt text](image-18.png)

- Set execution bit for everyone
``` Bash
chmod a+x /home/test_tmp/suid_test.sh
```
![alt text](image-19.png)

``` Bash
ls -l /home/test_tmp/
```
![alt text](image-20.png)

---
**І тут почалося найцікавіше щоб я не робив воно виконує від імені хто виконує**

- Try executing test_suid.sh script from different users
``` Bash
whoami # переконатися що я testuser1
/home/test_tmp/suid_test.sh
su testuser2
/home/test_tmp/suid_test.sh
```
![alt text](image-21.png)

- Try changing UIDs to the different users to test_suid.sh and repeat Item# 3
``` Bash
sudo chown testuser2 /home/test_tmp/suid_test.sh
```
![alt text](image-22.png)

**Я пробував активувати suid:**
``` Bash
sudo nano /etc/default/grub
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash fs.suid_dumpable=1"
sudo update-grub
sudo reboot
##############################
mount | grep "$(df / | tail -1 | awk '{print $1}')"
# Output:
# /dev/sda2 on / type ext4 (rw,relatime)
```
**Все стверджує що має працювати але...**

### Adding/Creating New Storage Devices to the Linux OS:
- Add 3x new Disk controllers to the Virtual Machine: SCSI, SAS and NVME(NOTE: Extension pack to VBox must be added in order to use NVME Controllers).


- Add 2xNew HDDs to each of the Disk Controllers (Select VDI, Dynamic Allocation 1Gb size)


- Verify which device nodes were created in the /dev folder for each of the Drives added.


- Create MBR partition table with a total of 4x partitions similar in size ( 2x Primary and 2x Logical partitions)  for the 1st drive for SCSI and NVME disk controllers using parted utility. (25%, 50%, 75%,100% can be used when specifying partition size)


- Create GPT partition table with a total of 4x partitions similar in size for the 2nd drive for SCSI and NVMEdisk controllers using parted utility. (25%, 50%, 75%,100% can be used when specifying partition size).


- Create MBR partition table with a total of 4x partitions similar in size ( 2x Primary and 2x Logical partitions)  for the 1st drive for SAS disk controller using fdisk utility


- Create GPT partition table with a total of 4x partitions similar in size for the 2nd drive for SAS disk controller using fdisk utiliy.


- Compare Partition Table display information using fdisk and parted utilities.


- Verify how disk device nodes were changed in the /dev folder for each of the drives added.


- Create 24x subfolders in the /mnt directory with the following names: nvme0n[12]_ext4, nvme0n[12]_xfs, nvme0n[12]_reiserfs, nvme0n[12]_btrfs, sd[bcde]_ext4, sd[bcde]_xfs, sd[bcde]_reiserfs, sd[bcde]_btrfs.


- Create 4x different filesystems per each of the Disk Drives: xfs4, xfs, reiserfs, btrfs using mkfs.* utilities (NOTE:Appropriate FS*progs packages would probably need to be installed in order to get desired utilities for FS creation, follow bash hints in order to get them installed quickly). Use default options for creating FSs.


- Investigate each FS creation logs and record them somewhere for the later evaluation.


- Mount created disk node devices with created FS to the appropriate folder.


- Evaluate and investigate the system  mount  table and save output somewhere for the later evaluation.


- Investigate available free disk space for each of the filesystems mounted (Also record output to some file for the later evaluation).