# destroy-ios-steps

========= Stage 1: Jailbreak ===========

Download Absinthe:
https://www.iphonehacks.com/download-absinthe

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
https://www.stanleyulili.com/git/how-to-install-git-bash-on-windows/ instructions

Install OpenSSH server:
https://github.com/PowerShell/Win32-OpenSSH/releases/ get Latest
Unzip wherever you like

run GitBash(AS ADMINISTRATOR, TO GET ROOT AUTHORITIES), cd .. into directory you installed OpenSSH into
type: powershell.exe -ExecutionPolicy Bypass -File install-sshd.ps1

then generate keys:
type: ssh-keygen.exe -A

OPEN 22 PORT FOR CONNECTION:
Open POWERSHELL (AS ADMINISTRATOR, AGAIN):
New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Inbound -Action Allow -DisplayName SSH

Check if everything works: Get-NetFirewallRule -Name *OpenSSH-Server* |select Name, DisplayName, Description, Enabled (DO IT IN POWERSHELL).
netstat -na| grep ":22" (grep the port, check if Listening!)

Find your IP address("ipconfig" in terminal).






