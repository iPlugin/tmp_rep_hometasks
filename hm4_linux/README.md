![alt text](screen/logo.png)
# Homework 4 | `Deadline 24 Dec` | Linux command line intro. Part 2
## Topics in this lecture:
- Input/output streams
- Pipes
- Wildcards
- vim 
- bash / sh
- bash variables
- special variables
- Eval, $(), ``, xargs

## Description of the homework
### Packages installation
- Install vim package
- Add new APT repository from PPA and install popular “telegram” messendger: ppa:atareao/telegram
- Investigate and find-out where new PPA was stored in the FS: /etc/apt/…
- Investigate where GPG key was stored and how it was verified.
- Investigate where telegram APP files were placed to the FS.
- Run telegram APP from Ubuntu GUI.
- Find-out “telegram” app PID, process entry and parameters (use appropriate CLI app).
- Remove telegram APP using “apt-get” application from CLI.
- Remove telegram PPA repo from the system using CLI.

### Additional find task: 
- Find out how to find files bigger than 1Gb in size and perform finding operations across the whole filesystem.
- Find out how to find empty files and directories and perform finding in the system temporary directory.
- Find out how to find all files and directories in the user’s home directory which were changed within the last hour and find them.
- Perform the Item above but for the files and directories accessed within the last hour.
- Find all files with permissions for reading, writing and executing for the owner, group and others in the user’s home directory.

### Vimtutor task
- Install vimtutor
- Run and practice vimtutor

### Extending user’s BASH profile.
- Define and add alias “psw” which will display all processes for all users with wide output to the user’s bash profile.
- Add shell function “arps” displaying ARP table from the /proc/net/arp node.

## Work in Progress
### Packages installation
- Install vim package
``` Bash
sudo apt install vim
```

![alt text](screen/image.png)

``` Bash
vim --version
```

![alt text](screen/image-1.png)

- Add new APT repository from PPA and install popular “telegram” messendger: `ppa:atareao/telegram`
``` Bash
sudo add-apt-repository ppa:atareao/telegram
```

![alt text](screen/image-2.png)

``` Bash
sudo apt install telegram
```

![alt text](screen/image-3.png)

- Investigate and find-out where new PPA was stored in the FS: /etc/apt/…
``` Bash
ll /etc/apt/sources.list.d
```

![alt text](screen/image-4.png)

- Investigate where GPG key was stored and how it was verified.
``` Bash
ll /etc/apt/trusted.gpg.d/
```

![alt text](screen/image-5.png)

- Investigate where telegram APP files were placed to the FS.
``` Bash
dpkg -L telegram
```

![alt text](screen/image-6.png)

- Run telegram APP from Ubuntu GUI
![alt text](screen/image-7.png)

- Find-out “telegram” app PID, process entry and parameters (use appropriate CLI app).
``` Bash
ps aux | grep "telegram"
```

![alt text](screen/image-8.png)

- Remove telegram APP using “apt-get” application from CLI.
``` Bash
sudo apt-get remove telegram
```

![alt text](screen/image-9.png)

- Remove telegram PPA repo from the system using CLI.
``` Bash
sudo add-apt-repository --remove ppa:atareao/telegram
```

![alt text](screen/image-10.png)


### Additional find task: 
- Find out how to find files bigger than 1Gb in size and perform finding operations across the whole filesystem.
``` Bash
sudo find / -type f -size +1G 2> /dev/null
```

![alt text](screen/image-11.png)

- Find out how to find empty files and directories and perform finding in the system temporary directory.
``` Bash
sudo find /tmp -empty
```

![alt text](screen/image-12.png)

- Find out how to find all files and directories in the user’s home directory which were changed within the last hour and find them.
``` Bash
sudo find ~ -mmin -60 2> /dev/null
```

![alt text](screen/image-13.png)

- Perform the Item above but for the files and directories accessed within the last hour.
``` Bash
sudo find ~ -amin -60 2> /dev/null
```

![alt text](screen/image-14.png)

- Find all files with permissions for reading, writing and executing for the owner, group and others in the user’s home directory.

``` Bash
sudo find ~ -type f -perm 777
```

![alt text](screen/image-15.png)

### Vimtutor task
- Install vimtutor

``` Bash
which vimtutor
```

![alt text](screen/image-16.png)

- Run and practice vimtutor

``` Bash
vimtutor
```

![alt text](screen/image-17.png)


### Extending user’s BASH profile.
- Define and add alias “psw” which will display all processes for all users with wide output to the user’s bash profile.

``` Bash
vim ~/.bashrc
```

`Перейти в insert режим Esc -> i`

![alt text](screen/image-18.png)

`Зберегти і вийти Esc -> :wq`

``` Bash
source ~/.bashrc
psw
```

![alt text](screen/image-21.png)

- Add shell function “arps” displaying ARP table from the /proc/net/arp node.

``` Bash
vim ~/.bashrc
```

`Перейти в insert режим Esc -> i`

![alt text](screen/image-19.png)

`Зберегти і вийти Esc -> :wq`

``` Bash
source ~/.bashrc
arps
```

![alt text](screen/image-20.png)