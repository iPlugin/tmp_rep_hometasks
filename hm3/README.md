# Вітаю Yanina Husarevych

# Description of the homework
1. Block/Allow file deletion from directory by other users:
- Create test_tmp directory in /home folder from using the root user permissions
- Set rwx permissions for the owner, group and others to /home/test_tmp
- Create test TEXT files in /home/test_tmp folder with testuser1 permissions
- Create test TEXT files in /home/test_tmp folder with testuser2 permissions
- Block file deletion from this directory by other users
- Try deleting files belonging to testuser1 from the testuser2 account
- Allow file deletion from this directory by other users
- Try deleting files belonging to testuser1 from the testuser2 account
- Provide Terminal screenshots of the performed operations.

2. Verify that SUID bit does not work for executable Shell scripts.
- Create suid_test.sh script from the testuser1 credentials with the following content: “#!/bin/sh whoami”
- Set execution bit for everyone
- Try executing test_suid.sh script from different users
- Try changing UIDs to the different users to test_suid.sh and repeat Item# 3
- Provide Terminal screenshots of the performed operations.

3. Changing the Shell for the users:
- Install zsh
- Install tcsh
- Change shell to zsh for the user testuser1
- Log-in to CLI with the testuser1 credentials
- Output processes list for the testuser1
- Output processes list for the testuser2
- Change shell to tcsh for the user testuser2
- Log-in to CLI with the testuser2 credentials
- Output processes list for the root user
- Capture Screenshots for each of the Item above.

4. Exploring the Most useful commands:
- Create a table (text, excel/google sheet, e.t.c.) for the Most useful commands Chapter which would consist of the following rows:Brief Description/Command type(binary, shell built-in, e.t.c.)/Permissions(In case of separate binary)/Usage(Short or Traditional usage).

5. Find task:
- Find all files containing SUID bit in.
- Provide find options used
- Capture and provide an output for evaluation

# Work in Progress



# Expected result
1. Block/Allow file deletion from directory by other users:
Items #1-8 performed, 
Screenshots provided.

2. Verify that SUID bit does not work for executable Shell scripts:
Item #1-4 performed,
Screenshots provided

3. Changing the Shell for the users:
Items #1-10 performed, 
Screenshots provided.

4. Exploring the Most useful commands:
Extended table with additional information for the “Most useful commands” is created and provided for evaluation

5. Find task:
Find command arguments is provided
List of files with SUID bit is provided for evaluation