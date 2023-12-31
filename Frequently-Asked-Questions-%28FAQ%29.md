About Lubuntu
-------------

 * **What is Lubuntu?**
   * Lubuntu is an official flavor of Ubuntu designed to provide a lightweight but modern desktop experience, complete with a suite of useful applications.
 * **What's the difference between Lubuntu and Ubuntu?**
   * On the face of it, the big difference is the look and feel since they use a different desktop environment and different applications. Additionally, there's a notable difference in the resource footprint.
   * The reality is that there actually isn't much difference. Both are collections of specific packages available from the Ubuntu repository. Both are supported by the Ubuntu community. Both are run on Canonical's infrastructure. In that sense, except for those things specific to the desktop environment, anything that is applicable to Ubuntu is applicable to Lubuntu. As we like to say, Lubuntu /is/ Ubuntu.
 * **Who created Lubuntu?**
   * Mario Behling and Julien Lavergne originally created the project together, leading to the release of Lubuntu 10.04. Mario has not been an active contributor since those early days and [Julien moved on in 2018](https://lists.ubuntu.com/archives/lubuntu-devel/2018-May/001181.html). Simon Quigley was instrumental in the transition to LXQt at that time. The current developers are found [here](https://launchpad.net/~lubuntu-dev/+members#active).

Desktop Environment
-------------------

 * **What desktop environment does Lubuntu use? LXDE or LXQt?**
   * Lubuntu originally shipped with LXDE, but with the 18.10 release, LXQt became our desktop environment.
 * **Is the only difference between the LXDE and LXQt versions of Lubuntu the desktop environment?**
   * No. The entire landscape of applications was changed. Basically, there was a switch from using GTK+ to Qt applications. A table comparing the two paradigms can be found [here](https://phab.lubuntu.me/w/bugs/). A notable difference is the fact that we use the more general purpose Calamares installer instead of the rather Ubuntu-specific Ubiquity one in the LXQt versions.
 * **How are LXDE and LXQt related?**
   * The long story short is that in the face of problems with the newly released GTK+3, developers of the Razor-Qt project and LXDE developers combined efforts to create something unique relative to LXDE in Qt. It's not a rewrite with 1:1 feature completeness. The longer explanation can be found [here](https://github.com/lxqt/lxqt/wiki/History).
 * **Is LXQt better than LXDE?**
   * LXDE served Lubuntu very well for a very long time. Many releases of Lubuntu saw little in the way of changes because there was no need to change. LXDE has great stability. At time of writing, it is still not entirely functionally GTK+3 compatible and GTK 4 is out. This is problematic as that means [GTK+2 has reached end of life](https://blog.gtk.org/2020/12/16/gtk-4-0/). Beyond that, the pace of LXQt's development is much higher, making it easier for us to identify and resolve bugs.
 * **Can I still use LXDE with Lubuntu?**
   * Come April 2021, there will be no support from the Lubuntu team for LXDE versions of Lubuntu. The final LXDE release, 18.04, will still be supported until April 2023 by the Ubuntu community. 
   * Looking beyond April 2023, LXDE packages will still be available in the repositories, though, so you can continue to use them. You would just need to install an Ubuntu base system (with Ubuntu Server or a net install) and then install the LXDE metapackage. This is not supported by the Lubuntu team.
   * If you're currently on an LXQt release, you can install the LXDE metapackage and remove the LXQt components, so yes. But this isn't supported by the Lubuntu team.
   * Note that, as described in the release notes, upgrading from the LXDE versions to a LXQt is not supported. This is because you will end up with both paradigms on your system. It would succeed but your install would be very bloated and likely very confused.

Hardware
--------

 * **What happened to PPC support?**
   * The Ubuntu project dropped it. We alone kept support going as long as possible, but without an adequate amount of testing from the community, we were forced to [drop it](https://lists.ubuntu.com/archives/lubuntu-devel/2017-February/000970.html). We were the last Ubuntu flavor to support it. The last supported release was 16.04.
 * **What about 32 bit support?**
   * Again, the Ubuntu project stopped publishing images and, again, we alone kept support going as long as possible, but again, we lacked adequate testing and [dropped it](https://lubuntu.me/sunsetting-i386/). We were the last Ubuntu flavor to support it. The last supported release was 18.04.
   * We recommend our upstream parent, [Debian](https://www.debian.org/), if you still need 32 bit support. There's a lot of similarity to Ubuntu and it is incredibly popular, so it should prove to be a comfortable environment.
 * **Can I run Lubuntu on a Raspberry Pi?**
   * Yes, but not in the way you normally would on another architecture. At time of writing, there are no Raspberry Pi-specific desktop images being published except for the bog standard Ubuntu Desktop. The solution is to use the Ubuntu Server image and then install the Lubuntu Desktop package. More information is found [here](https://discourse.lubuntu.me/t/raspberry-pi-installation/2050/2).