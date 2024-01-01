Umm so yeah, we have a new upstream version. Usually [merges.ubuntu.com](https://merges.ubuntu.com) should merge it automatically. But it's a stupid robot that gets scared of single line translation changes. so we need to deal with them ourselves.

Here are the steps:

  1. Follow [[ packaging/packaging-requirements | packaging-requirements ]]
  1. `sudo apt install ubuntu-dev-tools meld yaru-theme-gtk yaru-theme-icon kdiff`
  1. `mkdir work && cd work`
  1. `grab-merge lxqt-qtplugin`    //replace this with package name. 

This basically grabs whole merge from merges.ubuntu.com and gives you a report saying where it is failing to merge. A directory with package name will be created. it will have a REPORT, orig.tars of new version and of version currently in archives, the debian source and also patches which it try to apply. we only need to focus on REPORT. There is also a folder in which we are supposed to work and fix the merge. `cd` into it.

  1. `cd ~/work/lxqt-themes/lxqt-themes-0.16.0-1ubuntu1/`
  1. `cat ../REPORT`

Read the report and you will notice a conflicts section which has files listed with `C` or `C*` infront of them. Those files marked with 'C ' contain diff3 conflict markers, which can be resolved using the text editor of your choice.  Those marked with 'C*' could not be merged that way, so you will find .UBUNTU and .DEBIAN files instead and should chose one of them or a combination of both, moving it to the real filename and deleting the other.

MoM gives you a start on the changelog. It should look something like this:
```
screengrab (2.1.0-1ubuntu1) UNRELEASED; urgency=low

  * Merge from Debian unstable. Remaining changes:
    - SUMMARISE HERE

 -- Ubuntu Merge-o-Matic <mom@ubuntu.com>  Thu, 07 Jan 2021 15:55:46 +0000
```
Some things to note about the changelog above:
  1. The urgency should be changed to `urgency=medium` low isn't really used in Ubuntu
  1. The Merge line should remain and any changes you make above what the merge has should be listed (e.g. if you bump standards-version or debhelper version)
  1. At the end when you do a `dch -r ""` the name, email, date, and release should all get updated. Double check with a `less debian/changelog` or substitute whatever pager you use.

Of all the conflicting files, only focus on files under `debian/` Fix them using nano as follows.
  1. `nano debian/control`
After all the conflicting files under debian are fixed, cd into your main work directory and clone the repo of package from phab.
  1. `cd ~/work && mkdir phab && cd phab`
  1. `git clone ssh://git@phab.lubuntu.me/source/lxqt-themes.git && cd lxqt-themes`
Now just copy all the ***changed and newly added files*** from the fixed debian folder of the merge into the phab clone using meld or kdiff. (or any command line tool that suits you)
  1. `meld ~/work/lxqt-themes/lxqt-themes-0.16.0-1ubuntu1/debian/ ~/work/phab/lxqt-themes/debian`
After copying the changed and newly added files. close meld and edit the debian changelog.
  1. `dch -e`                                                   //assuming you are in same directory as earlier i.e ~/work/phab/lxqt-themes/
After that just follow [[ packaging/packaging-example | packaging-example ]]
uscan, untar, debuild -b, arc diff in that order.


also, small advice: 
Try to check changes in a ppa before uploading to archives. sometimes stuff breaks in s390x architectures and you need tp fix it on top of this merge manually. You can definetly upload to archive and wait for it to throw the error but ppa builds are faster and you will be able to identify and fix problems faster. later just upload to archive once successful in ppa. that way you don't have to dread the build failed mail from archives later on.