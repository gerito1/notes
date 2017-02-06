Some Notes tips and tricks.
---------------------------

#### Use X compression over ssh for smoother X sessions

> ssh -p 22 192.168.0.x -l user -YC

#### Optionally use a quickier chipher

For example like blowfish-cbc or arcfour > aes128-cbc > aes128-ctr etc [source](http://xmodulo.com/how-to-speed-up-x11-forwarding-in-ssh.html)

In my OPI 2

> ssh -p 22 192.168.0.x -l user -YC -c aes128-ctr

#### Locate devices ip conected to the local network.

Because dynamic IP addresses sometimes I don't know where my thing is...

> sudo arp-scan --interface=wlan0 --localnet

#### Stop graphical session.

Simply kill the dm (display manager). In Armbian Jessie (Orannge Pi 2, with XFCE-4 gui)

Stat/Stop

> sudo systemctl start nodm

> sudo systemctl stop nodm

Enable/Disable

> sudo systemctl enable nodm

> sudo systemctl disable nodm
