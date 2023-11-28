Create first basic Linux image
==============================

This document shares the information regarding kickstart of Yocto and creation of basic linux image to run using `qemu`

## Preparation of the environment

### Installation of required libraries

This steps starts with the installation of the yocto. I have followed here [This tutorial](https://dornerworks.com/blog/heres-how-you-can-build-your-own-custom-linux-distro-with-yocto/)

### Modifcation local.conf file

To modify this file I have followed [this youtube video](https://www.youtube.com/watch?v=5fj05BWryhM&list=PLwqS94HTEwpQmgL1UsSwNk_2tQdzq3eVJ&index=1&pp=iAQB&ab_channel=Tech-A-Byte). Only my target machine name is:

```sh
MACHINE ??= "qemux86"
```

### Summary of the steps


