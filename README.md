# Support for the LED in Synaptics touchpads in Xorg

## Introduction

This repository provides the patches by Takashi Iwai from SUSE for
supporting the LED in Synaptics touchpads. Like the one that comes
with the
[HP Envy 14](https://secure.wikimedia.org/wikipedia/en/wiki/HP_Envy#Envy_14).
 
## Installation

To enable the support for the LED you must apply the two patches:

 1. Clone the repo:
 
     git clone git://github.com/perusio/xorg-synaptics-led-support.git

 2. Apply the `touchpad-led-2.6.28.patch` to the kernel source tree:
     
     patch -p1 -i /path/to/touchpad-led-2.6-28.patch -s --dry-run
   
   Check if there's no output. If there is there are problems applying
   the patch. Note that you should invoke the above command from the
   **root of the kernel source**. For example, if you're applying to
   kernel version 2.6.39, the root directory is `linux-2.6.39`.
   
   Now run `patch` to effectively **apply** the patch:
   
     patch -p1 -i /path/to/touchpad-led-2.6-28.patch -s
     
 3. Apply the `04-xf86-input-synaptics-clickpad-led-1.4.0.patch` to
    the xorg synaptics driver.
     
    I'll gloss over the details and instead point you to a
    [debian](http://debian.org) package I created that already
    contains the **patched** xorg synaptics driver:
    [http://debian.perusio.net/unstable](http://debian.perusio.net/unstable). This
    package is for **testing/unstable**. The instructions for adding
    my debian repository to your `sources.list` are given
    [here](http://debian.perusio.net).
    
## Dynamic Kernel Module System (DKMS)

I compile my own **custom** kernels. If you use debian **stock**
kernels you can use the
[Dynamic Kernel Module System](http://packages.debian.org/wheezy/dkms)
and build a debian package within that framework.

Detailed instructions regarding that are out of scope for this modest
README. Here's a
[wiki](http://tjworld.net/wiki/Linux/Ubuntu/Kernel/BuildDebianDKMSPackages)
that elaborates on how to do that.
