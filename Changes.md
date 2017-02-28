Changes that diverge from systemd
=================================

Default settings
----------------

* *net.ifnames=0* -- also disabled in 'udev' rules, and udev 'persistent network
  names' functionality restored. The reason of the change upstream is not
  particularly compelling, the core of the argument is "we believe this is
  better", the NIC naming suits best for networkd.

* kernel command line 'debug' is not affected, instead 'systemd.debug' is used
  for the purposes of systemd that interfered with the documented behaviour
  [link to upstream bug/WONTFIX]
  > debug -> systemd.debug
  > quiet -> systemd.quiet

Removed parts
-------------

* gudev [LINK to the separate project]
* gtk-docs
* locale
* qrencode
* timedate -- removed in systemd as well [REFERENCE]
* nspawn
* efi
* machinectl, machined
* hostnamectl, hostnamed
  - /etc/hostname, /etc/HOSTNAME, dhcp, your other network daemon


Packaged separately
-------------------

* hwdb -- data-only, different update cycle
* udev rules --
* systemd units -- most users are fine with the defaults, but it should be
  possible to provide own set of full targets set, eg. do a minimal boot up
  sequence, or drop dependency on initrd
* shell completions --
