# dymodes - dynamic [usb] mode switch.
Sometimes a USB modem isn't recognized by a computer because the modem is in storage-mode. Installing `usb_modeswitch` usually solves the issue (as `usb_modeswitch` switches attached modems to modem-mode on the background). But sometimes, it doesn't know the right command for a given modem. And that's where `dymodes` comes in; it tries to dynamically find the right command.

## usage
Plug a modem into your machine and run this program. It will ask for a device to work on, then it will get to work. (Note that in some cases, the process might take several minutes.)

```sh
sudo ./dymodes
```

If it successfully switches mode of the modem, it will print a udev-command you can manually add to the usb-modeswitch rules (/lib/udev/rules.d/40-usb_modeswitch.rules) so that you'll not have to re-run this program the next time you plug that modem in. Or, you can just include an `--edit-rules` option, which instructs `dymodes` to do the editing.

```sh
sudo ./dymodes --edit-rules
```

If `--edit-rules` is given, `dymodes` backs up the original rules file in its working directory; just in case things might not work properly and you might want to restore the original rules.

**NOTE**: Plug in only one modem when running `dymodes`.

## target platform
 - Linux

## requirements
 - Python >= 3.4
 - usb_modeswitch
 - lsusb

## license
Public domain.