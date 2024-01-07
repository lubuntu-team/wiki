# Low-Hanging Fruit

**This is a working document. It may become outdated once newer contributors become less new. Always ask in [the Lubuntu Development channel](https://lubuntu.me/links). Thanks!**

Rough prerequisites:
 - Ask nicely for an account on git.lubuntu.me (so you can create merge requests).
 - Have a basic understanding of Git. Try to keep commit messages useful, and the commits themselves self-contained. Be professional, but correctly executed wittiness will never be admonished.
 - Vim is great. We have a bias towards Vim. You don't have to use Vim, but it's something we'd recommend you learn.
 - Being able to effectively search the Internet is an excellent skill to have.
   - You can use ChatGPT as a **reference**, but it'll be obvious to us if you use it wholesale, no matter how clever you think you are. :)
 - Be respectful, and read over the [Ubuntu Code of Conduct](https://ubuntu.com/community/ethos/code-of-conduct).
 - Create a [Launchpad](https://launchpad.net/) account, and get some familiarity with both [Ubuntu](https://ubuntu.com/community/membership) and [Lubuntu](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Membership) Membership. **Lubuntu is part of the Ubuntu community.**

If you have any questions, we are happy to help. Mentorship is important to us in Lubuntu, and no question is too stupid. We're happy to go slow with you for the first few tasks until *you* can take your training wheels off. :)

------

*Key: 1 is easiest, 5 is hardest**

This list is meant to detail starter tasks for newer contributors. If you'd like to take one of these items, please say so in the Lubuntu Development channel, so we know you're working on it:
 - [ ] [1] Figure out the correct spelling/grammar for "Wi-Fi" in English, and search both the [nm-tray source code](http://github.com/palinek/nm-tray/) and our [new lubuntu-installer-prompt source code](https://git.lubuntu.me/Lubuntu/installer-prompt) for the incorrect versions. Submit a simple, concise pull request to both fixing this.
 - [ ] [3] [Calamares fails to open "donate" or "Lubuntu support"](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1981473)
 - [ ] [3.5] Convert [our pkgselect QML file](https://git.lubuntu.me/Lubuntu/calamares-settings-ubuntu/src/branch/ubuntu/noble/common/modules/pkgselect) to a dedicated .ui file (perhaps with Qt 5 Designer), and manipulate the (currently non-working) actions with C++/Qt 5.
    - Full installation should automatically check all four boxes, regular install should automatically uncheck all of the boxes but leave them enabled, and minimal install should hide that entire checkbox section.
    - We have **tons** of [packaging documentation](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging), but the only command you will need to know for this is `sudo apt build-dep calamares-settings-ubuntu && dpkg-buildpackage -us -uc -b -rfakeroot`. This is ran in the same directory *as* `debian/` (meaning, if you run `ls`, `debian/` will be listed as one of the items in the current directory). You may need to install the `fakeroot` package.
 - [ ] [2] Add support for `/etc/sddm.d` in the [SDDM Configuration Editor](https://github.com/qtilities/sddm-conf/issues/36). Fix as many bugs as you can find.
 - [ ] [3] Work with Aaron Rainbolt (arraybolt3) to finish up [Lubuntu Update](https://git.lubuntu.me/Lubuntu/lubuntu-update). Use it and find bugs to fix.
 - [ ] [3.5] Figure out how to change the Qt pallette based on how lxqt-config-appearance does it, and add a toggle for it to the installer prompt or somewhere else where it makes sense.
 - [ ] [3] [Granular Pause of Idleness Checks](https://github.com/lxqt/lxqt-powermanagement/issues/389)
 - [ ] [5] Fix as many of [the existing LXQt Power Management issues](https://github.com/lxqt/lxqt-powermanagement/issues) as you can

If you run out of tasks, want something less technical, or just want to improve your writing skills, the [Lubuntu Manual](https://git.lubuntu.me/Lubuntu/manual) always needs more help.

-----

The next step after some of these basic programming-only items would be to start with some packaging, and strive to become an official member of the project. Both you and us will "just know" when you're ready for the next step. Many developers started off by also doing bug triage, so they can **understand** the software they're writing. Helping other users with support is a great idea as well.

Best of luck, don't be afraid to ask questions and go the extra mile!
