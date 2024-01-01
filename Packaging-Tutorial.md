This is a tutorial which hopes to make it easy for new contributors to figure out how to fix a bug in Lubuntu. Note that this is specific to repositories that Lubuntu hosts on Phabricator, i.e. those components that differentiate Lubuntu from other Ubuntu flavors— most notably, LXQt. Everything else is handled upstream in Ubuntu. The process there will be similar.

Packaging is a vast and complex subject, especially given the many upstreams (Ubuntu, Debian, the developer themselves) and the changing processes/requirements among them. We have our [own guide](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Guide) that proves some links to further resources.

Long story short
================

🚨**WARNING**🚨 This is a high-level overview that is useful as a reference once you understand the process. **If you are new, DO NOT just follow this but read the links below first**.

⚠️**NOTE**⚠️ Anything in CAPS is to be considered a variable and not to be taken literally. 

Some important variables:
 1. **PACKAGE**: name of the source package, e.g. calamares
 1. **VERSION**: version string of the package, e.g. 3.2.11-0ubuntu1
 1. **CODENAME**: adjective in the full codename, e.g. eoan

📣**IMPORTANT**📣 You ***must*** be using the current development version for the build process below to work.

📣**IMPORTANT**📣 You ***must*** use the ssh clone link or pushing your changes will not work. DO NOT USE THE http LINK!!!!

```lang=sh
## make a place to contain your work
mkdir WORKDIR
cd WORKDIR

## get the packaging repository from gitea
git clone git@git.lubuntu.me:Lubuntu/PACKAGE.git
cd PACKAGE

## make sure you're on the development branch
git checkout ubuntu/CODENAME

## get the upstream source code
uscan --download-current-version
tar -x --strip-components=1 -f ../PACKAGE_*.orig.tar.xz

## make a new patch
mkdir debian/patches # just in case it doesn't exist
quilt push -a  # just in case there are patches, we apply them all
quilt new NAME.patch
# this is where you actually make the changes you want
quilt edit PATH/TO/FILE 
quilt refresh
quilt header --dep3 -e

## update the changelog
dch # -i or -a, depending (see below)
dch -r --distribution CODENAME

## test build the package
sudo apt update; sudo apt build-dep PACKAGE -y
debuild -b --no-sign

## get rid of source
rm -rf !(debian) .pc/ # requires bash and `shopt -s extglob`

## push your changes
git add -A
git commit -m "SOME MEANINGFUL MESSAGE."
git push

## finally a sponsor (usually same as developer) uploads your revision
# get a new working copy or working with the above…
# build the source package
debuild -S -d -sa

# upload!
dput ubuntu ../PACKAGE_VERSION_source.changes

## after it is accepted into the archive, a developer will tag it
git tag ubuntu/VERSION
git push origin ubuntu/VERSION
## remenber the VERSION here should be the package version that you put in changelog. not focal or eoan or something like that.

```
⚠️**NOTE**⚠️: always 👏 add 👏 a 👏 [[ changelog | Changelog ]] 👏 entry 👏 🤣

Digging deeper
==============

📣**IMPORTANT**📣 You must complete the [packaging requirements](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Requirements) if you want the above to work (don't skip this!)

📣**IMPORTANT**📣 The following is **required reading** if you want the above to make sense

 * [Exceptions](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Exceptions)
 * [Version numbering](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Versions)
 * [Real world packaging example](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Example)

Bonus points
============

 * [Packaging guide](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Guide) provides information on standards and policies
 * [Upload to a PPA to test your packages before release](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Upload-to-a-PPA)
 * ~~[Leverage CI for testing](https://phab.lubuntu.me/w/packaging/ci/) as an alternative to PPAs~~
 * [Packages](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packages) discusses where to find packages, their various states, how to get them in the archives, etc.