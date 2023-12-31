Software inevitably has bugs. Sometimes despite the most rigorous testing, bugs still get through. Luckily, bug reporting is an easy way to alert developers to the need to solve an issue. Additionally, it's easier to analyze and troubleshoot bugs in a central repository than it is on a mailing list or chat.

# How to report bugs

 1. **Get a [Launchpad account](https://help.launchpad.net/YourAccount/NewAccount)**, as all bugs are tracked there.¹
 1. For the bug reporting tools to automatically collect important data, **install [apport](https://wiki.ubuntu.com/Apport) and make sure it's enabled**.²
 1. To create the bug report, open the terminal and run: **`ubuntu-bug` name_of_the_affected_package** (see below for a list of packages).³
 1. **Subscribe the Lubuntu Packages Team** (~lubuntu-packaging) to the bug report.
 1. Read the documentation below for advice to **write an effective bug report**.

## Package Names

NOTE: When in doubt about what package to file the bug against, please use [lubuntu-meta](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta).

## Common packages

| component | package
| ----- | -----
| settings | [lubuntu-default-settings](https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings)
| artwork | [lubuntu-artwork](https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork)
| splash screen logo | [lubuntu-artwork](https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork)
| splash screen text | [lubuntu-artwork](https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork)
| display manager settings | [lubuntu-artwork](https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork)
| installer settings | [calamares-settings-ubuntu](https://bugs.launchpad.net/ubuntu/+source/calamares-settings-ubuntu)
| metapackage | [lubuntu-meta](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta)

## Core desktop environment

| component | LXDE (≤18.04) | LXQt (≥18.10) | notes
| ----- | ----- | ----- | -----
| window manager | [openbox](https://bugs.launchpad.net/ubuntu/+source/openbox) | [openbox](https://bugs.launchpad.net/ubuntu/+source/openbox)
| display manager | [lightdm](https://bugs.launchpad.net/ubuntu/+source/lightdm) | [sddm](https://bugs.launchpad.net/ubuntu/+source/sddm)
| session manager | [lxsession](https://bugs.launchpad.net/ubuntu/+source/lxsession) | [lxqt-session](https://bugs.launchpad.net/ubuntu/+source/lxqt-session)
| application launcher | [lxpanel](https://bugs.launchpad.net/ubuntu/+source/lxpanel) | [lxqt-runner](https://bugs.launchpad.net/ubuntu/+source/lxqt-runner) | has run dialog
| taskbar | [lxpanel](https://bugs.launchpad.net/ubuntu/+source/lxpanel) | [lxqt-panel](https://bugs.launchpad.net/ubuntu/+source/lxqt-panel)
| file manager | [pcmanfm](https://bugs.launchpad.net/ubuntu/+source/pcmanfm) | [pcmanfm-qt](https://bugs.launchpad.net/ubuntu/+source/pcmanfm-qt) | also manages desktop
| notification daemon | [xfce4-notifyd](https://bugs.launchpad.net/ubuntu/+source/xfce4-notifyd) | [lxqt-notificationd](https://bugs.launchpad.net/ubuntu/+source/lxqt-notificationd)
| authentication agent | [lxpolkit](https://bugs.launchpad.net/ubuntu/+source/lxpolkit) | [lxqt-policykit](https://bugs.launchpad.net/ubuntu/+source/lxqt-policykit)
| screen locker | [light-locker](https://bugs.launchpad.net/ubuntu/+source/light-locker) | [xscreensaver](https://bugs.launchpad.net/ubuntu/+source/xscreensaver)
| Bluetooth manager | [blueman](https://bugs.launchpad.net/ubuntu/+source/blueman) | [bluedevil](https://bugs.launchpad.net/ubuntu/+source/bluedevil)

## Configuration

| component | LXDE (≤18.04) | LXQt (≥18.10)
| ----- | ----- | -----
| window manager configuration | [obconf](https://bugs.launchpad.net/ubuntu/+source/obconf) | [obconf-qt](https://bugs.launchpad.net/ubuntu/+source/obconf-qt)
| hot key configuration | [lxhotkey](https://bugs.launchpad.net/ubuntu/+source/lxhotkey) | [lxqt-globalkeys](https://bugs.launchpad.net/ubuntu/+source/lxqt-globalkeys)
| theme configuration | [lxappearance](https://bugs.launchpad.net/ubuntu/+source/lxappearance) | [lxqt-config](https://bugs.launchpad.net/ubuntu/+source/lxqt-config)
| monitor settings | [lxrandr](https://bugs.launchpad.net/ubuntu/+source/lxrandr) | [lxqt-config](https://bugs.launchpad.net/ubuntu/+source/lxqt-config)
| input settings | [lxinput](https://bugs.launchpad.net/ubuntu/+source/lxinput) | [lxqt-config](https://bugs.launchpad.net/ubuntu/+source/lxqt-config)

## Default applications

| component | LXDE (≤18.04) | LXQt (≥18.10)
| ----- | ----- | -----
| installer | [ubiquity](https://bugs.launchpad.net/ubuntu/+source/ubiquity) | [calamares](https://bugs.launchpad.net/ubuntu/+source/calamares)
| software center | [gnome-software](https://bugs.launchpad.net/ubuntu/+source/gnome-software) | [plasma-discover](https://bugs.launchpad.net/ubuntu/+source/plasma-discover)
| package manager | [synaptic](https://bugs.launchpad.net/ubuntu/+source/synaptic) | [muon](https://bugs.launchpad.net/ubuntu/+source/muon)
| deb installer | [gdebi](https://bugs.launchpad.net/ubuntu/+source/gdebi) | [libqapt](https://bugs.launchpad.net/ubuntu/+source/libqapt) or [plasma-discover](https://bugs.launchpad.net/ubuntu/+source/plasma-discover)
| archive tool | [file-roller](https://bugs.launchpad.net/ubuntu/+source/file-roller) | [ark](https://bugs.launchpad.net/ubuntu/+source/ark)
| task manager | [lxtask](https://bugs.launchpad.net/ubuntu/+source/lxtask) | [qps](https://bugs.launchpad.net/ubuntu/+source/qps)
| partition tool | [gnome-disk-utility](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility) | [partitionmanager](https://bugs.launchpad.net/ubuntu/+source/partitionmanager)
| disc burner | [xfburn](https://bugs.launchpad.net/ubuntu/+source/xfburn) | [k3b](https://bugs.launchpad.net/ubuntu/+source/k3b)
| terminal | [lxterminal](https://bugs.launchpad.net/ubuntu/+source/lxterminal) | [qterminal](https://bugs.launchpad.net/ubuntu/+source/qterminal)
| text editor | [leafpad](https://bugs.launchpad.net/ubuntu/+source/leafpad) | [featherpad](https://bugs.launchpad.net/ubuntu/+source/featherpad)
| music player | [audacious](https://bugs.launchpad.net/ubuntu/+source/audacious) | [vlc](https://bugs.launchpad.net/ubuntu/+source/vlc)
| video player | [gnome-mpv](https://bugs.launchpad.net/ubuntu/+source/gnome-mpv) | [vlc](https://bugs.launchpad.net/ubuntu/+source/vlc)
| image viewer | [gpicview](https://bugs.launchpad.net/ubuntu/+source/gpicview) | [lximage-qt](https://bugs.launchpad.net/ubuntu/+source/lximage-qt)
| drawing program | [mtpaint](https://bugs.launchpad.net/ubuntu/+source/mtpaint) | [libreoffice](https://bugs.launchpad.net/ubuntu/+source/libreoffice)
| web browser | [firefox](https://bugs.launchpad.net/ubuntu/+source/firefox) | [firefox](https://bugs.launchpad.net/ubuntu/+source/firefox)
| email | [sylpheed](https://bugs.launchpad.net/ubuntu/+source/sylpheed) | [trojita](https://bugs.launchpad.net/ubuntu/+source/trojita)
| calculator | [galculator](https://bugs.launchpad.net/ubuntu/+source/galculator) | [kcalc](https://bugs.launchpad.net/ubuntu/+source/kcalc)
| document viewer | [evince](https://bugs.launchpad.net/ubuntu/+source/evince) | [qpdf](https://bugs.launchpad.net/ubuntu/+source/qpdf)
| word processor | [abiword](https://bugs.launchpad.net/ubuntu/+source/abiword) | [libreoffice](https://bugs.launchpad.net/ubuntu/+source/libreoffice)
| spreadsheet | [gnumeric](https://bugs.launchpad.net/ubuntu/+source/gnumeric) | [libreoffice](https://bugs.launchpad.net/ubuntu/+source/libreoffice)

# How to write a good bug report

It is a common misconception that reporting bugs is an extremely difficult task, but as long as you clearly explain the problem, someone with more experience can guide you in getting any additional information. **New people reporting bugs are very strongly encouraged to read [How To Write Bugs Effectively](https://www.chiark.greenend.org.uk/~sgtatham/bugs.html) to help with wording their bug report.**

## Essential components

The more complete you can make your bug report, the more likely it is to be fixed. Here's the pieces you should consider essential:

 1. The report is filed against an appropriate package. See below.
 1. The report has a clear title.
 1. The report description includes the following pieces:
 	- Steps to reproduce (this is the most important thing; if it's not reproducible, it's nearly impossible to fix).
 	- Expected results.
 	- Actual results.
 	- Affected versions.
 	- Optionally, any other notes concerning conditions required to reproduce the bug, testing information, log files, etc.
 1. The report includes appropriate tags, but especially "lubuntu."

## General guidelines

- Ideally, it's good to do a little web search or ask around to see if your bug is really a support issue.
- One quick way to ensure you have a real bug is to set up a virtual machine with the version of Lubuntu you're using and see if you can repeat the behavior. If you can't, you might still have a bug, but the issue will be related to some specific aspect of your system, which will need to be tracked down.
- If you do have a bug, it's a good idea to do a search on Launchpad to see if you find a duplicate bug. If you do, work to add to and triage that bug report instead of reporting a new one.
- **MOST IMPORTANTLY: if you're not sure if you should report a bug, report it anyway!**

## Additional resources

- The Ubuntu wiki features a [page about reporting bugs](https://help.ubuntu.com/community/ReportingBugs).
- The Ubuntu QA Team publishes [general information](https://wiki.ubuntu.com/QATeam/Overview/#Bugs) on how bug reporting works and why it is so important, as well as how to write a proper bug report.
- We publish a [quick intro to using Launchpad with bugs](https://wiki.ubuntu.com/Lubuntu/ReportingBugs/Launchpad).
- The Ubuntu team made a nice, easy video walkthrough:
https://www.youtube.com/watch?v=27OhY83MsU8

---

# Triage: making bug reports better

An important part of QA is not only making bug reports, but making them in such a way that they can be worked on by developers. Additionally, triage should be something that QA considers part of their workload. Bug reports are there to help developers know what to work on next. The only way development happens is if these bug reports are clear and clearly marked.

The work here is making sure all of the essential components above are set up appropriately. Additionally, the following components are done:

1. The bug is reproduced by the triager and marked as confirmed.
1. An upstream bug report is created and links to the downstream bug and vice versa.
1. It is given a status of triaged.
1. It is given a reasonable priority.

Advice to these ends are provided by the [Ubuntu Bug Squad](https://wiki.ubuntu.com/BugSquad) team which has an open membership. Their [documentation](https://wiki.ubuntu.com/Bugs/Triage) is a valuable reference, but they are available by IRC and email for additional questions. Or you can contact the friendly Lubuntu Development/QA teams!

You will also need to contact the aforementioned folks to set statuses and priorities. Alternately, you can submit an application to the [Ubuntu Bug Control](https://wiki.ubuntu.com/UbuntuBugControl) team. The more well-equipped triagers we have on this team, the better, so please do so!

# What to triage

Of course, before you triage you need bugs to triage! Sometimes bugs are reported on the various communication channels or through tasks here, but more often than not they're not. They're otherwise invisible unless you go to a particular package on Launchpad and look at its bugs. Luckily, the Lubuntu Packages Team was created to collect all the bugs from the entire Lubuntu packageset. You can go to its [bug page](https://bugs.launchpad.net/~lubuntu-packaging) and sort through all the different bugs.

Do be aware that this covers the **entire supported** packageset, which means that until [April 2021](https://lubuntu.me/bionic-released/), both GTK (LXDE) and Qt (LXQt) versions of Lubuntu will be included, including all of the applications.

# Example

Here's an example of a complete, well-triaged bug report:

it has the following qualities:

1. It has been marked as confirmed.
1. It is linked to an upstream bug report. If you follow the link to the tracker, you'll find it links back to the downstream bug.
1. It is marked as triaged.
1. It is given a reasonable priority.
1. It has clear steps to reproduce, expected results, actual results, and any other additional notes detailing the version numbers and other conditions that apply and don't apply.
1. It has the Lubuntu Packages Team subscribed.
1. It's given appropriate tags, but especially the lubuntu one.

---

¹ Gitea (this site) has a bug tracker, but we use it only for tracking development tasks rather than collecting bug data.
² This is sent only through the Launchpad servers and should include no private information.
³ Alternately, you can manually create a report with `https://bugs.launchpad.net/ubuntu/+source/` //name_of_the_affected_package// `/+filebug`