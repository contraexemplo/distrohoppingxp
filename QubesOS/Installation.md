- **Version:** Qubes OS 4.0.1

- **Installation performed in:** May 2019

- **Installation medium:** USB drive with 8 GB of storage

## Issues

### Laptop restarts after a few minutes of interactions with the installer

#### Brief description

After a few moments interacting with the installer, the screen goes black and my laptop restarts. This happens both with Legacy and UEFI boot. It takes about one minute to get to Ananconda and another minute for it to freeze and trigger a reboot.

#### Using the basic graphics installer in Legacy mode

Unfortunately, X fails to startup.
```
Starting installer, one moment...
Anaconda 25.20.9 for Qubes R4.0.1 started.
  * installation log files are stored in /tmp  during the installation
  * shell is available on TTY2
  * if the graphical installation interface fails to start, try again with the inst.text bootoption to start text installation
  * when reporting a bug add logs from /tmp as separate text/plain attachments
12:29:32 Not asking for VNC because we don't have a network
12:29:32 X startup failed, aborting installation
12:29:32 X startup failed, aborting installation
The installation cannot continue and the system will be rebooted
Press ENTER to continue
  ```
Pressing `ENTER` will trigger a `Pane is dead` message.

#### Solution

**Spoiler:** Unsurprisingly, it seems like `nouveau` was the one triggering this issue. All actions described below happened on Legacy mode.

Press `TAB` with the option `Install QubesOS 4.0.1` highlighted. This will give you access to all kernal parameters that option will initialize with. Add the parameter `nouveau.modeset=0` just before `initrd.img`.
