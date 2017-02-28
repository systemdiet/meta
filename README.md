System on a diet
================


What
----

This project aims to be an alternative to systemd, reduced in feature count and
slow moving.  Number of features have been removed where a suitable external
project exists, some defaults have been restored to previous values or
behaviour. Some non-code parts have been split to allow further customizations.


Goals
-----

Keeping certain level of 1-1 replacement of systemd is desired, as most modern
distros will not consider nor accept any 2nd base userspace system management
suite.

Backward compatibility is supposed to span over longer period, support for older
kernels.

Expected update frequency: low, only security updates in the core. Long-term
maintainability.  Provide namely the base functionality.


Why
---

You've heared all the arguments already, nothing new.  Disagreement with the
direction the systemd is heading. Lack of a potential replacement became
frustrating in connection with upstream's rush for features. Here's some code
to play with.

Update cycles:

The subsystems have different update cycles and different priorities.
Make it possible to update just eg. the hwdb and keep all daemons
running. No need to boot-cycle the machine just because new sub-package hwdb is
updated and built together with the process manager.

Compatibility:

* keep configuration via /etc/ files
* keep forward compatibility with upstream systemd (ie. make switch back to systemd possible without much hassle)
* possibliy provide a script to check a machine setup if diet will be able to support it
* keep some level of UI compatibility with sysvinit (rcservice scripts, runlevel aliases)


Who
---

J. Random Hacker.


Status
------

This is a research project and not in fully usable state yet.  I want to get
the most boring work done (splitting, packaging, integration) and see if it's a
viable path.  The code development is stalled (no bugfixes etc) until the
packaging is done.  Help is welcome but at the moment there's more on the
research side and there are no clear tasks or small issues to pick.
[TODO](TODO.md) The development is irregular and happens during the
[hackweeks](http://hackweek.suse.com) event.


The rest
--------

When the groundwork is done, the once refused enhancements could be considered
again, eg. support for other libc implementations.

*System on a low crap diet.*
