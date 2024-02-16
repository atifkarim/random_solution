Miscellaneous Problem
=====================

In this doc solution of miscellaneous problem is discussed

## Mounting Driver problem in Ubuntu

While logout from windows abnormally and login in ubuntu then mounting problem occurs.
In the error message you will see the `driver address or name`
where the problem arises. Eg: `/dev/sda9` is the problematic one. Then open terminal and type the command

```sh
sudo ntfsfix /dev/sda9
```

Here, replace `/dev/sda9` part with the message that is showing in your error message.
Source taken from [here](https://askubuntu.com/a/696648/1128908)


## Ethernet problem in Ubuntu

### Wired connection Issue

- See [here](https://askubuntu.com/a/71205/1128908) to get description of the problem. The steps are also written in the following lines:

    ```sh
    sudo nano /etc/NetworkManager/NetworkManager.conf
    ```

- change the line `managed=false` to `managed=true`. Save, stop and start `network manager`:
    ```sh
    sudo service network-manager restart
    ```

### After suspend Ethernet connection is lost issue

After suspend my ubuntu 20.04 Ethernet connection cannot established again while I have tried to re-login. I have found a solution [here](https://askubuntu.com/a/1058760/1128908).

What I have done:

- At first to get the driver info I have used this command `sudo lshw -C network`

- This one has provided infos where I have looked for `description: Ethernet interface`. In this section I have found a line started with `configuration: autonegotiation=on broadcast=yes driver=r8168`. This line has more info but that are not important.

- In the directory `/etc/systemd/system/` I have created a file named `fix_r8168.service`

- I have copied and pasted the answer in that file by changing the driver number only
    ```sh
    [Unit]
    Description=Fix RTL-8168 Driver on resume from suspend
    After=suspend.target

    [Service]
    User=root
    Type=oneshot
    ExecStartPre=/sbin/modprobe -r r8168
    ExecStart=/sbin/modprobe r8168
    TimeoutSec=0
    StandardOutput=syslog

    [Install]
    WantedBy=suspend.target
    ```

- After this enabled the service by teh command `systemctl enable fix_r8168.service`.

The above steps has solved the issue.

## Problem with `unmet dependencies`

To solve follow [this](https://askubuntu.com/a/870051/1128908). Steps are:

```sh
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade
```

## Long boot time

After upgrading `Ubuntu 18` to `20` boot time was very long due to ```mysql```. A [Solution](https://askubuntu.com/a/1227490/1128908) will be found here. Steps are:

- Close the `mysql` service at start up
```sh
sudo systemctl disable mysql
```
- Then run `mysql` manualy
```sh
sudo service mysql start
sudo service mysql stop
sudo service mysql status
```

## Broken `Python`

See the solution [here](https://stackoverflow.com/a/46960872/10634362)

## Install Ubuntu with Windows

See [here](https://medium.com/linuxforeveryone/how-to-install-ubuntu-20-04-and-dual-boot-alongside-windows-10-323a85271a73).

## Connect bluetooth device

I have faced problem while trying to connect bluetooth headphone. It was not detected in the panel. This [post](https://medium.com/@karankajrolkar/ubuntu-20-04-bluetooth-earphones-not-connecting-ed2df2ef5a3d) has helped me to solve the problem.

## Activate finger gestures

T activate the gestures in Ubuntu follow [this link](https://medium.com/@yash9439/how-to-enable-touchpad-gestures-in-ubuntu-22-04-c0ec460c423)