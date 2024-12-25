# Вітаю Yanina Husarevych

# Description of the homework
1. Packages installation
- Install vim package
- Add new APT repository from PPA and install popular “telegram” messendger: ppa:atareao/telegram
- Investigate and find-out where new PPA was stored in the FS: /etc/apt/…
- Investigate where GPG key was stored and how it was verified.
- Investigate where telegram APP files were placed to the FS.
- Run telegram APP from Ubuntu GUI
- Find-out “telegram” app PID, process entry and parameters (use appropriate CLI app).
- Remove telegram APP using “apt-get” application from CLI.
- Remove telegram PPA repo from the system using CLI.

2. Additional find task: 
- Find out how to find files bigger than 1Gb in size and perform finding operations across the whole filesystem.
- Find out how to find empty files and directories and perform finding in the system temporary directory.
- Find out how to find all files and directories in the user’s home directory which were changed within the last hour and find them.
- Perform the Item above but for the files and directories accessed within the last hour.
- Find all files with permissions for reading, writing and executing for the owner, group and others in the user’s home directory.

3. Vimtutor task
- Install vimtutor
- Run and practice vimtutor

4. Extending user’s BASH profile.
- Define and add alias “psw” which will display all processes for all users with wide output to the user’s bash profile.
- Add shell function “arps” displaying ARP table from the /proc/net/arp node.

# Work in Progress
1. Packages installation
- Install vim package

``` Bash
sudo apt install vim
vim --version
```

![alt text](image.png)

- Add new APT repository from PPA and install popular “telegram” messendger: `ppa:atareao/telegram`

``` Bash
sudo add-apt-repository ppa:atareao/telegram
```

![alt text](image-1.png)

``` Bash
sudo apt install telegram
```

![alt text](image-4.png)

- Investigate and find-out where new PPA was stored in the FS: /etc/apt/…

``` Bash
ll /etc/apt/sources.list.d
```

![alt text](image-2.png)

- Investigate where GPG key was stored and how it was verified.

``` Bash
ll /etc/apt/trusted.gpg.d/
```

![alt text](image-3.png)

- Investigate where telegram APP files were placed to the FS.

``` Bash
dpkg -L telegram
```

![alt text](image-5.png)

- Run telegram APP from Ubuntu GUI

![alt text](image-6.png)

- Find-out “telegram” app PID, process entry and parameters (use appropriate CLI app).

``` Bash
pidof telegram
ps aux | grep "telegram"
```

![alt text](image-7.png)

- Remove telegram APP using “apt-get” application from CLI.

``` Bash
sudo apt-get remove telegram
```

![alt text](image-8.png)

- Remove telegram PPA repo from the system using CLI.

``` Bash
sudo add-apt-repository --remove ppa:atareao/telegram
```

![alt text](image-9.png)

2. Additional find task: 

- Find out how to find files bigger than 1Gb in size and perform finding operations across the whole filesystem.

``` Bash
sudo find / -type f -size +1G 2> /dev/null
```

![alt text](image-10.png)

- Find out how to find empty files and directories and perform finding in the system temporary directory.

``` Bash
sudo find /tmp -empty
```

![alt text](image-11.png)

- Find out how to find all files and directories in the user’s home directory which were changed within the last hour and find them.

``` Bash
sudo find ~ -mmin -60 2> /dev/null
```

![alt text](image-12.png)

- Perform the Item above but for the files and directories accessed within the last hour.

``` Bash
sudo find ~ -amin -60 2> /dev/null
```

![alt text](image-13.png)

- Find all files with permissions for reading, writing and executing for the owner, group and others in the user’s home directory.

``` Bash
sudo find ~ -type f -perm 777
```

![alt text](image-14.png)

3. Vimtutor task
- Install vimtutor

``` Bash
which vimtutor
```

![alt text](image-15.png)

- Run and practice vimtutor

``` Bash
vimtutor
```

![alt text](image-16.png)

4. Extending user’s BASH profile.

- Define and add alias “psw” which will display all processes for all users with wide output to the user’s bash profile.

``` Bash
vim ~/.bashrc
source ~/.bashrc
```

`Перейти в insert режим Esc -> i`

![alt text](image-17.png)

- Add shell function “arps” displaying ARP table from the /proc/net/arp node.

``` Bash
vim ~/.bashrc
source ~/.bashrc
```

![alt text](image-18.png)

`Зберегти і вийти Esc -> :wq`

``` Bash
arps
```

![alt text](image-19.png)