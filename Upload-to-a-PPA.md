Purpose of this document
========================

As a supplement to the [Packaging Tutorial](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Tutorial), this is a great solution if you'd like people to test a change before you get it uploaded.

Requirements
============

 * `gpg` setup from [packaging requirements](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Requirements).
 * [Add your key to Launchpad](https://launchpad.net/~/+editsshkeys)
 * [Create your PPA](https://launchpad.net/~/+activate-ppa)

Procedure
=========

 1. Start in the folder containing your debian folder of whatever package you're working on
 1. Get the source:
    1. `uscan --download-current-version`
    1. `tar -x --strip-components=1 -f ../PACKAGE_*.orig.tar.xz`
 1. `dch -i` a new [[ changelog | Changelog ]] entry and make sure the version number ends with `ppa#` where `#` is some number. This will make the package essentially a higher version than those in the repos.
 1. Build the source: `debuild -S`
 1. Upload it to Launchpad: `dput ppa:`***your-launchpad-id***`/`***your-ppa-name***` ../PACKAGE_*source.changes`

You should immediately get an accepted message by email. Then it starts building. This can take a while. Be patient…