Setup OpenVPN server for Rackspace Cloud
=======================================================

Script is tested on CentOS 6.0/6.2/6.3

Patches preferably as Github pull requests are welcome!

GPL version 2 licensed easy-rsa tools and example configuration copied
from OpenVPN project, Copyright (C) 2002-2010 OpenVPN Technologies, Inc.
See OPENVPN-COPYING.txt

Other parts Copyright 2013 Marius Voila <myself@mariusv.com>
Licensed under GPL version 2. 

INSTALLATION INSTRUCTIONS
=========================

**Centos on Rackspace**

- Create the Centos server

- Login to the machine

- Install zip ::

        sudo yum -y install zip

- Enable the EPEL repository. When writing this, it's as simple as: ::

        sudo rpm -iv http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm

  If the link does not work, see instructions at http://fedoraproject.org/wiki/EPEL

- Continue with the common instructions

**Common**

- Download the repo zip file and run the installation script: ::

        wget https://github.com/mariusv/raxOpenVPN/archive/master.zip
        unzip master.zip
        cd raxOpenVPN
        sudo sh setup.sh

- Let the script run. Take note if the server external ip address
  detection is succesful. If it's not, you need to edit the
  configuration files before using them.

- Download the configuration files from directory raxOpenVPN/openvpn.*,
  there is both a zipped file with all the config files and
  the plain configuration files

- Get your openvpn client to use the files.

    On Windows, after installing openvpn, just place the files in the openvpn
    configuration directory, shortcut link to the config dir is in the start menu.
    Also note, on Windows you need to run the OpenVPN GUI with administator
    privileges.

    On many Linux desktops, start VPN connection manager, and IMPORT the
    simpleopenvpn.ovpn file, make the vpn not start automatically.
    Do not move the certificate files afterwards, they are needed.
    Author has tested this on Ubuntu 12.04, the package to apt-get is
    network-manager-openvpn-gnome .

- Enjoy your very own VPN!

**TO DO**

- Support for Debian/Ubuntu
- Distribution check

Some notes
==========

Clients are configured to use Google public dns servers when
the vpn connection is active: https://developers.google.com/speed/public-dns/

Only one client certificate is generated, but it can be used simultaneously
with multiple connections. To generate more client certificates, see the
commented lines in the setup script.

If you keep the vpn server generated with this script on the internet for a
long time (days or more), consider either restricting access to the ssh port on
the server by ip addresses to the networks you use, if you know the addresses
you are most likely to use or at least change ssh from port 22 to a random
port.
