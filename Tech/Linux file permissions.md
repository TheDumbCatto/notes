![](Pasted%20image%2020221115173105.png)

- Each columns in the permissions part is represented by 3 bits, meaning a 7 in decimal would correspond to 111 in binary and consequently rwx permission and so on.
- Besides from an owner, a file can have a **group owner**. All users belong to that group owner obtain the group permission as shown in the image.
- Basic file's permission management:
	`chown` to change the file's owner.
	`chmod` to change the file's permissions.
	`getfacl` to view the file's ACL
	`setfacl` to set ACL for a file
	![](Pasted%20image%2020221115173616.png)
	