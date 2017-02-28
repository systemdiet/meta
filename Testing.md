Testing
=======

Experimental setup on openSUSE 13.2

Switch from systemd on 13.2
---------------------------

Note, that the network interface names will change after reboot. You can fix
after update and reboot if you can access the machine directly. Otherwise
rename the interface (eg. ens3) to eth0 and reboot with

* add repository (named system4 right now)
* zypper ref
* zypper dup --from system4
  * confirm all, bash completion filenames might clash
* mkinitrd
  * important step, otherwise the system will not boot as updating package *systemd* does not regenerate initrd and we get mixed versions of udev and systemd daemons
* sync
* reboot
  * the command *reboot* will not work (because of running systemd 210+ on top of 208 udev)
  * do the 'reisub' combo (echo X > /proc/sysrq-trigger)

References:

* http://download.opensuse.org/repositories/home:/dsterba:/system4/openSUSE_13.2/

Debugging startup
-----------------

Add the follwoing to kernel command line (eg /boot/grub2/grub.cfg, or /etc/default/grub)

> debug systemd.debug

remove

> splash=silent quiet

