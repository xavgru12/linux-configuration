Dongle from Asus used for bluetooth connections of keyboard and mouse.

## Download bin files

- Ensure the directory exists
sudo mkdir -p /lib/firmware/mediatek/mt7925

- Download the Bluetooth RAM code (The one you saw on the server)
sudo wget -O /lib/firmware/mediatek/mt7925/BT_RAM_CODE_MT7925_1_1_hdr.bin https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/mediatek/mt7925/BT_RAM_CODE_MT7925_1_1_hdr.bin

- Download the Wi-Fi Patch (The MT7925 often needs this initialized for the BT combo to work)
sudo wget -O /lib/firmware/mediatek/mt7925/WIFI_MT7925_PATCH_MCU_1_1_hdr.bin https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/mediatek/mt7925/WIFI_MT7925_PATCH_MCU_1_1_hdr.bin

- Download the Wi-Fi RAM code
sudo wget -O /lib/firmware/mediatek/mt7925/WIFI_RAM_CODE_MT7925_1_1.bin https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/mediatek/mt7925/WIFI_RAM_CODE_MT7925_1_1.bin

set permission:
sudo chmod 644 /lib/firmware/mediatek/mt7925/*.bin

- reload bluetooth
sudo modprobe -r btusb
    sudo modprobe btusb

check if its active
sudo dmesg | grep -i Bluetooth


## blacklist internal hci bluetooth interface
So the usb dongle is used for bluetooth.
find vendor and product id by hciconfig -a and lsusb
 place in blacklist file:

sudo nano /etc/udev/rules.d/81-bluetooth-blacklist.rules

SUBSYSTEM=="usb", ATTRS{idVendor}=="0e8d", ATTRS{idProduct}=="0717", ATTR{authorized}="0"


retrigger rules:
sudo udevadm control --reload-rules
sudo udevadm trigger

