
# SSH Setup

## SSH Server Setup on Windows

- Install OpenSSH Server > setup using ChatGPT.

- Test with SSH Client
- Type `ssh "vishal vishwakarma@hostname/ip"` hostname works when router supports hostname resolution.
- Enter Microsoft password, not local.

## SSH Server setup in Termux

```bash

 passwd # Set 'ssh@pass' and keep the password same for all devices
 sshd # Start
 ps aux | grep sshd # Verify

# add in config.fish to autostart
sshd

# For first time, test From client device:
ssh -p 8022 u0_a363@192.168.0.142 # password 'ssh@pass' - Connect with Hotspot or Wi-Fi.

# After testing, just type 
sshpass -p 'ssh@nord4' ssh -p 8022 u0_a630@192.168.1.13

whoami # username 
ifconfig # IP address

```

### SSH Client for Auto Login

```bash
sudo apt install sshpass -y && sshpass -V # for storing password and verify

or 

Use SSH keygen to for password login.
    
sf # source to apply the changes

```


### sqlplus dynamic IP auto login with custom sql commands

```bash
# sqlplus function with custom commands in c:\tools\commands.sql with 'cl scr and set linesize 100'
function sqlplus
    sshpass -p '12513365@Ms' ssh -t "vishal vishwakarma@vishal" "sqlplus system/tiger @C:\\tools\\commands.sql"
    ---------------------------OR----------------------------
    set HOST_IP (ipconfig.exe | grep -m 1 "IPv4 Address" | awk '{print $NF}' | tr -d '\r') # IP address containing 172.25.16.1
    sshpass -p '12513365@Ms' ssh -t "vishal vishwakarma@$HOST_IP" "sqlplus system/tiger @C:\\tools\\commands.sql"
end
```

## REMOTE HOST IDENTIFICATION HAS CHANGED Solution

```bash
# Remove the old host key
ssh-keygen -f ~/.ssh/known_hosts -R "[192.168.1.25]:8022"

# Login with standard method to update the host key
ssh -p 8022 u0_a630@192.168.1.13 # Then enter password. Use alias after if needed.
```

## Passwordless SSH Login

```bash
# In Client Device

# Generate SSH key pair
ssh-keygen -t rsa # Press enter to accept default setup.

# Copy public key to remote host
ssh-copy-id phone / u0_a630@192.168.1.10 # Then enter password.

# Test
ssh phone / u0_a630@192.168.1.10 # Should connect without password.
```

## Short steps to connect with SSH

```bash
cd .ssh # Go to .ssh directory
nano config # Create config file

# Paste the following
# Phone
Host phone
    HostName 100.70.91.88 (phone/tailscale_ip)
    Port 8022
    User vishal

# Tablet
Host tablet
    HostName 100.92.203.123(Short domain/tailscale_ip)
    Port 8022
    User vishal

# Ubuntu
Host ubuntu
    HostName 100.125.28.13(Short domain/tailscale_ip)
    Port 2222
    User vishal

# Here, in phone, due to other apps, domain can cause issue due to conflict with other apps. IP always works and free from the conflict and only changes after re-installing the tailscale. for IP, after re-installation, it is needed to update the ip in config inside .ssh folder.

# Set permissioin
chmod 600 config

# Test
ssh phone

# Here u0_a615 username is not needed, just any name like vishal or ubuntu works same.

# Termux username changes on each re-install. You can again only change the username by re-installing only.

```

## Setup Open SSH Server in WSL Ubuntu

```bash
# Install SSH server
sudo apt install openssh-server -y

# Start SSH service
sudo service ssh start

# Check status
sudo service ssh status
```
### From Powershell

```powershell
# Find WSL IP
wsl hostname -I

# Set up port forwarding (replace <WSL_IP> with output)
netsh interface portproxy add v4tov4 listenport=2222 listenaddress=0.0.0.0 connectport=22 connectaddress=172.31.57.25(<WSL_IP>)

# Allow port in firewall
New-NetFirewallRule -DisplayName "WSL SSH Forward" -Direction Inbound -LocalPort 2222 -Protocol TCP -Action Allow

# Find Windows IPv4 for Termux connection
ip # in Ubuntu
ipconfig # in powershell
```
### From Termux
```bash
# Termux: Install SSH client
pkg install -y openssh -y

# Test via forwarded port
ping 100.86.124.118/vishal/vishal.bombay-fort.ts.net <tailscale_ip> # ping tailscale ip to test connection
ssh -p 2222 vishal@192.168.1.8 # (wsl_username@Windows_IP)

# in Termux ssh config file, after tailscale setup
Host ubuntu
    HostName vishal
    Port 2222
    User vishal


# Set permissioin
chmod 600 config

# Test
ssh ubuntu

# or 

# From powershell
ssh vishal@localhost
```

## SSH via TailScale (Works over any network)

- Sign into TailScale in both PC and Android.

- Connect TailScale after installation in both PC and Android.

- PC tailscale tray > account > Admin console > do changes if needed.

- DNS tab: Tailnet DNS name - bombay-fort.ts.net (can be renamed)

<br>

```bash
# Windows DNS address 
vishal # Short DNS address
vishal.bombay-fort.ts.net # Full DNS address

# Android DNS address
'phone' / 'tablet' # Full DNS address: phone.bombay-fort.ts.net

# Enable - allow on LAN.
```

### TailScale in WSL Ubuntu
```bash
# Install TailScale
curl -fsSL https://tailscale.com/install.sh | sh

# Sign in
sudo tailscale up

# Manage or See details
Windows notification tray > Account > Admin console...
```

### Useful Usage of Tailscale
- Use the tailscale domain to use the ftp with the fixed ip, even over internet.
```bash
# Example full standard ftp address
ftp://192.168.1.10:9999

# Tailscale ftp same address over anywhere
ftp://<tailscale_ip>phone:9999
```

- Tailscale domain to use in SSH adress
```bash
ssh -p 8082 u0_a600@phone
```
