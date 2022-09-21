Use OpenVPN in Ubuntu
=====================

- To install `OpenVPN` in Ubuntu follow [this link](https://gist.github.com/tienthanh2509/50094f55439e19af3a09911aa5c48852)
- Also the commands are written here
    ```sh
    curl -s https://swupdate.openvpn.net/repos/repo-public.gpg | apt-key add -
    echo "deb http://build.openvpn.net/debian/openvpn/stable xenial main" > /etc/apt/sources.list.d/openvpn-aptrepo.list
    apt update
    apt install -y openvpn
    ```
- Run OpenVPN
    ```sh
    sudo openvpn --config gw-UDP4-1194-karim-config.ovpn
    ```

- This file(`.ovpn`) will be given by the company/ provider