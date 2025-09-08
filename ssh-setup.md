
# SSH Setup

- `shell-name`: access shell from terminal client.

## SSH Server Setup on Windows

- Install OpenSSH Server > setup using ChatGPT.

- Test with SSH Client
- Type `ssh "vishal vishwakarma@hostname/ip"`. hostname will work when router support hostname resolution on other devices.
- Enter Microsoft password as ssh password, not local.

## SSH Server setup in Termux

 1. `passwd`: _Set password `ssh@pad6/ssh@nord4`_
 2. `sshd`: _Start_
 3. `ps aux | grep sshd`: _Verify_
 4. `config file` ==> add `sshd` to autostart.
 5. For one time, test From client device: `ssh -p 8022 u0_a363@192.168.0.142` and pwd `ssh@pad6/ssh@nord4` - Connect with Hotspot or Wi-Fi.
 6. After testing, just type `sshpass -p 'ssh@nord4' ssh -p 8022 u0_a630@192.168.1.13` and connect. Fish will save it so just change details each time.

- In client config file, add  line `alias sshpad6="~/.pad6_ssh_login.sh`. > `touch ~/.pad6_ssh_login.sh` > `chmod +x ~/.pad6_ssh_login.sh` >

- `#!/bin/bash (enter) sshpass -p 'ssh@pad6' ssh "u0_a327@192.168.0.149" -p 8022`.

- `whoami`: _username_ `ifconfig`: _IP address_

### SSH Client for Auto Login

```bash
sudo apt install sshpass -y && sshpass -V # for storing password and verify

nvim ~/.ssh_login_windows.fish # add below script in this file

#!/usr/bin/env fish
sshpass -p '12513365@Ms' ssh "Vishal Vishwakarma@vishal/192.168.0.125"

chmod +x ~/.ssh_login_windows.fish # make the script executable.
~/.ssh_login_windows.sh # run to verify the script.

nvim ~/.config/fish/config.fish # open config file
alias sshwindows="~/.ssh_login_windows.fish" # add alias

source `sf` # apply the changes
sshwindows
```

### SSH Client for Auto Login on dynamic auto IP

```bash
#!/usr/bin/env fish
set HOST_IP (ipconfig.exe | grep -m 1 "IPv4 Address" | awk '{print $NF}' | tr -d '\r') # Get filtered host IP address
sshpass -p "12513365@Ms" ssh "vishal vishwakarma@$HOST_IP"
------------------------------OR------------------------------------
sshpass -p "12513365@Ms" ssh "vishal vishwakarma@vishal"
```

### sqlplus dynamic IP auto login with custom sql commands

```bash
# sqlplus function with custom commands in c:\tools\commands.sql with 'cl scr and set linesize 100'
function sqlplus
    sshpass -p '12513365@Ms' ssh -t "vishal vishwakarma@vishal" "sqlplus system/tiger @C:\\tools\\commands.sql"
    ---------------------------------------------OR---------------------------------------------------------
    set HOST_IP (ipconfig.exe | grep -m 1 "IPv4 Address" | awk '{print $NF}' | tr -d '\r') # IP address containing 172.25.16.1
    sshpass -p '12513365@Ms' ssh -t "vishal vishwakarma@$HOST_IP" "sqlplus system/tiger @C:\\tools\\commands.sql"
end
```

## REMOTE HOST IDENTIFICATION HAS CHANGED Solution

```bash
ssh-keygen -f ~/.ssh/known_hosts -R '[ip(192.168.0.142)]:8022'

Then first login to ssh with password and then use alias.
```

### Copy files using SSH
```bash
scp -P 8022 u0_a583@192.168.1.3:/sdcard/Download/KSU.tar.gz "/mnt/c/Users/Vishal Vishwakarma/Desktop"
```
**Explanation**
- scp = secure copy
- -P 8022 = ssh port
- u0_a583@IP_Address - Termux SSH user and ip
- /sdcard/Download/KSU.tar.gz = file on the remote source device






















fff
