<h2 align=center>Linux CLI</h2>

Non-root user command looks like :  
```command
~$ sudo apt-get update
~$ sudo apt-get install python3
```  

<br>

Root user command looks like :  
```super_user
~# adduser sammy
~# shutdown
```
<br>
Basically whatever navigation works & operatings we do in Windows by using mouse (i.e. copy-paste-folder opening-selecting-etc.), here in Linux same thing we'll do but in terminal panel/tab with commands. And similarly there are more Linux specific operations for which also we use some special commands.  

Operating a PC with CLI or commands causes : No more GUI/interface load, lagging, hanging task to the PC, where everything will be operated from a single terminal panel/tab only.  

If we are newly starting working/learning/operating with Linux command (as a beginner), then we can use an practical approach which helps us to understand how the Linux command works in backend. It's like when we are opening the Linux's Terminal (CLI) then at the same time we will also open the File-Explorer (GUI) interface of the Linux. We open the CLI & GUI both side-by-side, so that when we do any command in the CLI we can see it real ouput effect in the GUI screen. It's very similar to when we're working with HTML/CSS, where in windows' one side screen will be code editor and another side will be the live-preview browser which shows the real-time output effect of the HTML/CSS code (side-by-side in split screen). And with this approach there's 'no more visualization' but 'direct preview of command output' in split-screen. Also, we can use this approach with 'GIT' command, 'SQL' command, and any other command related learnings where it will directly show the live preview of command output/effect. But for backend codings like Java, JavaScript, TypeScript, etc. we have to use different tools like PostMAN, etc., it's because backend coding includes a coding-structure, methods, variables, and many more which are complex than a simple command.  


<br>
<br>

Both Linux and Windows have a concept of normal users and privileged users (commonly referred to as "root" in Linux and "administrator" in Windows).  

Suppose we have two PCs: one with Windows installed and a single user account, and another with Kali Linux installed, also with a single user account.  

In both systems, when using the terminal or command line, there are two types of user modes available: normal user mode and elevated (privileged) user mode.  

In Windows, this corresponds to a standard user and an administrator (admin) user.  

In Kali Linux, this corresponds to a normal user and the root user.  

If we are using Kali linux's terminal as normal user, then to switch to root user we use the command : `sudo su`.  
If we are suing Windows's command prompt as normal user, then we can't switch directly but can do like : **'cmd' >> Run as administrator**.  

<br> 

### Note
We can understand like "an 'Admin user' mean an user which is the first user & which already presents/creates during the installation time of the OS". An Admin user (or Administrator) is typically a user account that has elevated privileges and control over the operating system. While it's common for an Admin user to be created during the installation of an OS (like Windows, macOS, or Linux), an Admin user doesn't necessarily have to be the one created at installation. It’s the user account that has special permissions to manage system settings, install software, create or remove other users, and generally administer the OS.  

To sum it up:  
- An Admin user can be created during OS installation, but it could also be added later by someone with administrative rights.
- Not every user created during installation is necessarily an admin; it depends on how the OS is configured (e.g., in Windows, you can choose to create an admin account or a standard user).

<br> 
<br> 

When we open Command prompt in Windows, then its default path will be like :  
```
C:\Users\user1>
```
Inside which there are folders like : 3D Object, .m2 folder, Desktop, Document, Music, Pictures, Videos, etc. For to see these folders/directories inside '\user1' path, we use `dir` command which list all the files & folders in Windows.  

And when we open Command prompt with Admin mode in Windows, then its path will be like :  
```
C:\Windows\system32>
```

<br> 

Similarly, when we open Terminal in Linux, then its default path will be like :  
```
C/home/user1:~$

or 

user1@user1:~$
```
Inside which there are folders like : Desktop, Documents, Downloads, Music, Pictures, etc. For to see these folders/directories inside '/user1' path, we use `ls` command which list all the files & folders in Linux.  

Similarly, when we open Terminal with Admin/Root mode in Linux, then its path will be like : (in Linux the path for Admin is same) 
```
C/home/user1:~#

or 

C/home/root@user1:~#

or

root@user1:~#
```



--------
--------


<h2 align=center>Windows CLI</h2>

To change Diver :  
```
D:
```
<br> 

To list all folders & files inside a directory :  
```
dir
```

<br> 

To select/visit inside a directory : (here insteadl of typing manually, we can use the 'TAB' key to auto-select the folder/file names)  
```
cd "Java Course"
```

<br>

To go to previous directory : (this command is same in both Windows & Linux, with the above 'TAB' key function)  
```
cd ..
```

<br> 

To clear the screen of CLI :  
```
cls
```

<br> 

To exit from CLI or command prompt :  
```
exit
```





