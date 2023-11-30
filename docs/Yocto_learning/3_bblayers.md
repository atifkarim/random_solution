BBlayers
========

## Objective

This document will depict regarding `build/conf/bblayers.conf` file

## Purpose

This file contains the information of the layers.
- Layers are collection of metadata that provides configuration information, recipe configuration and files.
- Recipe are suitable instruction to building packages
    - Where to get source codes
    - Which patches to apply
    - How to configure the source
    - How to compile
- Usually layers name starts with `meta` word. It is a convention to use.


## Command

- To show which layers are added use the following command from `poky/build` directory(Do not forget to `source oe-init-build-env` if not done yet):
  ```bash
  bitbake-layers show-layers
  ```

-  Output could be as like as follows:
  ```bash
  NOTE: Starting bitbake server...
  layer                 path                                      priority
  ==========================================================================
  meta                  /home/vmash18/yocto/poky/meta             5
  meta-poky             /home/vmash18/yocto/poky/meta-poky        5
  meta-yocto-bsp        /home/vmash18/yocto/poky/meta-yocto-bsp   5
  ```

- One can new layers in the `bblayers.conf` file manually or using command(Here, as a random manner I have added `meta-skeleton` layer):
  ```bash
  bitbake-layers add-layer ../meta-skeleton/
  ```
  After this open the `build/conf/bbblayers.conf` file and you will see as like as:
  ```bash

  BBLAYERS ?= " \
  /home/vmash18/yocto/poky/meta \
  /home/vmash18/yocto/poky/meta-poky \
  /home/vmash18/yocto/poky/meta-yocto-bsp \
  /home/vmash18/yocto/poky/meta-skeleton \
  "
  ```

- To remove the layer run
  ```bash
  bitbake-layers remove-layer ../meta-skeleton
  ```
  or
  ```bash
  bitbake-layers remove-layer meta-skeleton
  ```