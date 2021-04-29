---
layout: post
published: true
title: Linux Files Permissions and Those chmod Numbers we Use 🤔
date: 2021-04-29
subtitle: A short guide to learn Linux file permissions and what the hell are those numbers we use with chmod command
category: Posts
tags: linux beginners
bigimg: /img/linux-files-permission.jpg
share-img: /img/share-linux-files-permission.jpg
---

One thing to know about Linux is that you have file permissions for 3 categories.

1. User: The user who owns the file.
2. Group: Users belong to groups. Users in the same group also own the file.
3. Others: Permissions for users that are not the owner of the file and don't belong to the group.

# Example
Let's assume that your username is *mary* and you run an *ls* on your home folder

```
mary:/home# ls -lah
-rwxr--r--      1 mary   accounting    8 Jan 190 06:47 my_super_script.sh
 ^^^^^^^^^        ^^^^   ^^^^^^^^^^
 Permissions      User     Group
.....
```
> The first dash (-) represents the file type and it's not related to permissions.

Permissions are composed of 9 characters. In our case, those 9 characters are **rwxr--r--**

> Any permission not granted will be represented by a dash (-).  


Now, it might seem confusing reading **rwxr--r--**. This because permissions for the 3 categories permissions are put all together.

But you can look it like this to better understand it:

```
mary   accounting   Others    8 Jan 190 06:47 my_super_script.sh
rwx       r--        r--
```
> Here we broke down the 9 character string rwxr--r-- into 3 groups. Each one representing the three categories we mentioned early (user, group, others).

|User Permission (mary)|Group Permissions (accounting)|Permissions for others|
|:---:|:---:|:---:|
|rwx|r--|r--| 


- User Permission: The user *mary* can read, write and execute the file **(rwx)**.
- Group Permissions: Users in the group *accounting* can read the file but they can't write to it or execute it **(r--)**
- Permission for others: Users that are not *mary* or don't belong to the *accounting* group can read the file but they can't write to it or execute it **(r--)**

# Changing permissions and those numbers on the chmod command

You've probably copied and paste things like `chmod 644 myfile.html` or raised hell with `chmod -R 777 folder` when something wasn't working.

Remember that **chmod -R 777 folder** will do this:

![chmod777](/img/chmod777-cartman.jpg)


But where do those numbers come from?. From this table:

|Code|Meaning|
|:----:|-------|
|0|Permission denied|
|4|Read access|
|2|Write permission|
|1|Execute permission|

Let's see some examples and use the table above to better understand it

| command | user | group | others|
|---|:---:|:---:|:---:|
| chmod 664 | 6 | 4 | 4 |
| | 4+2 (read + write) | 4 (read)| 4 (read) |
| chmod 600| 6 | 0 | 0 |
| | 4+2 (read + write) | No read, write or execute | No read, write or execute |
| chmod 777| 7 | 7 | 7 |
| | 4+2+1 (read + write + execute)|4+2+1 (read + write + execute)|4+2+1 (read + write + execute)|  


> Remember that you set permissions for 3 categories: user, group and others

What you're doing it's just adding up the code for each permissions in each category.


# Read Official Docs, it's always helpful
For more detailed information read the manual [https://linux.die.net/Intro-Linux/sect_03_04.html](https://linux.die.net/Intro-Linux/sect_03_04.html)