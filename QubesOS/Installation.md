- **Version:** Qubes OS 4.0.1

- **Installation performed in:** May 2019

- **Installation medium:** USB drive with 8 GB of storage

## Issues

### Laptop restarts after a few minutes of interactions with the installer

#### Brief description

After a few moments interacting with the installer, the screen goes black and my laptop restarts. This happens both with Legacy and UEFI boot. It takes about one minute to get to Ananconda and another minute for it to freeze and trigger a reboot.

#### Failed attempts to solve the issue

I tested a few other options before ultimately finding out what was crashing Anaconda. For instance, using the basic graphics installer in Legacy mode. Unfortunately, X fails to startup:
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
Pressing `ENTER` would trigger a `Pane is dead` message and lead me to forcefully shut down the machine.

I also updated my BIOS from version 1.8.1 to 1.9.0, and attempted to edit some installation files to no avail.

#### Solution

It seems like `nouveau` was the one triggering this issue. All actions described below were performed on Legacy mode only. A test on UEFI mode is pending.

Legacy mode is the only one of the two modes with a boot menu. It will give you three options: Install Qubes R. 4.0.1, test this media & install Qubes R.4.0.1 and troubleshooting. Press `TAB` with the option `Install Qubes R4.0.1` highlighted. This will give you access to all parameters that option will initialize with:

`> mboot.c32 xen.gz console=none --- vmlinuz inst.stage2=hd:LABEL=Qubes-R4.0.1-x86_64 i915.alpha_support=1 quiet rhgb rd.live.check --- initrd.img`

Add the parameter `nouveau.modeset=0` between `quiet rhgb` and `initrd.img`. This will prevent `nouveau` from initializing as set by default. Press `ENTER` to proceed with the installation.

**Note:** If you have a habit of installing operational systems on UEFI mode, your Qubes OS installation may not boot automatically. Enter the boot options menu on your BIOS, go to `Change Boot Mode Settings`and change it to `Legacy Mode`. Make sure to also check `BIOS Setup` to see if `qubes` is properly marked on the `Boot Sequence` menu.
