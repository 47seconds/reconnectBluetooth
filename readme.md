# Automatic Bluetooth Reconnection Script

This script automates the reconnection of Bluetooth devices after switching operating systems in a dual-boot setup. Sometimes, previously saved devices do not reconnect automatically, requiring manual removal and reconnection. This script simplifies that process.

## Prerequisites

### Give permissions

#### Bluetooth service should be present and bluez bluez-utils
```sh
sudo pacman -S bluez bluez-utils
# OR
sudo apt-get install bluez bluez-utils
# OR use any other package manager compatible with your system
```

You have to give executable permission
```sh
chmod +x recoonectBluetooth
```
alternatively, you can use `bash` keyword before script to execute it
```sh
bash reconncetBluetooth 
```

### optional
You can move script to your scripts directory and export that path to bash, zsh, etc.
```sh
cd ~
mkdir scripts
cd scripts
git clone https://github.com/47seconds/reconnectBluetooth.git
mv reconnectBluetooth/reconnectBluetooth .
rm -rf reconnectBluetooth
vim ~/.bashrc
# add this at last line: export PATH=$HOME/scripts:$PATH
# :wq to save and exit vim
source ~/.bashrc
```
Now you can access this script from anywhere.

## Usage

#### Get help:
```sh
./reconnectBluetooth -h
# OR
./reconnectBluetooth --help
```

#### To list current devices in `bluetoothDevices.txt`:
```sh
./reconnectBluetooth list
# OR
./reconnectBluetooth devices
```

#### To rewrite device/s for reconnectiom in `bluetoothDevices.txt`:
```sh
./reconnectBluetooth [MAC ADDRESS DEVICE 1] [...]
```

#### To add/append for reconnection in `bluetoothDevices.txt`:
```sh
./reconnectBluetooth -a [MAC ADDRESS DEVICE 1] [...]
```

#### To find device MAC address:
```sh
# lists the saved devices in bluetooth
bluetoothctl devices

# to see MAC addresses of not saved devices, scan for them and note them somewhere
bluetooth
power on
scan on
```

#### To reconnect all devices listed in `bluetoothDevices.txt`:

```sh
./reconnectBluetooth
```


## Notes

- **Devices List Location:** The list of devices is stored at `~/scripts/bluetoothDevices.txt`.
- **Append Command Caution:** Never use the append (`-a`) command when the list is empty. Always initialize the list by adding devices first.
- **Script Caution:** If not used carefully, the script may malfunction and attempt to connect to an empty list of devices, wasting time unnecessarily.
- **Execution Ease:** You don't need `./` if added script path to shell path