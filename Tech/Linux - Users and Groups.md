## 1. Users
***
- Each user has a unique ID which can be viewed using `id`
```
dumbcate@dumbcate ~ $ id
uid=1000(dumbcate) gid=1000(dumbcate) groups=1000(dumbcate)
```

- New account can be created using `adduser` or modifying */etc/passwd*
- Switch user using `sudo su`

***

## 2. Groups
***
- Each user in a Linux system belongs to at least 1 group. The permissions that a group has is imposed on all the users in that group.
- Create a group using `groupadd`
- Add users to group using `usermod`
- List groups using `groups` or */etc/group*

***