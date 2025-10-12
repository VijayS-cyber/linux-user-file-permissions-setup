# linux-user-file-permissions-setup
Step-by-step guide to create two Linux user accounts and set file permissions so only one user can read/write a specific file, ensuring secure access control. Useful for system administration and security practice.
1.	Open a terminal with sudo privileges
o	Access your Linux system and open a terminal.
o	Ensure you have administrative (sudo) rights to create users.
2.	Create the first user
o	Run: sudo adduser user1
o	Follow the prompts to set a password and user details.
3.	Create the second user
o	Run: sudo adduser user2
o	Similarly, set a password and complete the setup.
4.	Switch to user1
Run: su - user1
o	Enter the password for user1 when prompted.
5.	Create a private file
o	Run: echo 'This is a private file.' > /home/user1/private.txt
o	This creates a file in user1's home directory.
6.	Set file ownership
o	Run: sudo chown user1:user1 /home/user1/private.txt
o	Ensures the file is owned by user1 and their primary group.
7.	Set restrictive permissions
o	Run: chmod 600 /home/user1/private.txt
o	This allows only the owner (user1) to read and write the file.
8.	Verify the permissions
o	Run: ls -l /home/user1/private.txt
o	You should see output like: -rw------- 1 user1 user1 ...
9.	Switch to user2
Open a new terminal or log out and run: su - user2
o	Enter user2's password.
10.	Test access from user2
o	Try: cat /home/user1/private.txt
o	This should fail with a permission denied error, confirming user2 has no access.
11.	Return to user1 to confirm access
o	Switch back to user1 and verify they can still read and write the file.
This setup ensures that only user1 has read and write access, while user2 (and all others) are denied access
