# destroy-ios-steps

========= Stage 0: Eminem Song ========

This is a long journey ahead of you, so you need some proper music!

Eminem - The Real Slim Shady on Spotify:
```
https://open.spotify.com/album/6t7956yu5zYf5A829XRiHC?highlight=spotify:track:3yfqSUWxFvZELEM4PmlwIR
````

========= Stage 1: Jailbreak ===========

Download Absinthe:

```
https://www.iphonehacks.com/download-absinthe
```

After you donwloaded the archive, extract it anywhere you like
In the extracted folder, find absinthe icon, rightclick it, ---> select properties ---> compatibility
place tick in "Run this program in compatibility mode for", and select Windows XP(service pack 3) - Got no fucking idea, what's that for, but it does not work otherwise :D
Then, doubleclick absinthe icon, and wait for installation process to finish.

Latest version of iTunes needs to be installed on your PC!

Connect your device via usb cable, after that - run absinthe
Wait until absinthe recognizes your device, and then press "Jailbreak". Wait for process to finish(takes about 3-5 min),
and do not disconnect your device

========= Stage 2: Preparing apple device =============

After device is successfully "jailbroken", some software needs to be installed.
But first, we need to update Cydia's packages, which is going to be done automatically as soon as you enter it.

1) Install Mobile Terminal package on your Iphone (Enter Cydia, ---> Search "Mobile Terminal")
2) Install OpenSSH (Enter Cydia, ---> Search "OpenSSH")

======== Stage 3: Preparing Windows PC ================

Install GitBash(optional, will be easier to manipulate the "Linux-like" terminal):
```
https://www.stanleyulili.com/git/how-to-install-git-bash-on-windows/ instructions
```

If you don't want to use and install Gitbash, you can do that with CMD terminal. To open it:
```
Press windows key
Type CMD in your search window
Find Command Prompt
Rightclick -> RUN AS ADMINISTRATOR(!!!)
```

Install OpenSSH server:
```
https://github.com/PowerShell/Win32-OpenSSH/releases/ 
```
get Latest, unzip wherever you like

run GitBash(AS ADMINISTRATOR, TO GET ROOT AUTHORITIES), cd .. into directory you installed OpenSSH into, and type: powershell.exe -ExecutionPolicy Bypass -File install-sshd.ps1

example:
```
cd /my/path/to/folder/OpenSSh
powershell.exe -ExecutionPolicy Bypass -File install-sshd.ps1
```

OPEN 22 PORT FOR CONNECTION:
Open POWERSHELL (AS ADMINISTRATOR, AGAIN):
```
New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Inbound -Action Allow -DisplayName SSH
```
If you don't create the rule with the above command, - your windows firewall will block any kind of ssh connection, so don't forget this part.

Check if rule is created: 
```
Get-NetFirewallRule -Name *OpenSSH-Server* |select Name, DisplayName, Description, Enabled (DO IT IN POWERSHELL).
```
You should also check if ssh-agent and sshd services are both enabled and running, you can do that by following this steps:

```
press windows key + r, and Run window will open
type: services.msc, hit enter
Search for OpenSSH Authentication Agent and OpenSSH SSH Server, start them both

```
If you want to check if your 22 port is accepting connections, use:
```
netstat -na| grep ":22" (grep the port, check if Listening!)
```

If you wan't to check that everything works, you can try connecting to your Phone from your windows PC and vice versa, by typing:
```
ssh myPcName@myPcIp and then entering password(from Iphone) and
ssh root@myIphonsIp, deff password === alpine (from your pc)
```
To get your pc name, open Command Prompt, type:
```
whoami
```
It will return your name, that you are supposed to use while connecting.

Find your IP address of your PC:
```
Open terminal
type: ipconfig
```
To find your Phones ip:
```
settings -> general -> network -> select your wifi connection, look for Ip address in the list
```
if you're connected, proceed to the next step.

======== Stage 4: Make a disk image =========

Enter Mobile terminal, type: 
```su```
to get root authorities

To start copy process:
```
dd if=/dev/rdisk0 bs=1M | ssh username@ip 'C:\dd-0.5\dd.exe of=iphone.img'
```



