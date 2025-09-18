# Ubuntu WSL

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
2. Set **username** (e.g., `vishal`) and **password** (e.g., `ubuntu`).

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
* **Command line:**  Opens in current folder
```bash
wsl.exe
```
* **Starting directory:** default path
```bash
\\wsl$\Ubuntu\home\ubuntu
```
* **Customize appearance:** Cursor shape: Bar

---

## Remove WSL Ubuntu

Open **PowerShell** as Administrator.
1. `wsl --list`
2. `wsl --shutdown` > `wsl --unregister Ubuntu`
3. Must remove autostartup script from the startup menu.
