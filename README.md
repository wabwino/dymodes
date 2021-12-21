# dymodes - dynamic [usb] mode switch
Sometimes a USB modem isn't recognized by a Linux machine because it is in storage-mode, not modem-mode. Installing `USB_ModeSwitch` usually solves the issue, but sometimes, `USB_ModeSwitch` doesn't know the right mode-switching command for a given modem. And that's where `dymodes` comes in: it tries to dynamically find the command.

## usage
Plug a modem into your machine and run the program. It will ask for a device to work on, then it will get to work. The process should take a few seconds.

```sh
sudo ./dymodes
```

The preferred way to run `dymodes` though is to pass it an `--edit-rules` argument, which instructs `dymodes` to edit `USB_ModeSwitch` rules (and to create a custom config for the modem) so that switching for that modem must henceforth be automatic. Otherwise, you'll have to rerun `dymodes` every time you plug that modem in.

```sh
sudo ./dymodes --edit-rules
```

When `--edit-rules` is given, `dymodes` backs up the original rules file in '~/.dymodes/'.


**NOTE**: Plug in only one modem when running `dymodes`.

<!--
## demo
The repo contains a short video that shows `dymodes` switch a Huawei modem from an "unrecognized" (storage) mode into a recognized modem state.
-->

## requirements
 - Python >= 3.6
 - USB_ModeSwitch

<!--
## removing dymodes rules
The probability of one wanting to remove rules and configs created by `dymodes` is very low. That's why there is no official way of removing them.
-->
