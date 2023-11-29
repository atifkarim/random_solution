Yocto - Create Custom Linux
===========================

One of my wish to know how to deal with embedded devices and for which one of the most important part is know the working principle of Linux system. According to this path, I have found that, embedded devices are probe to interact with tiny size of Linux which is known as Custom Linux where only required libraries will be present. And for this purpose, `yocto` is a renowned tool regarding which the developer of this platform is announced as -> " It is not an Linux distribution, it creates a custom one for you."

## Background

This documents serves the walking journey of mine to learn this tool. Rather than using any embedded board due to some constrains, I am setting up a virtualized environment using `KVM` and `QEMU`. As an operating system I am using `Ubuntu 18.04 LTS (Long Term Support)`

- My host machine's(aka virtual machine) details is as like as follows where I have installed Yocto:
```cli
vmash18@vmash18-Standard-PC-Q35-ICH9-2009:~$ uname -r
5.4.0-150-generic

vmash18@vmash18-Standard-PC-Q35-ICH9-2009:~$ uname -a
Linux vmash18-Standard-PC-Q35-ICH9-2009 5.4.0-150-generic #167~18.04.1-Ubuntu SMP Wed May 24 00:51:42 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```

## Steps

In this section I will try to add the theme of the steps by which I have learned this technology.

- [Installation and first trial](1_yocto_intro.md)
- [Local configuration](2_local_conf.md)
- [BBlayers configuration](3_bblayers.md)

## Sources

- [My first step](https://dornerworks.com/blog/heres-how-you-can-build-your-own-custom-linux-distro-with-yocto/)
- [An awesome youtube tutorial which has helped me a lot](https://www.youtube.com/watch?v=5fj05BWryhM&list=PLwqS94HTEwpQmgL1UsSwNk_2tQdzq3eVJ&index=1&pp=iAQB&ab_channel=Tech-A-Byte)
- [Quickstart guide](https://erickof.medium.com/yocto-project-tutorial-baking-a-minimal-linux-image-from-scratch-625b3e65f768)
- [Yocto Official documentation](https://docs.yoctoproject.org/brief-yoctoprojectqs/index.html)