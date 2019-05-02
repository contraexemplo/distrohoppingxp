# distrohoppingxp 🐇

Hello, fellow human. 👋

I am one of those people who can't decide on which operational system to use and have a tendency to hop from one Linux distribution to another frequently. I am also an owner of an Inspiron 15 7567, a laptop far from ideal to distrohop seamlessly. Why? My unit, in particular, has the following specifications:

| Model number |                         i15-7567-A20P                         |
|------------------|:-------------------------------------------------------------:|
|     Processor    |   i7-7700HQ (Kaby Lake) Quad Core, 6MB Cache, up to 3.8 GHz   |
|   Graphics card  | NVIDIA GeForce GTX 1050Ti (Mobile), 4GB GDDR5 graphics memory |
|      Memory      |                       8GB, DDR4, 2400MHz                      |
|      Storage     |                        1TB 5400 RPM HDD                       |

As I tested a few Linux distributions, including Arch Linux (including Manjaro and Antergos), Ubuntu (including Xubuntu and Kubuntu), Debian and Fedora, I noticed a few things:

1. When using a USB stick, my attempts to test most distributions will fail as they usually won't boot due to forcing the use of **nouveau**, [a libre driver for NVIDIA cards](https://nouveau.freedesktop.org/wiki/). To boot successfully, you will need either to disabled nouveau before booting or use NVIDIA's proprietary driver. **Manjaro, in particular, will allow you to do that without much hassle**.
2. This laptop in particular uses [NVIDIA's Optimus technology](https://www.nvidia.com/object/optimus_technology.html), and you may experience a lot of issues with basic functionalities such as connecting external screens into your HDMI port. (Though a bit overwhelming at times, the Arch Linux wiki provides great insight to users about [NVIDIA Optimus](https://wiki.archlinux.org/index.php/NVIDIA_Optimus) and [Bumblebee](https://wiki.archlinux.org/index.php/bumblebee).)

As I prepared myself to permanently switch to [Qubes OS](https://www.qubes-os.org/) (and to document properly all the trouble I'll go through with my little buddy as current documentation is already deprecated), I thought, "There must be someone out there stumbling upon the same issues I encountered during my distrohopping times with this laptop, and they must be cursing the entire internet for not finding someone else with the same problems."

I figured it would be useful to write a couple of reports about my own experiences, and share it with anyone that may have something to add... Thus, this repository was born. ✨ Enjoy!

