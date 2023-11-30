Layer creation
==============

This doc will show how to create own layer

## Steps

- Run the command from `poky/build` directory to create the layer
  ```bash
  bitbake-layers create-layer ../meta-myLayer
  ```

- Add the layer in `build/conf/bblayers.conf` file
  ```bash
  bitbake-layers add-layer ../meta-myLayer/
  ```

> I have to modify one line in `meta-myLayer/conf/layer.conf` file. I have added
> ```bash
>  LAYERSERIES_COMPAT_../meta-myLayer = "sumo"
> ```
> Here, sumo is the branch name of the poky repository

- I have changed the python function name in `vim ../meta-myLayer/recipes-example/example/example_0.1.bb` as like as follows: `python do_display_banner()`

- And add the line at the end of that example file: `addtask display_banner before do_build`
- After that, from `build` directory executed `bitbake example` command. This shows the output in the console