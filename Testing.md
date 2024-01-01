# Updates


 * **Current development is on Lubuntu 24.04 [Noble Numbat](https://discourse.ubuntu.com/t/noble-numbat-release-schedule/35649).**
 * **Maintenance development applies to Lubuntu 23.10 [Mantic Minotaur](https://discourse.ubuntu.com/t/mantic-minotaur-release-schedule/34989) and Lubuntu 22.04 [Jammy Jellyfish](https://discourse.ubuntu.com/t/jj-release-schedule/23906).**

---

# General information


## What we do


The QA/Testing Team (which is informed by the [main Ubuntu QA team](https://wiki.ubuntu.com/QATeam)) is responsible for using formal test cases to check images of Lubuntu. The current [testing checklist can be found here](https://discourse.lubuntu.me/t/testing-checklist/4695) with some [documentation on understanding the testcases found here](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743). This allows the [Release Team](https://launchpad.net/~lubuntu-product-managers) to easily gauge the health of the images. This makes it possible to tell whether an image is functional enough to justify a release and determine where resources need to be allocated to make sure an image gets released. 

Other tests may be organized around application testing, new features, bug fixes, etc., but the primary and most significant role of the QA team concerns images.

This testing is split into two main types:

 1. **Daily image testing**: Daily images are constantly being tested to give us an early warning notice of any problems that could affect Milestone releases. This also gives us an opportunity to do more heavy testing to discover any bugs we hadn't noticed before.
 1. **Testing Milestone images**: Our most important job is preparing for release. A few days (usually two) before a milestone is due (according to our [release schedule](https://wiki.ubuntu.com/Releases)), the archive is frozen and Daily images stop being produced. The most recent image becomes the test image for the Milestone. These are called Beta, and Final, depending on the stage of the release cycle. When all images pass testing, the Final Release image is published.


## Getting Involved


 1. **Join the [Lubuntu QA](https://launchpad.net/~lubuntu-qa) team** (you'll need a Launchpad account).
 1. **[Join the main mailing lists](http://lubuntu.me/links/)**, specifically lubuntu-devel. Announcements often end up here, so it's pretty crucial.
 1. **Read the following tips for success.**
 1. **[Start your first test](https://wiki.ubuntu.com/Testing/ISO/Walkthrough)!**
 1. **Do not hesitate to [reach out](http://lubuntu.me/links/) and ask questions.** The mailing lists, chat, and forums are all good methods. We're here to help!

**🚨IMPORTANT🚨** All release stages are tracked by [the ISO Tracker](http://iso.qa.ubuntu.com/) where you can get the latest builds, see and allocate any bugs, and formally report testing results. ***It is essential to record all results on the ISO Tracker.*** Sending a report on the mailing list is great, but if you don't also record the results on the tracker, it is challenging to collate all the data.

**⚠️WARNING⚠️**The most important thing to do is to ***always be on the lookout for [bugs](https://phab.lubuntu.me/w/bugs/) and report them whenever you find them!*** Also, make sure to check for previously reported bugs and include them in your results if they're still applicable!


## Tips for success


 * **Using a development milestone is not suitable for daily production machines.** That is why, to play it safe, it's better to use [virtual machines](https://help.ubuntu.com/community/VirtualMachines), spare testing machines, and/or USB drives, especially with early milestone releases. Beta milestone releases are a bit more stable, but are still under heavy development to ensure the highest quality release possible.
 * **Testing on bare metal is important, too.** Some bugs are hardware dependent and would not be revealed if we only used virtual machines. This necessarily requires wiping the data from that machine, so make sure to [backup your important data](https://help.ubuntu.com/community/BackupYourSystem). 
 * **The most important part of testing is to actually install the system and check how the installation process will work.**  This is very important. Unless you're specifically doing a testcase on upgrades, don't upgrade. Fresh installs only, please.
 * ***Always* make sure to [check the integrity](https://help.ubuntu.com/community/HowToMD5SUM) of the downloaded ISO as well as the media it's installed on.** If either is off by a single bit, it can cause all sorts of inexplicable problems. At the very least, run the "Check disc for defects" option when booting the image.
 * **Use [zsync](https://help.ubuntu.com/community/ZsyncCdImage) to speed up repeated image downloads and to ensure automatic integrity checking.** Pro tip: copy an existing image and rename it to the name of a different image you want and run `zsync` on the different image and it will speed things up there, too.
 * **Don't lose track of which image you have**! Since images are changing daily (and sometimes more often than that) but do not have a filename that indicates which version it is, it's easy to make the mistake of testing the wrong image. `strings /path/to/iso | grep -m 3 Lubuntu` will show a line that includes the version number. So will the `cdrom` line in /etc/apt/sources.list from within the image. Using `stat -c %y /path/to/iso` will also give the last modified date, which should be helpful as well. Remember date/time is expressed in UTC.
 * **Do not mark a testcase as failed unless there is a critical error**. This would mean a failed boot, a failed installation, crashes, lack of intended functionality, etc. Often when we're right about to release, the Release Manager is scanning quickly to see the state of testing and these "false negatives" can be distracting. However, if in doubt, mark it as failed.


## Links


 * [Milestone Process](https://wiki.ubuntu.com/MilestoneProcess) - timing for a new Ubuntu release
 * [New Release Cycle Process](https://wiki.ubuntu.com/NewReleaseCycleProcess) - getting dailies started and development started after an Ubuntu release
 * [cdimage crontab](http://bazaar.launchpad.net/~ubuntu-cdimage/ubuntu-cdimage/mainline/view/head:/etc/crontab) - timing for building of all Ubuntu images (ours usually takes 90 minutes)
 * [status of building Lubuntu images](https://launchpad.net/~ubuntu-cdimage/+livefs/ubuntu/focal/lubuntu) 
 * [Lubuntu image building logs](http://people.canonical.com/~ubuntu-archive/cd-build-logs/lubuntu/)

---

*Contents of this page originated from the Ubuntu Wiki, all copyright goes to the respective author*
