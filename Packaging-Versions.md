Purpose of this document
========================

This is meant to supplement the [Packaging Tutorial](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Tutorial) to provide answers about choosing the right version number.

Format
======

 * Version number is in the format ***upstream_version***-***debian_patch_number***ubuntu***ubuntu_patch_number***.      
 * You will generally be incrementing *ubuntu_patch_number*.
 *…unless it's a native package, in which case, there is only a simple version number.

Pre-check
=========

 * Before deciding on the version number to use, check a few things:
   * `git pull` or just check the repo to see if there have been additional changes while you've been working on your local copy. If there have been changes, there's likely an updated `debian/changelog` entry that you'll want to append ( `dch -a`).
   * ~~Check to see if your repo contains any pending changes. This should be shown by browsing in the repo to the file(s) in question or you can just look at [all pending revisions](https://phab.lubuntu.me/differential/query/active/). If there are any, you might want to check in on the status, as you can potentially get your changes rolled in.~~
   * Check Launchpad for what's in the archives. The best way to do this is to use  `!upkg` ***your_source_package*** in DuckDuckGo. Also see [Packages](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packages).

Final decision
==============
 * Read the [[ changelog | Changelog ]] wiki.
 * If the final entry in `debian/changelog` is equal to the "release" version, increment ( `dch -i`).
 * If the final entry in `debian/changelog` is greater than the "release" version, append ( `dch -a`).
 * If there's something in "proposed," you'll probably want to increment, but check in and see if your change can't be rolled in.

⚠️**NOTE**⚠️ **The minimum version number for a package in Ubuntu is upstream_version-0ubuntu1.** 
The minimum version number for a package in Debian is upstream_version-1. In neither should the patch number be zero since the packaging itself constitutes a change to the upstream version.
