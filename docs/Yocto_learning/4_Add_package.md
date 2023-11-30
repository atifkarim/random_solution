Add package
===========

This document will show how to add package in custom linux

## Check in yocto

- Open the yocto Linux using qemu:
  ```bash
  cd ~/yocto/poky
  source oe-init-build-env
  ```
- From `build` directory, run qemu command
  ```bash
  runqemu ~/yocto/sources/tmp/deploy/images/qemux86/
  ```
- After opening yocto terminal type any package, eg: `python` or `git`, you can see that those are not found

## Check package

- At first have to check the packages are available or not. From `~/yocto/poky/build` directory type
  ```bash
  bitbake-layers show-recipes
  ```
  It will provide a huge list which is not reader friendly.

- So, use only the following
  ```bash
  bitbake-layers show-recipes python3
  ```

  It will show the following output
  ```bash
  w-recipes python3
  NOTE: Starting bitbake server...
  Loading cache: 100% |############################################| Time: 0:00:00
  Loaded 1282 entries from dependency cache.
  === Matching recipes: ===
  python3:
  meta                 3.5.5
  ```
  It is showing that, `python3` is available and in `meta` layer


## Add package

- At first, check in `bblayers.conf` the `meta` layer is added or not. If not, add it

- Now, open the `conf/local.cpnf` file and add the following lines(I will add `python3` and `git`)
  ```bash
  IMAGE_INSTALL_append = " python3"
  IMAGE_INSTALL_append = " git"
  ```