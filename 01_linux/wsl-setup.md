# Ubuntu WSL

### Remove WSL Ubuntu

Open **PowerShell** as Administrator.
1. `wsl --list`
2. `wsl --shutdown` > `wsl --unregister Ubuntu`
3. Must remove autostartup script from the startup menu.

---

## Install WSL Ubuntu

1. Open **PowerShell** as Administrator.
2. Run the command:

```powershell
# Install Ubuntu
wsl --install

# Check after installation
wsl --list --verbose
```

## Launch Ubuntu

1. Without restarting, Open **Ubuntu** from the Start Menu.
2. Wait 2 minutes for the installation to complete.
3. Create a **username** (e.g., `ubuntu`) and **password** (e.g., `ubuntu`).

---

Inside Ubuntu, update and clean packages:

```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt autoremove -y
```

---

## 4. Terminal Settings

1. Set **Default Shell** to Ubuntu in your terminal settings.
2. To open Ubuntu in the current folder:

* **Settings → Profiles → Ubuntu**
* **Command line:** `wsl.exe` (Opens in current folder)
* **Starting directory:** `\\wsl$\Ubuntu\home\ubuntu` (default path)
* **Customize appearance:** Cursor shape: Bar
