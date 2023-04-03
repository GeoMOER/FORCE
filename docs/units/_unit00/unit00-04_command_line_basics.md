---
title: Command line basics
toc: true
header:
  image: '/assets/images/teaser/allbands.png'
  caption: '[Netra Bhandari](https://www.uni-marburg.de/en/fb19/disciplines/physisch/environmentalinformatics){:target="_blank"}'
---

Try the following snippets to get acquainted with command line basics 

# Getting the command line 
* In your virtual machine search for "Terminal"
* A quick way is **Ctrl-Alt-T**

# Understanding locations 
To get the present working directory type "pwd". You will probably be getting a result like /home/your_username

```
pwd
```
To change the working directory type. Use forward slash.

```
cd /new_location_name
cd /home/username/Desktop #example to make desktop as working directory
cd ~/Desktop #'~' means start from home directory
```

To go to home directory , use "cd home
```
cd home
cd .. #To go one step up the directory
cd ../../../ #To go multiple step up (shown here is three steps up)
```
Creating a new folder

```
mkdir /Desktop/FORCE #mkdir stands for make directory
cd ~/Desktop/FORCE
mkdir dir1 dir2 dir3 #makes multiple subdirectories within FORCE directory
```

Remove a folder

```
rmdir dir1 #deletes empty directory
```


Get a list of folders

```
ls 
```

apt command - Use apt for installing, upgrading, configuring, and removing apps/programs

```
apt (command)
apt update
```

Commands via sudo (superuser do). sudo allows you to run a command as root . This command will ask you for a password.

```
apt install sudo # use if sudo is not available
sudo apt-get update #to get updates
sudo apt-get install git-all #installing git
sudo (command)
```
