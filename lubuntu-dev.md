# Lubuntu Developers

- are members of the [~lubuntu-dev team in Launchpad](https://launchpad.net/~lubuntu-dev).
- are collectively responsible for the maintenance of packages in the Lubuntu package set.
- have a strong working knowledge of packaging concepts and techniques, refined through experience.
- have a strong working knowledge of Ubuntu and Lubuntu project procedures, especially those related to the release process and support commitments, and an understanding of the reasons why they exist.
- are able to apply this knowledge to the variety of packages and subsystems contained in the Lubuntu package set.
- have a history of substantial direct contributions to the distribution.
- take a leading role in new development projects to improve Lubuntu.
- exercise great care in their work, with the understanding that their efforts have a direct impact on others, including:
  - every Lubuntu user.
  - the Ubuntu Release Team.
  - corporate partners who provide support for Lubuntu.
- feel a sense of personal responsibility for the quality of Lubuntu releases and for the satisfaction of Lubuntu users.
- understand how Lubuntu integrates into the greater Ubuntu system and respects and concerns themselves with impacts of Lubuntu changes on the rest of the system.

## Prospective Lubuntu Developers

A well-qualified Lubuntu Developer should...
- have a good working relationship with existing Lubuntu Developers in the community.
- have the following references saved somewhere and can understand the rationale/purpose behind each:
  - [Proposed Migration guide](https://wiki.ubuntu.com/ProposedMigration)
  - [Build status page](http://qa.ubuntuwire.com/ftbfs/)
  - [Merge-o-Matic (MoM)](https://merges.ubuntu.com/)
  - [Stable Release Update guide](https://wiki.ubuntu.com/StableReleaseUpdates)
  - [The packageset list for each release (the packages Lubuntu Developers can upload to)](http://people.canonical.com/~ubuntu-archive/packagesets/)
  - [The Debian Free Software Guidelines (DFSG)](https://www.debian.org/social_contract.html#guidelines) - [helpful FAQ](https://people.debian.org/~bap/dfsg-faq.html)
- have read the most up-to-date version of the [Debian Policy Manual](https://www.debian.org/doc/debian-policy/).
- have [a working build environment](https://phab.lubuntu.me/w/packaging/packaging-requirements/) locally and can upload to PPAs without assistance.
- understand what an Ubuntu delta is, why some of the Lubuntu packages have deltas, and how/when to merge or sync a Lubuntu package.
- have a detailed understanding about how to...
  - update Standards-version and Debhelper to the latest version.
  - cherry-pick patches from upstream and work with quilt.
  - package new upstream releases and properly adjust the packaging after doing so.
  - compose new changelog entries, taking into account multiple entry authors, urgencies, and closing bugs in the changelog.
  - determine when a package is native or quilt, and can identify the key differences between the two.
  - work with bugs in Launchpad.
  - work with Git.
  - interact with upstream (Debian and LXQt/KDE/etc.) and file bugs.
- have at least a basic understanding of...
  - signing packages using debsign and generate diffs between two package versions using debdiff.
  - [working with symbols files](https://wiki.debian.org/UsingSymbolsFiles) and knowing the difference between optional symbols, arch-specific symbols, C++ symbols, and private symbols.
  - the differences between the supported Ubuntu architectures and what machines they are for.
  - working with autopkgtests and how to test autopkgtest changes locally as well as in a PPA.
  - the tools in the devscripts and the ubuntu-dev-tools packages.
- (optional) read [some of the questions asked](https://salsa.debian.org/nm-team/nm-templates) of a prospective Debian Developer and try to answer as many as you can as accurately as you can. You don't need to send the answers anywhere, but in the process of answering those questions, you will learn a lot of useful facts about development.

## Applying to be a Lubuntu Developer

To become a Lubuntu Developer, the existing Lubuntu Developers need to review your application. Here is what you need to do to apply:

- You MUST be a [Lubuntu Member](membership) first.
- Set up a personal wiki page under the `lubuntu-dev/Applications` subdirectory of this wiki. Please make use of the [template](lubuntu-dev/Applications/Template).
- Talk to your sponsors beforehand and ask them to add some information to the wiki page. In a regular application, you will have 3-5 sponsors.
- Once your application is ready, send an email indicating your readiness to apply and linking your wiki page to the [Lubuntu Developers mailing list](mailto:lubuntu-devel@lists.ubuntu.com). Your goal is to get quorum for the meeting (as defined below). To do this, either provide potential times to meet or something like a [Doodle poll](https://doodle.com/). Applications may be processed via email if necessary to get sufficient review.
- Attend the meeting.

All members of the Lubuntu community are welcome to attend and ask questions, add your feedback (even if unsolicited) to the wiki page in question, or ask questions on the [Lubuntu Developers mailing list](mailto:lubuntu-devel@lists.ubuntu.com).

The Lubuntu Developers will have prepared for the meeting (reviewed the application details, checked a few examples of your work, talked to sponsors, etc.) and ask questions to make sure the applicant qualifies for the team. During the meeting the Lubuntu Developers will cast their votes and if quorum is reached, will add the applicant to the team or ask them to reapply in due time. Quorum is defined as either the majority of the current Lubuntu Developers or three Lubuntu Developers, whichever is smaller.

## What's next?

So now you're a Lubuntu Developer. You may be asking yourself the question, "**What next?**" World domination? Not quite. You can work towards other levels of upload permission which, while not completely necessary, greatly benefit the community as a whole.

If you have a passion for helping with low-hanging fruit and community packages in Ubuntu, you might be interested in applying to be an [Ubuntu Master of the Universe (MOTU)](https://wiki.ubuntu.com/UbuntuDevelopers#MOTU). This is the most common next step from Lubuntu Developer, and allows you to upload to all community-supported packages in the Ubuntu archive. Since you're already a Lubuntu Developer, you have an understanding of packaging processes and procedures, and in order to become a MOTU, you need to prove that you can apply this knowledge to a wide variety of packages. You can do this by:
- helping with transitions.
- merging packages from Debian using MoM.
- fixing FTBFS packages using the build status page.
- subscribing to the [Ubuntu Developer mailing list](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel) and other Ubuntu mailing lists to get an understanding of current project developments.
- fixing bugs!

Please note that getting to MOTU can take a considerable amount of time, especially if the archive is frozen. Be patient; if you keep proposing good work, your sponsors will likely let you know when they believe you are ready to apply.

If you have a passion for helping out with the core infrastructure of Ubuntu and its core packages, you might be interested in applying to be an [Ubuntu Core Developer (core-dev)](https://wiki.ubuntu.com/UbuntuDevelopers#CoreDev). Please note that MOTU is a subset of core-dev, and you are highly encouraged to seek MOTU first. You can become a core-dev by:
- doing everything listed above for MOTU.
- proposing useful changes to core infrastructure such as the ISO build tooling ([livecd-rootfs](https://code.launchpad.net/livecd-rootfs), [ubuntu-cdimage](https://code.launchpad.net/ubuntu-cdimage)), [ubuntu-release-upgrader](https://code.launchpad.net/ubuntu-release-upgrader), etc.
- merging/syncing packages in Main.
- leading new, major projects which benefit the Ubuntu project as a whole.
- fixing bugs!

*The Lubuntu Council reserves the right to make adjustments to this process as needed. Please contact us if you need accommodations or if you have questions.*
