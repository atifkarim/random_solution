Mount iphone
============

## Objectives

This doc will show how to connect iphone with Linux machine to transfer photos.

## Tested Gadgets

This experiment has tested on:
- iphone XS Max(OS version: )
- Ubuntu OS (`Linux ash-X556UQK 6.2.0-37-generic #38~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Nov  2 18:01:13 UTC 2 x86_64 x86_64 x86_64 GNU/Linux`)

## Create connection

### Required software

- I have used here `ifuse` to mount the iphone. Install it via terminal: `sudo apt-get install ifuse`
- No software is needed to install on iphone

### Mount iphone

- At first, connect the iphone via data/usb/lighting cable. In this stage you can see in the file manager only `Documents of IPHONE_USER_NAME`.
- Open the terminal in Linux machine and type:
  ```bash
  mkdir ~/iphone
  ifuse ~/iphone
  ```
- Now, you can see the `iphone` name or logo on your file manager
- You can double click on that symbol/name to see the content of the iphone or just navigate via terminal to copy the content

> In my case, I have to do the job via terminal as I can see the `iphone` logo but after entering the directory was empty

### Transfer data

- Now, simply select your destination directory and copy all files from iphone. What I have done:
  ```bash
  mkdir ~/new_pic
  cp -r ~/iphone/DCIM/* ~/new_pic/
  ```

- After completion unmount the directory by right click on the iphone logo/name from the file manager and unplug the cable.
  
### Bonus

To check the size of the contents of any directory which contains several sub directories in Linux:

```bash
du -shBG directory_path
```