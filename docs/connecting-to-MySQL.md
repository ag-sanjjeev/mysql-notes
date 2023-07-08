# Connecting to MySQL

To start working with MySQL, you need to establish a connection to the MySQL server. This guide will walk you through the steps to connect to a MySQL database using various methods.

## Method 1: Command Line

1. Open a command prompt or terminal window.
2. Type the following command to connect to the MySQL server:

   
```bash
   mysql -u <username> -p
```
 
Replace `<username>` with your MySQL username.

3. Press Enter and you will be prompted to enter your MySQL password. Type your password and press Enter.
	
	
   If incase your username doesn't have any password protection then follow as below.

```bash
   mysql -u <username>
```


	Note: If you are connecting to a remote MySQL server, you may need to specify the host using the `-h` flag followed by the host address.

4. If the credentials are correct, you will be connected to the MySQL server, and you will see the MySQL command prompt.
