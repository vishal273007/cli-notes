
# SSH Setup

- `shell-name`: access shell from terminal client.

## SSH Server Setup on Windows

- Install OpenSSH Server > setup using ChatGPT.

- Test with SSH Client
- Type `ssh "vishal vishwakarma@hostname/ip"`. hostname will work when router support hostname resolution on other devices.
- Enter Microsoft password as ssh password, not local.

## SSH Server setup in Termux

 1. `passwd`: _Set password `sshpass`_ # Keep the password same for all devices as IP is already unique
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



### SFTP in Termux

sftp -P 8022 u0_a583@192.168.1.11

- `lcd "/mnt/d/downloads"`: Change local path in PC
- `cd /sdcard`: Change path in connected remote phone

*get file.txt* = Copy to PC path from Phone
*put file.txt* = Copy to Phone from the PC

- `ls`: check the copied file in the current path in phone

- `Ctrl + L / ! clear`: clear

*lcd* = local change directory [change folder path in PC]
*cd* = change foler path in connected ssh device.


##SFTP Usage (On Remote Device)**

### 📂 Folder management
mkdir NewFolder              # create a new folder on phone
rmdir OldFolder              # remove an empty folder on phone

### 📄 File upload (PC → phone)
put file.txt                 # upload one file to current remote dir
put * /sdcard/TargetFolder/  # upload all files from local dir to phone folder
put -r MyFolder              # upload a whole folder recursively

### 📄 File download (phone → PC)
get file.txt                 # download one file from phone
get * "/mnt/d/downloads"     # download all files in current remote dir to local folder
get -r PhoneFolder           # download a whole folder recursively

### ✏️ Rename / Move on phone
rename oldname.txt newname.txt   # rename or move a file/folder

### ❌ Delete on phone
rm unwanted.txt               # delete a file
rmdir EmptyFolder             # delete an empty folder

# 📜 Navigation & listing on phone
cd /sdcard/DCIM              # change remote directory
ls                           # list files in current remote dir



## SFTP Usage (For Local Device)

# 📂 Folder management (local PC)
! mkdir LocalFolder              # create a new folder on PC
! rmdir LocalFolder              # remove a folder on PC (must be empty)

# 📄 File operations (local PC)
! rm file.txt                    # delete a file on PC
! mv oldname.txt newname.txt     # rename or move a file on PC

# 📜 Navigation & listing (local PC)
lcd /mnt/c/Users/Vishal\ Vishwakarma/Desktop   # change local dir (WSL path)
lcd "C:\Users\Vishal Vishwakarma\Desktop"      # change local dir (Windows PowerShell path)
lls                                            # list files in current local dir







