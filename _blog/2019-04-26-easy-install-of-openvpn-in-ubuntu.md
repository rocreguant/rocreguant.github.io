---
title: "Easy install of OpenVPN in Ubuntu"
date: "2019-04-26"
categories: 
  - "gnulinux"
  - "hacks"
---

Sometimes it is useful to tunnel your connections through a server. Because it is located in a different country or simply to add an extra layer of security. What it is not always easy is to create the infrastructure. But that is solved now.

So to create the credentials we simply need to run this line `wget https://git.io/fj3wZ --no-check-certificate -O openvpn-install.sh; chmod +x openvpn-install.sh; sudo ./openvpn-install.sh`

The previous line downloads a [bash script](https://github.com/rocreguant/I-have-time/blob/master/openvpn-install.sh) and then executes it to create the necessary files.

Happy tunneling! :)
