Variable
========

This doc will depict about several yocto variables

## Example file name

Consider, after creating a layer, there is a file/recipe(example) is preset. It's naming convention is `PN_PV_PR.bb`. Here,
  - PN = Package name
  - PV = Package version (default value `1.0`)
  - PR = Package revision (default value `r0`)

## Command

My example name is `example_0.1.bb`. From `poky/build` I have executed the following command and got the output.
  - package name
    ```bash
     bitbake -e example | grep ^PN=
    ```
    > Output: PN="example"

  - package version
    ```bash
    bitbake -e example | grep ^PV=
    ```
    > Output : PV="0.1"

  - package revision
    ```bash
     bitbake -e example | grep ^PR=
    ```
    > Output : PR="r0"

  - Workdir
    ```bash
    bitbake -e example | grep ^WORKDIR=
    ```
    > Output : WORKDIR="/home/vmash18/yocto/sources/tmp/work/i586-poky-linux/example/0.1-r0"
    
    > Why `yocto/sources`? Because, Initially I have set up may sources in `~/yocto/poky/build/conf/local.conf` file with desired path and that was `~/yocto/sources`
    
    > Format of WORKDIR is `PN/PV-PR`. Loom here, `example/0.1-r0` and match with the previous output

  - Source directory
    ```bash
    bitbake -e example | grep ^S=
    ```
    > Output : S="/home/vmash18/yocto/sources/tmp/work/i586-poky-linux/example/0.1-r0/example-0.1"

    > Format of source dir is : `WORKDIR/PN-PV`

  - Build directory
    ```bash
    bitbake -e example | grep ^B=
    ```
    > Output will be same as Source directory

    > Format of Build directory = Source directory

  - Destination directory : Where executable file of recipe will present
    ```bash
    bitbake -e example | grep ^D=
    ```
    > Output : D="/home/vmash18/yocto/sources/tmp/work/i586-poky-linux/example/0.1-r0/image"

