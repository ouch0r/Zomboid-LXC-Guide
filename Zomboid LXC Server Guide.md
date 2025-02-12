#Server #Gaming #Linux
### Intro 
So you got a machine which is running Linux Containers and you want to host a Zomboid Server?
  
While trying setting up a server following the offical guide from the pzwiki I ran into some hiccups here and there. Here's a much simpler and easier to follow step by step solution.  
I can now set up zomboid servers on as many linux containers I want to! Yeah!  
I am a linux noob myself so beware! I might not be able to help if you got any questions...  
  
First set up a fresh isolated Linux system. You can find guides for that on the world wide web. lol

### Fresh LXC

Fresh machine set up and ready to go

login as

```
root
yourpasswordyouchosewhilesettingupthismachine
```

### Update all containers

Update all containers

```
apt update && apt dist-upgrade y
```
### Set timezone and reboot

Set time and reboot  

```
dpkg-reconfigure tzdata
reboot
```

### Install dependencies 

Install dependencies
  
>[!info]
>This will get us anything we need to install the server  
  
```
apt install software-properties-common
add-apt-repository multiverse
dpkg --add-architecture i386
apt update
apt install lib32gcc-s1
apt install steamcmd
```
  
>[!Danger]
>**Don't run steamcmd as the root user!!**

### Create new user + navigation

Create zomboid user

```
adduser zomboid
```
  
Switch to zomboid user
  
```
su zomboid
```

Navigate to your zomboid folder
  
```
cd .. 
cd home
cd zomboid
```

Create server directory

```
mkdir pzserver
cd pzserver
```
### Run steamcmd / Install server

Run steamcmd
  
>[!caution] 
>Make sure you're logged in as the zomboid user!  

```
steamcmd
```

Install zomboid server
 
```
force_install_dir /home/zomboid/pzserver/
login anonymous
app_update 380870 validate
exit
```
### Initialise and set up server

Initialise server

```
./start-server.sh 
ctrl + C 
reboot
```
  
Set up server
  
```
su zomboid
cd ..
cd home
cd zomboid
cd Zomboid
cd Server
nano servertest.ini
```
### Have Fun!

Everything should be working now!
  
>[!Keep this in mind]
>Remember to forward ports in your firewall to your LXC. 
>Use nano to edit your *.ini and/or *.lua files to your liking.

Have fun getting bitten on your very own dedicated server!