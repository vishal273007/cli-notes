# Ubuntu WSL

## Install WSL Ubuntu

1. Open **PowerShell** as Administrator.
2. Run the command:

```powershell
wsl --install
```
Then check if installed.
```powershell
wsl --list --verbose
```

## Launch Ubuntu

1. Without restarting, Open **Ubuntu** from the Start Menu.
2. Set **username** (e.g., `vishal`) and **password** (e.g., `ubuntu`).
3. Run `touch .hushlogin` to hide home screen message.

Inside Ubuntu, update and clean packages:

```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt autoremove -y
```

## Fish Shell

Install Fish shell
```bash
sudo apt install fish -y
```

Set as default shell
```bash
chsh -s $(which fish)
```

Set Fish Prompt
```bas
fish_config
```
then > Prompt tab > Simple

## Terminal Settings

1. Set **Default Shell** to Ubuntu in your terminal settings.
2. To open Ubuntu in the current folder:

* **Settings → Profiles → Ubuntu**
* **Command line:**  Opens in current folder
```bash
wsl.exe
```
* **Starting directory:** default path (change vishal as required username)
```bash
\\wsl$\Ubuntu\home\vishal
```
* **Customize appearance:** Cursor shape: Bar

* `Save` after changes in Terminal.

---

# Change hostname

1. Edit /etc/wsl.conf: `sudo nano /etc/wsl.conf`

```bash
[boot]
systemd=true

[user]
default=vishal

[network]
hostname = ubuntu
generateHosts = false
```

2. Edit /etc/hosts: `sudo nano /etc/hosts`
- Change `127.0.1.1   vishal. vishal` to
```bash
127.0.1.1   ubuntu. ubuntu
```

3. Edit /etc/hostname: `sudo nano /etc/hostname`
- Replace `vishal` with `ubuntu`.

4. `wsl --shutdown` in Windows Terminal.

5. Terminal > change shell > delete previous ubuntu instance > set new ubuntu instance after reinstalling.

---

`---`: means thick hr line like above this.

## Uninstall WSL Ubuntu

Open **PowerShell** as Administrator.
1. Check if Linux is Installed
```bash
wsl --list --verbose
```

2. Close Ubuntu
```bash
wsl --shutdown
```

3. Remove
```bash
wsl --unregister Ubuntu
```

4. Must remove autostartup script from the startup menu.
