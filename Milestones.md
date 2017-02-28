Hackweek 15 (2017)
------------------

tl;dr slow progress, packaging and docs, no coding or backports

day 1:
* catch up from the previous hw
* found out that the units/ hadn't been properly separated from git last time
* resolving build problems with recent gperf 3.1 that changed prototype, fixed
  by a few lines of sed
* not final build yet

day 2:
* gperf problems fixed
* consolidated notes to the meta/ git project, too messy to be published
* shuffling make variables to let units build and install
* integrating back to the main project until it works
* build success on 13.1, 13.2 and Tumbleweed
* install & boot test on 13.2, previously used, no problems
* install & boot test on a fresh Tumleweed
  * expected problems resolved
    * network names change: copy ifcfg-ens3 to ifcfg-eth0, wicked ifup
    * hostname from dhcp set properly
  * other problems without resolution
    * user@.service failed, some problem with pam, but does not affect login to
      root or other users
  * more tests
    * installed KDE5, Gnome, LXDE plus xdm and sddm
    * KDE5 starts, login ok, applications start, yeah there's practically no
      problem with running systemd v208 (from 2013) on a up-to-date distro
      (from 2017), somehow feels I'm still on a good track
      (to be correct about the version, some patches from v209 were backported
      to libsystemd so satisfy package dependencies and linker)

day 3: day 4: spent on other project

day 5:
* split hwdb from systemd package, build and install tests fine, easy
* split units from systemd package, too many packaging issues
* quick test on tumbleweed was fine, kde5 up, there are various error
  messages in the logs
* quick test on 13.2: does not boot, stuck in dracut, some services
  failed to start
* writeups


Hackweek 14 (2016)
------------------

Some non-code parts split to separate gits but still installed from the single
systemd package. Started the systemdie github repo.


Hackweek 13 (2015)
------------------

* [v208](../../systemdiet/commits/v208)
  * unmodified upstream release

* [v208.1](../../systemdiet/commits/v208.1)
  * merged upstream branch with stable-208 patches (commit 75a17dd008d2a97df4c8901216b875382af9f570, date 2014-11-06)

* [v208.2](../../systemdiet/commits/v208.2)
  * synchronize hwdb files up to upstream version 219

* [v208.3](../../systemdiet/commits/v208.3)
  * removed readahead
  * removed qrcode
  * removed localectl, localed
  * removed timedatectl, timedated

* [v208.4](../../systemdiet/commits/v208.4)
  * removed nspawn
  * removed efi
  * removed machinectl, machined
  * removed hostnamectl, hostnamed

* [v208.5](../../systemdiet/commits/v208.5)
   * *net.ifnames=0* is now default, http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/
      * for simple (1 network card) setups it's overcomplicating things
      * the "classical" shorter names are readable and human friendly
      * where interface name stability is required, udev rules can pin a MAC to a given name
      * "we believe that" the physical device location encoded in the interface name is not interesting to the user, unlike the presumed _use_

* [v208.6](../../systemdiet/commits/v208.6)
   * new libsystemd.so consisting of daemon, login and id128 libraries
   * library symbol version compatibility 209 (covers base packages)
   * no need to rebuild base packages that require 209 (procps, polkit ...)
   * no need to do bootstrap with systemd-mini
   * works on openSUSE 13.2 as replacement of default distro packages

* [v208.7](../../systemdiet/commits/v208.7)
   * removed gudev (removed upstream, libgudev exists externally)
   * remove gtk-doc
   * revert to minimal version of kmod 14
   * remove hwdb, track by separate git, not packaged separately yet
   * remove python bindings (removed upstream)
   * recognize only "systemd.debug" and "systemd.quiet" kernel boot parameters, "debug" and "quiet" shall affect only kernel again


Hackweek 11 (2015)
------------------

Research the project 'uselessd', packaging, exploring system package
dependencies. (More notes burried somewhere.)
