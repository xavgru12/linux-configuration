bluetooth is setup to be dual by default, change to bredr
Open main.conf again: sudo nano /etc/bluetooth/main.conf

Find the line #ControllerMode = dual.

Change it to:
ControllerMode = bredr
(This forces "Basic Rate/Enhanced Data Rate" mode, which is more stable for input devices).

Restart Bluetooth: sudo systemctl restart bluetooth

----------
disable auto suspend:
echo "options btusb enable_autosuspend=n" | sudo tee /etc/modprobe.d/btusb_no_suspend.conf

----------
fast connect:
Scroll to the bottom and look for IdleTimeout.

If it's commented out (has a #), remove the # and set the value to 0:
IdleTimeout = 0

Look for FastConnectable and set it to true:
FastConnectable = true

Save (Ctrl+O, Enter) and Exit (Ctrl+X).

Restart the Bluetooth service:
sudo systemctl restart bluetooth
