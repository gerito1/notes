Some Notes tips and tricks.
---------------------------

* Use X compression over ssh for more fluid X sessions
> ssh -p 22 192.168.0.x -l user -XC

* Optionally use a quickier chipher like blowfish-cbc or arcfour > aes128-cbc > aes128-ctr etc source http://xmodulo.com/how-to-speed-up-x11-forwarding-in-ssh.html

For example in my OPI 2

> ssh -p 22 192.168.0.x -l user -XC -c aes128-ctr

* Locate devices ip conected to the local network. Because dynamic IP addresses sometimes I cannot connect to the device I want to.

> sudo arp-scan --interface=wlan0 --localnet

* Armbian (Orannge Pi 2, with XFCE-4 gui) Stop graphical session. Simply kill the dm (display manager)

> sudo systemctl stop nodm

> sudo systemctl start nodm

> sudo systemctl disable nodm

> sudo systemctl enable nodm
