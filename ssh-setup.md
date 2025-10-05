
# SSH Setup

## SSH Server Setup on Windows

- Install OpenSSH Server > setup using ChatGPT.
- SSH Client -> Type `ssh "vishal vishwakarma@hostname/ip"` # hostname works when router supports hostname resolution.
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

# After testing, connect with single command
sshpass -p 'ssh@pass' ssh -p 8022 u0_a600@192.168.1.13

whoami # username [vishal/u0_a600]
hostname # hostname [localhost/ubuntu]
ifconfig # IP address [192.168.1.13]
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
ssh -p 8022 u0_a630@192.168.1.13 # Then enter password.
```

## Passwordless SSH Login

```bash
# Generate SSH key pair in client device
ssh-keygen -t rsa # Press enter to accept default setup.

# Copy public key by running the following command in client device
ssh-copy-id phone / u0_a630@<hostname/ip> # Then enter password.

# Test
ssh phone / u0_a630@<hostname/ip> # Should connect without password.
```

## Config File Setup for quick connection

```bash
cd .ssh # Go to .ssh directory
nano config # Create config file

# Paste the following
# Phone
Host phone
    HostName 100.70.91.88 # <phone/tailscale_ip>
    Port 8022
    User vishal

# Tablet
Host tablet
    HostName 100.92.203.123 # <Short domain/tailscale_ip>
    Port 8022
    User vishal

# Ubuntu
Host ubuntu
    HostName 100.125.28.13 # <Short domain/tailscale_ip>
    Port 22
    User vishal

# Here, in phone, due to other apps, domain can cause issue due to conflict with other apps. IP always works and free from the conflict and only changes after re-installing the tailscale. for IP, after re-installation, it is needed to update the ip in config inside .ssh folder.

# Set permissioin
chmod 600 config

# Test
ssh phone

# Here u0_a600 username is not needed, just any name like vishal or ubuntu works same.
# Termux username changes on each re-install. You can again change the username by re-installing.
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

# Set up port forwarding (replace <WSL_IP> with output) -- if using same port 22, ensure windows is not running ssh server
netsh interface portproxy add v4tov4 listenport=22 listenaddress=0.0.0.0 connectport=22 connectaddress=172.19.25.11 <WSL_IP>

# Allow port in firewall
New-NetFirewallRule -DisplayName "WSL SSH Forward" -Direction Inbound -LocalPort 22 -Protocol TCP -Action Allow

# Find Windows IPv4 for Termux connection
ifconfig # in Ubuntu
ipconfig # in powershell

# Test after forwarding wsl port to windows
ssh vishal@windows-tailscale-ip
```
### From Termux
```bash
# Termux: Install SSH client
pkg install openssh -y

# Test via forwarded port
ping 100.86.124.118/vishal<tailscale_ip> # ping tailscale ip to test if connection is working

ssh vishal@ubuntu # test with hostname:
ssh vishal@100.125.28.13 # wihout mentioning port
ssh -p 22 vishal@100.125.28.13 # mention port explicit


# in Termux ssh config file, after tailscale setup
Host ubuntu
    HostName 100.125.28.13(Short domain/tailscale_ip)
    Port 22
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

- Sign in with TailScale in both PC and Android.

- Connect TailScale after installation in both PC and Android.

- PC tailscale tray > account > Admin console > do changes if needed.

```bash
# Set custom device name and disable key expiry

# DNS tab: Tailnet DNS name - bombay-fort.ts.net (can be renamed)

# Enable - allow on LAN in Android TailScale app.

# Windows Domain names 
vishal # Short Domain name
vishal.bombay-fort.ts.net # Full Domain name

# Android Domain names
'phone' / 'tablet' # Full Domain name: phone.bombay-fort.ts.net
```

<br>

### TailScale in WSL Ubuntu
```bash
# Install TailScale
curl -fsSL https://tailscale.com/install.sh | sh

# Sign in
sudo tailscale up

# Manage or See details
Windows notification tray > Account > Admin console...
```

### Other Usage of Tailscale
Tailscale IP address to use ftp with fixed ip, even over internet.
```bash
# Tailscale ftp same address over anywhere
ftp://100.70.91.88:9999/ # ftp://<tailscale_ip>phone:9999
```
Tailscale domain to use in SSH address
```bash
ssh -p 8082 u0_a625@100.70.91.88 # <domain/tailscale_ip>
```
