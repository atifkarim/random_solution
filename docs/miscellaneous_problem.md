Miscellaneous Problem
=====================

In this doc solution of miscellaneous problem is discussed

## Mounting Driver problem in Ubuntu

While logout from windows abnormally and login in ubuntu then mounting problem occurs.
In the error message you will see the `driver address or name`
where the problem arises. Eg: `/dev/sda9` is the problematic one. Then open terminal and type

```sh
sudo ntfsfix /dev/sda9
```
here replace `/dev/sda9` part with the message that is showing in your error message.
Source taken from [here](https://askubuntu.com/a/696648/1128908)


## Ethernet problem in Ubuntu

See [here](https://askubuntu.com/a/71205/1128908). The steps are also written in the following lines:

```sh
sudo nano /etc/NetworkManager/NetworkManager.conf
```
change the line `managed=false` to `managed=true`. Save, stop and start `network manager`:
```sh
sudo service network-manager restart
```

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