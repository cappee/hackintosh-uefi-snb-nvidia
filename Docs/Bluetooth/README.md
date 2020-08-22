#  Patching Bluetooth

I bought an USB bluetooth dongle on eBay for 2€ and I found out only after receving that is a Cambridge Silicon Radio (with PID 1 and VID 2578).<br>
In Catalina it works OOB, but in High Sierra (strangely) it doesn't.<br>
So I found a [topic](https://www.tonymacx86.com/threads/bluetooth-problems.174289/) in tonymacx86 that helped me so much.

## Procedure

* We have to remove IOBluetoothFamily.kext from /S/L/E<br>
`sudo rm -Rf /System/Library/Extension/IOBluetoothFamily.kext`

* Then we need copy older kexts in /S/L/E<br>
`sudo cp -r AppleMultitouchDriver.kext /System/Library/Extension/`<br>
`sudo cp -r AppleBluetoothMultitouch.kext /System/Library/Extension/`<br>
`sudo cp -r IOBluetoothFamily.kext /System/Library/Extension/`<br>
`sudo cp -r IOBluetoothHIDDriver.kext /System/Library/Extension/`<br>

* Finally we can generate new kexts cache and reboot<br>
`sudo kextcache -i /`

## Screenshots

You can see my Bluetooth working in those screenshots
![](https://github.com/gabrielecappellaro/hackintosh-uefi-snb-nvidia/blob/master/Images/Bluetooth.png)
![](https://github.com/gabrielecappellaro/hackintosh-uefi-snb-nvidia/blob/master/Images/SpotifyOnBluetooth.png)
