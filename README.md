# dymodes - dynamic [usb] mode switch.
Sometimes a USB modem isn't recognized by a Linux machine because it is in storage-mode, not modem-mode. Installing `usb_modeswitch` usually solves the problem, but sometimes, `usb_modeswitch` doesn't know the right mode-switching command for a given modem. And that's where `dymodes` comes in: it dynamically tries to find the right command.

## usage
Plug a modem into your machine and run the program. It will ask for a device to work on, then it will go to work. (Note that in some cases, the process might take several minutes.)

```sh
sudo ./dymodes
```

After successful switching, it prints a command that should be added to usb_modeswitch rules (/lib/udev/rules.d/40-usb_modeswitch.rules) so that the switching for that modem must henceforth be automatic. (Otherwise, you'll have to rerun this program every time you plug the modem in). Or, you can just include an `--edit-rules` option, which instructs `dymodes` to edit the rules itself.

```sh
sudo ./dymodes --edit-rules
```

When `--edit-rules` is given, `dymodes` backs up the original rules file in the current/working directory.

**NOTE**: Plug in only one modem when running `dymodes`.

## requirements
 - python >= 3.4
 - usb_modeswitch
 - lsusb