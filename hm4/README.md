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



# Expected result
1. Packages installation
- Vim package is installed
- New APT repository is added: ppa:atareao/telegram
- Packages list from APT repository is updated
- New ”telegram” package from APT repository is installed
- Installed “telegram” package is run in Ubuntu GUI.
- Installed “telegram” package is removed using CLI
- Previously added telegram PPA repo is removed from CLI.
- Used commands, and arguments are provided for Homework evaluation.
- Screenshot of the installed and running telegram APP is provided.
- “Telegram” app full (wide) process entry is provided.
- Locations of the installed repo and GPG keys are provided.


2. Additional find task:
- “find” command arguments provided for searching files bigger than 1Gb in size across the whole FS.
- “find” command arguments provided for searching empty files and directories in the system temp directory.
- “find” command arguments provided for searching files and directories changed within the last hour in the user’s home directory.
- “find” command arguments provided for searching files and directories accessed within the last hour in the user’s home directory.
- “find” command arguments provided for searching all files with permissions for reading, writing and executing for the owner, group and others in the user’s home directory. The list of such files is provided if found.

3. Vimtutor
- Vimtutor is installed
- Vimtutor is run and tested(Do some practice).

4. Extending user’s BASH profile.
- alias “psw” is added to the user’s bash profile. Alias must display all processes for all users with wide output.
- arps() function is added to the user’s bash profile.
- Run outputs of the psw and arps are provided for evaluation.