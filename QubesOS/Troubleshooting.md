# Troubleshooting

## qvm-usb

Managing attached devices using the graphical interface may be unsuccessful at times. I recommend performing those operations in the command line on `dom0`.

### Severe input lag when utilizing a USB device

In my use experience, not all devices will successfully work with a single solution. Some devices such as a wireless mouse may malfunction if attached to *any* qubes. Others like keyboards may need to be re-attached to start working properly.

To do the latter, first list all available devices to obtain their `BACKEND:DEVID`:

`[user@dom0 ~]$ qvm-usb`

The output should be something like this:

```
BACKEND:DEVID DESCRIPTION USED BY
sys-usb:2-12 SY20100110203954_Integrated_Webcam
sys-usb:2-2 Compx.2.4G_Receiver
sys-usb:2-3 USB_USB_Keyboard
sys-usb:2-4 0cf3_e007
```

Attach the device to the intended qubes using the following command:

`[user@dom0 ~]$ qvm-usb attach $QUBES $BACKEND-DEVID`

where `$QUBES` is the name of the qubes in which you wish to attach a device, and `$BACKEND-DEVID` is the correspondent identification given by `qvm-usb`.

To detach devices, use:

`[user@dom0 ~]$ qvm-usb detach $QUBES $BACKEND-DEVID`

## Fedora-related issues

### chsh: command not found on Fedora TemplateVM
The package `util-linux-user` wasn't installed by default. To do so:

```
sudo dnf install util-linux-user
```
