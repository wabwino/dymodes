# dymodes - dynamic [usb] mode switch.
If your USB modem is not recognized by your Linux machine, chances are high that the modem is in storage mode. You need to pass it a command that will switch it into modem mode.   To achieve that, you can learn about `lsusb`; `usb_modeswitch`; and other tools, or you can just run this program: it will switch the mode for you.

## usage
Plug your modem into your machine and then run this program. It will ask you to choose the device it has to work on, then it will get to work. (Note that if your device is unfamiliar, the process might take several minutes).

```sh
sudo ./dymodes
```

If it successfully switches the mode of your modem, it will print a udev command you can manually include in your usb-modeswitch rules (/lib/udev/rules.d/40-usb_modeswitch.rules) so that you'll not have to re-run this program the next time you plug your modem in. Or you can just include an `--edit-rules` argument, which instructs dymodes to do the editing.

```sh
sudo ./dymodes --edit-rules
```

In an unlikely event that `--edit-rules` damages your system's modem "detection", dymodes creates a backup of the original usb-modeswitch rules in its working directory. You should be able to restore that file to its original place.

**NOTE**: Plug in only a single modem when running dymodes.

## requirements
 - python >= 3.4
 - lsusb
 - usb_modeswitch

*(Tools found on typical desktop Linux)*

## license
Public domain.