# dymodes - dynamic [usb] mode switch.
if your usb modem is not detected by your linux machine, chances are high that the modem is in storage mode. you need to pass it a command that will switch it into modem mode.   to achieve that, you can learn about `lsusb`; `usb_modeswitch`; and other tools, or you can just run this program: it will switch the mode for you.

## usage
plug your modem into your machine and then run this program. it will ask you to choose the device it has to work on, then it will get to work. (note that if your device is unfamiliar, the process might take several minutes).

```sh
sudo ./dymodes
```

if it successfully switches the mode of your modem, it will print a udev command you can manually include in your udev rules (/lib/udev/rules.d/40-usb_modeswitch.rules) so that you'll not have to re-run this program the next time you plug your modem in.

but if you have no idea about udev rules, you can simply include an `--edit-rules` argument, which instructs dymodes to do the editing.

```sh
sudo ./dymodes --edit-rules
```

in an unlikely event that `--edit-rules` damages your system's modem detection, dymodes creates a backup of the original usb-modeswitch rules in its working directory. you should be able to restore that file to its original place.

**note**: plug in only a single modem when running dymodes.

## requirements
 - python >= 3.4
 - lsusb
 - usb_modeswitch
*(tools found on a typical linux distro)*

## license
public domain