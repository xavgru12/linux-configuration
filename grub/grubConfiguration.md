in /etc/gru /etc/grub.d/40_custom

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Windows 11' {
    search --fs-uuid --no-floppy --set=root 5CA7-745A 
    chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}




 with --set=root uuid from efi partition where ubuntu and microsoft bootloader is and chainloader like it is written
after modification, cmd: sudo update-grub
in /etc/default/grub, change these two lines for grub to appear during startup, if no button is pressed for 20 minutes, it will boot into ubuntu

#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=20

in order for the changes to take effect, execute this and then reboot:
sudo update-grub

