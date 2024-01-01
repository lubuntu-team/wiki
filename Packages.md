# Where is my package?

If you're not finding a package in the archives, it may be because it's stuck in the queue, which can be found at https://launchpad.net/ubuntu/CODENAME/+queue. Here are definitions for the various statuses:

 - **New:** brand new packages that have never been in the repositories waiting on review.
 - **Unapproved:** new changes to old packages waiting on review.
 - **Rejected:** these were for some reason or another rejected (sometimes it's because a new upload supersedes the first one).
 - **Accepted:** the package is no longer stuck in the queue, but it is not published yet.
 - **Done:** the package is published.

Note that different teams review different queues, and while there are some team members which overlap, different teams are responsible for different reviews.

**New** queue reviews are the responsibility of the Ubuntu Package Archive Administrators Team, or Archive Admins for short. You can find the member list [here](https://launchpad.net/~ubuntu-archive/+members).

**Unapproved** queue reviews for the **development release** is done by the Ubuntu Release Team. They also handle migration from `devel-proposed` to `devel[-release]`, and are the go-to contact for dealing with migration. You can find the member list [here](https://launchpad.net/~ubuntu-release/+members).

**Unapproved** queue reviews for **stable releases** are done by the Ubuntu Stable Release Updates Team, or SRU Team for short. They are responsible for landing updates as laid out in [the documentation](https://wiki.ubuntu.com/StableReleaseUpdates). You can find the member list [here](https://launchpad.net/~ubuntu-sru/+members).

You can find the majority of the people in these teams in #ubuntu-release on libera.chat IRC, and you are thus encouraged to ask there.

The easiest way to the package is to go to https://duckduckgo.com/?q=!upkg+SOURCE-PACKAGE-NAME.

# Package hunting: how to get from upload to distribution

The first step in getting a package uploaded is finding who can upload to the package. This requires an understanding of the archive sections of Ubuntu and ways of getting upload access.

Here are the sections of Ubuntu and what they mean:

 - **Main:** These packages are a core part of Ubuntu, either as part of the foundation or the GNOME desktop as provided in main Ubuntu. Canonical Ltd. as a company commits to provide support for all of these packages for the full length of the support cycle, including security updates and review from the Ubuntu Security Team. **Be careful when touching these packages, because you can break more than just Lubuntu when publishing updates to these.**
 - **Restricted:** These are proprietary drivers such as the NVIDIA drivers which are non-free but can be distributed. It is very rare that you should have to touch any of these packages, and these usually come directly from the distributor.
 - **Universe:** All free software that is not in Main. The majority of the software here flows down from Debian with little to no changes. All flavors have packages in this section, and it is by far the most populated section in Ubuntu.
 - **Multiverse:** Anything which could be in Universe but has non-free or "grey area" software which can be distributed but not always easily modified. An example of a package in here is the Microsoft fonts, which need to be downloaded from Microsoft and a license needs to be accepted prior to installing them.

The two main uploading teams in Ubuntu are [Ubuntu Core Developers](https://wiki.ubuntu.com/UbuntuDevelopers#Ubuntu_Core_Developers) and [Ubuntu Masters of the Universe (MOTU)](https://wiki.ubuntu.com/UbuntuDevelopers#MOTU). The latter is a subteam of the former. Ubuntu Core Developers have upload access to many code repositories that are core parts of Ubuntu, and have upload access to all four sections of Ubuntu. However, MOTUs are limited in that they only have upload access to Universe and Multiverse. You can additionally request upload access, or [Per Package Upload (PPU)](https://wiki.ubuntu.com/UbuntuDevelopers#Per-package_Uploaders) permissions to specific packages, but this is done less frequently than joining one of the above teams.

For Lubuntu packages, you need to find someone with MOTU permissions or higher. When in doubt, it could be helpful to use the `ubuntu-upload-permission` tool from the `ubuntu-dev-tools` package to see who can upload to a given package.

If your changes are committed in Git, the uploader simply runs `debuild -S -d [-sa]` to get a collection of files, much like the PPA instructions below. Once they are satisfied with the upload, they run `dput ubuntu ../PACKAGE_*source.changes` which uploads the package to Ubuntu. At this point, one of two things could happen.

If the upload is to a stable release, it appears in the Unapproved queue for the release you are uploading to. The bug report which should have been mentioned in the [[ changelog | Changelog ]] will then get either rejection or acceptance feedback from the SRU Team member processing the package. If the package is accepted, it gets accepted into the CODENAME-proposed pocket for testing. The package then needs to be [verified](https://wiki.ubuntu.com/StableReleaseUpdates#Verification), and if it works, after seven days (unless an exception is made), the package is released into `CODENAME-updates` for general consumption and phased in over a period of two days, assuming no apport reports are submitted that are interpreted as regressions (if this is the case, it is wound back to 0%). If the verification is failed or the package is rejected, it is removed.

[Pending (unverified) SRUs can be found here.](https://people.canonical.com/~ubuntu-archive/pending-sru.html)

[The phased updates for packages can be found here.](https://people.canonical.com/~ubuntu-archive/phased-updates.html)

Otherwise, the upload is for the development release. If there is no hard freeze in effect, an email will be sent from "Ubuntu Installer" to the uploader confirming the upload, and another copy is sent to the CODENAME-changes mailing list at lists.ubuntu.com, in the format of https://lists.ubuntu.com/CODENAME-changes. It will then go through [automated regression testing](https://wiki.ubuntu.com/ProposedMigration), which includes testing the packages and its reverse dependencies for autopkgtest regressions, testing if it is installable in the release pocket, and if there are any blocking bugs against it. If all checks pass (or the Release Team overrides), the package is then moved to `devel-release` (which is an invisible pocket pointing at `devel`) and an email is sent to the uploader from "Ubuntu Installer" confirming that it has migrated.

TODO: explain pockets.

TODO: explain how to view this all visually at Launchpad (just found from `!upkg PACKAGE` but blunt pointers might be nice).

TODO: explain the Archive Admin's role in moving packages to/from components, why some binaries are in Universe while the sources are in Main, and how to tell what's published where that doesn't involve manually grepping files from archive.ubuntu.com (Launchpad).