Lubuntu's packaging follows a specific set of standards to ensure consistency and cleanliness.

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", 
"SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this 
document are to be interpreted as described in RFC 2119.

If a policy is not described here, packaging must use the standards set by the version of [Debian Policy](https://www.debian.org/doc/debian-policy/) specified in the `Standards-version` line of a packages `debian/control` file.

Patches
=======

.quiltrc
--------

A packager's `~/.quiltrc` must contain the following lines.

```
for where in ./ ../ ../../ ../../../ ../../../../ ../../../../../; do
    if [ -e ${where}debian/rules -a -d ${where}debian/patches ]; then
        export QUILT_PATCHES=debian/patches
        break
    fi
done
QUILT_PUSH_ARGS="--color=auto"
QUILT_DIFF_ARGS="--no-timestamps --no-index -p ab --color=auto"
QUILT_REFRESH_ARGS="--no-timestamps --no-index -p ab"
QUILT_DIFF_OPTS='-p'
```

Patch style
-----------

 * All patches must be completely [DEP-3](https://dep-team.pages.debian.net/deps/dep3) compliant and all information should be accurate. No other information should be in the patch header besides DEP-3 headers.
 * After adding a new patch, `quilt push` (to get to the patch) and `quilt refresh` must be ran to ensure it applies cleanly and style formatting is solved.
 * All files in `debian/patches/` must be listed in `debian/patches/series` with the exception of the series file itself. When removing a file from `debian/patches/series`, it must be removed from the directory.
 * Patches should have a suffix of `.patch`.
 * Multiple upstream commits should be separated into multiple files, and must have a common suffix or prefix.

General formatting
==================

wrap-and-sort
-------------

The command `wrap-and-sort` must be ran before committing any changes to a file in `debian/` besides `control` and `patches/*`. No flags to `wrap-and-sort` should be used.

Debian policy compliance
========================

For uploads targeting the development release, `Standards-version` in `debian/control` should be updated to [the latest policy version](https://www.debian.org/doc/debian-policy/). If there is a reason not to, it should be discussed among developers and noted here.

Copyright compliance
====================

On new upstream releases, the whole diff must be checked and `debian/copyright` must be updated for the copyright notice changes. This is to ensure compliance with the [DFSG](https://www.debian.org/social_contract#guidelines) which must be followed in all Lubuntu packages.

A tool such as `licensecheck` may be used, but is manageable enough to do by hand if the diff is small.

Where the only changes made are our packaging changes, it's optional to add a copyright for `debian/*` as per license guidance below, but it is not a requirement.

[[ changelog | Changelog ]] entries
=================

There must be no trailing whitespace in the `debian/changelog` file. See [here](https://vim.fandom.com/wiki/Remove_unwanted_spaces) for tips on how to do remove them in `vim` or you can do it with `sed -i 's/[ \t]\+$//'`

When referencing Launchpad bugs, the following (case-insensitive) regex must be followed: `lp:\s+\#\d+(?:,\s*\#\d+)*`

VCS
===

Use of Git
----------

All Lubuntu packaging must be kept in Git. If an archive upload is 
done without committing to Git, as soon as this is noticed, it must be 
committed to the corresponding packaging repository.

Commits must be self-contained
------------------------------

Only one notable change must be done in each commit. It should contain a [[ changelog | Changelog ]] entry, except if it is small enough.

Commit messages
---------------

If the [[ changelog | Changelog ]] entry added in the commit contains a Launchpad bug reference, it must be in the commit message.

Commit messages should closely match the [[ changelog | Changelog ]] entry if there is 
one. The short commit message should be kept to 72 characters or less.

Uploads must be tagged
----------------------

For every upload done to the Ubuntu archive, **only once the upload is accepted**, the release commit must be tagged with `ubuntu/VERSION` where `VERSION` is the full Ubuntu version, e.g. `0.14.2-3ubuntu1`. In the case of epochs, use `%` instead of `:`, e.g. `1%19.10.3`.

Branch format
-------------

For packaging which we only ever expect one archive version to be used, `master` must be used. In all other cases, the `ubuntu/RELEASE` versioning scheme must be used. (For example, `ubuntu/bionic`.)

Vcs-* in debian/control
-----------------------

For packages we maintain our own packaging for but are also in Debian, the following format must be used in the `debian/control` file for the package's VCS entries:

```
Vcs-Browser: https:/git.lubuntu.me/Lubuntu/lxqt-about-packaging
Vcs-Git: https://git.lubuntu.me/Lubuntu/lxqt-about-packaging.git
XS-Debian-Vcs-Browser: https://salsa.debian.org/lxqt-team/lxqt-about
XS-Debian-Vcs-Git: https://salsa.debian.org/lxqt-team/lxqt-about.git
```

XS-Debian-* are where to find the repositories in Debian, and Vcs-* should link to the repositories in gitea.

Licensing
=========

The default license for new code should be [GPL3](https://www.gnu.org/licenses/gpl-3.0.en.html).

Example:

```
# Copyright © 2021 Lubuntu Developers
# Author: Walter Lapchynski <wxl@ubuntu.com>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <https://www.gnu.org/licenses/>.
```


