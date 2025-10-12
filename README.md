# linux-user-file-permissions-setup
Step-by-step guide to create two Linux user accounts and set file permissions so only one user can read/write a specific file, ensuring secure access control. Useful for system administration and security practice.
1.	Open a terminal with sudo privileges
Access your Linux system and open a terminal.
Ensure you have administrative (sudo) rights to create users.

3.	Create the first user
Run: sudo adduser user1

Follow the prompts to set a password and user details.

4.	Create the second user
o	Run: sudo adduser user2

Similarly, set a password and complete the setup.

5.	Switch to user1
Run: su - user1

Enter the password for user1 when prompted.

6.	Create a private file
Run: echo 'This is a private file.' > /home/user1/private.txt

This creates a file in user1's home directory.

7.	Set file ownership
Run: sudo chown user1:user1 /home/user1/private.txt

Ensures the file is owned by user1 and their primary group.

8.	Set restrictive permissions
Run: chmod 600 /home/user1/private.txt

This allows only the owner (user1) to read and write the file.

9.	Verify the permissions
Run: ls -l /home/user1/private.txt

You should see output like: -rw------- 1 user1 user1 ...

10.	Switch to user2
Open a new terminal or log out and run: su - user2

Enter user2's password.

11.	Test access from user2
Try: cat /home/user1/private.txt

This should fail with a permission denied error, confirming user2 has no access.

13.	Return to user1 to confirm access
Switch back to user1 and verify they can still read and write the file.

This setup ensures that only user1 has read and write access, while user2 (and all others) are denied access
