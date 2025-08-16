# Useful su -c Commands

## ⚡ Power / Restart
- `su -c "reboot"` — Reboot phone  
- `su -c "reboot -p"` — Power off  
- `su -c "reboot recovery"` — Reboot into recovery  
- `su -c "reboot bootloader"` — Reboot into bootloader/fastboot  
- `su -c "svc power shutdown"` — Alternative shutdown  

## 📶 Network
- `su -c "svc wifi enable"` — Enable WiFi  
- `su -c "svc wifi disable"` — Disable WiFi  
- `su -c "svc data enable"` — Enable mobile data  
- `su -c "svc data disable"` — Disable mobile data  

## 🔊 Screen / Buttons
- `su -c "input keyevent 26"` — Power button (screen on/off)  
- `su -c "input keyevent 24"` — Volume up  
- `su -c "input keyevent 25"` — Volume down  

## 📱 Apps
- `su -c "am force-stop com.whatsapp"` — Force stop app  
- `su -c "pm clear com.whatsapp"` — Clear app data  
- `su -c "pm disable-user com.whatsapp"` — Disable app  
- `su -c "pm enable com.whatsapp"` — Enable app  

## 🔋 Battery / System Info
- `su -c "dumpsys battery"` — Battery info  
- `su -c "dumpsys meminfo"` — Memory usage  
- `su -c "logcat -d | tail -n 50"` — Last 50 log lines (for debugging crashes)
