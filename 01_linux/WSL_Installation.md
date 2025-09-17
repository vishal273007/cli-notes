# Ubuntu WSL Installation

## 1. Enable WSL

1. Open **PowerShell** as Administrator.
2. Run the command:

```powershell
wsl --install
```

3. Restart the PC when prompted.

> **Note:** Ubuntu will be installed by default—no need to install from the Microsoft Store.

---

## 2. Launch Ubuntu

1. Open **Ubuntu** from the Start Menu.
2. Wait for the installation to complete.
3. Create a **username** (e.g., `ubuntu`) and **password** (e.g., `ubuntu`).

---

## 3. Verification

Check installed WSL distributions and status:

```powershell
wsl --list --verbose
```

Inside Ubuntu, update and clean packages:

```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt autoremove -y
```

Check Ubuntu version:

```bash
cat /etc/os-release
```

---

## 4. Terminal Settings (Optional but Recommended)

1. Set **Default Shell** to Ubuntu in your terminal settings.
2. To open Ubuntu in the current folder:

* **Settings → Profiles → Ubuntu**
* **Command line:** `wsl.exe` (Opens in current folder)
* **Starting directory:** `\\wsl$\Ubuntu\home\ubuntu` (default path)

3. Customize appearance:

* **Cursor shape:** Bar
