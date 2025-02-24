## The issue:

the command: 

`sudo do-release-upgrade` 
 returns:
```bash 
Checking for a new Ubuntu release
In /etc/update-manager/release-upgrades Prompt 
is set to never so upgrading is not possible.
```

Which means that the system is set to never check for upgrades O___O !!

## The fix:

`sudo nano /etc/update-manager/release-upgrades`

change: 

`Prompt=never`

to

`Prompt=lts`

to upgrade to the lts version or

`Prompt=normal`

for a non-lts version

## Braken (non upgradable) package refuses to upgrade so blacks everything:
### example

the command:
`apt list --upgradable`
returns:
`Listing... Done
dell-linux-assistant/bionic 2.2.0545 amd64 [upgradable from: 2.2.0544]
N: There is 1 additional version. Please use the '-a' switch to see it`

Meaning that the dell-linux-assistant is broken. 

Try upgrading it: `sudo apt install --only-upgrade dell-linux-assistant
`
or remove it (if upgrade fails): `sudo apt remove dell-linux-assistant`

then retry:
`sudo apt update && sudo apt upgrade -y
sudo do-release-upgrade`
