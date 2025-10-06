# Useful Termux Commands

## Important Commands
```bash
cd /  # open root storage 
cd /sdcard/  # open storage
```

### Termux Miscellaneous Commands
```bash
- termux-reload-settings # load the changes
- vol-up + k # hide/unhide termux bottom toolbar.
- termux-open file.txt / file.img # open files with termux
- termux-wake-lock/unlock # keep running/close after lock screen 
```

## su -c Commands
- `su -c "reboot"` — Reboot phone  
- `su -c "reboot -p"` — Power off  
- `su -c "reboot recovery"` — Reboot into recovery  
- `su -c "reboot bootloader"` — Reboot into bootloader/fastboot  

_Apps_
- `su -c "am force-stop com.whatsapp"` — Force stop app  
- `su -c "pm clear com.whatsapp"` — Clear app data  
- `su -c "pm disable-user com.whatsapp"` — Disable app  
- `su -c "pm enable com.whatsapp"` — Enable app  

## Battery details
```bash
# Function to get battery details
function battery
    su -c 'echo "Battery: $(cat /sys/class/power_supply/battery/capacity)% , Temp: $(($(cat /sys/class/power_supply/battery/temp)/10))°C"'
end

# OR in One line
su -c 'echo "Battery: $(cat /sys/class/power_supply/battery/capacity)% , Temp: $(($(cat /sys/class/power_supply/battery/temp)/10))°C"'
```
