Purpose of this document
========================

This is meant to supplement the [Packaging Tutorial](https://phab.lubuntu.me/w/packaging/packagingtutorial/).

Background
==========

We were having some trouble setting the default GTK theme only to discover that upstream had created [a patch](https://github.com/lxqt/lxqt-config/pull/278/commits/10945b90c8d9a084977675bc8b1db158acd4c909#diff-b37764f38e63f6ed1fa485106bf34ccaR294) that could help us out. We only package stable released versions, so we couldn't just repackage it with the new `master` in `git`. Instead, we wanted to patch our released version with this change.

Get the upstream changes
========================

So first we needed to pull down the upstream repository. Clicking on the repo got us to the main page.

At that point, we clicked the **`Clone`** or **`Download`** button and copied the clone link. Then we opened up a terminal and cloned the repo:

```
git clone https://github.com/lxqt/lxqt-config.git
```

Now we needed to make a patch. So we ran `git log`, which opens in a pager, like `less`. You should be able to use this to  search by typing `/` followed by some search terms, and then hitting {key ENTER}. So we did a search for "Set the default GTK theme" and found it at commit 4c3ad403dc14dde4fe41e56cf3272ac11e30346f. To make our patch we remember that `git` has a shortcut for "previous commit." Using that knowledge we did the following, creating a reasonably-named patch, and putting it in `$HOME` to keep it out of the way of everything else:

```
git diff 4c3ad403dc14dde4fe41e56cf3272ac11e30346f 4c3ad403dc14dde4fe41e56cf3272ac11e30346f^ > ~/set-default-gtk-theme.patch
```

Apply the patch
===============

So now we needed to get our repo. We could search for "lxqt-config" in the search box here and we will eventually find rLXQTCONFIGPACKAGING. Once there, we can clone our repo, by clicking on the {nav Clone} button. With that now we can go back to our terminal and clone the repo:

```
git clone ssh://git@phab.lubuntu.me:2222/source/lxqt-config.git
```

Then we checked out the development branch:

```
git checkout ubuntu/cosmic
```

Then we grabbed the source:

```
uscan --download-current-version
tar -x --strip-components=1 -f ../lxqt-config_0.13.0.orig.tar.xz
```

Seeing that we already had patches in `debian/patches` we proceeded to apply them:

```
quilt push -a
```

And then we imported our patch:

```
quilt import ~/set-default-gtk-theme.patch
```

After import, we performed a required `quilt push`. This is the step that actually applied the patch to the source. Sometimes these don't apply cleanly and some editing is required, but in this case, we had no problems.

Just for safety's safe, we did a `quilt refresh` and then used `quilt header --dep3 -e` to edit the header:

```
Description: Set default GTK theme if rc file doesn't exists.
Author: P.L. Lucas <selairi@gmail.com>
Applied-Upstream: https://github.com/lxqt/lxqt-config/commit/4c3ad403dc14dde4fe41e56cf3272ac11e30346f
```

Finish it up
============

We added a new [[ changelog | Changelog ]] entry with `dch -i`, incrementing the version number:

```
lxqt-config (0.13.0-0ubuntu5) cosmic; urgency=medium

  * Set default GTK theme if rc file doesn't exists. 

 -- Hans P. Möller <hmoller@gmail.com>  Thu, 04 Oct 2018 14:44:03 -0300
```

Then we built it to ensure there were no issues:

```
sudo apt update && sudo apt build-dep lxqt-config
debuild -b --no-sign
```

Next, we got rid of the source and remnants of quilt so the repo was back into a normal state.

```
rm -rf !(debian) .pc/
```

And finally, we put it up for review:

```
git add -A
arc diff
```

We gave it the commit message:

> Set default GTK theme if rc file doesn't exists.

And filled out the template for the differential revision review:

> Summary: Set default GTK theme if rc file doesn't exists.
> 
> Test Plan: See if default GTK theme is according to 'gsettings get org.gnome.desktop.interface gtk-theme'
> 
> Reviewers: @tsimonq2, @wxl
> 
> Subscribers:

And that gave us the URL of the differential revision:

https://phab.lubuntu.me/D27

And that point, it was reviewed and changes were requested. We made those changes, using `git add` and `git rm` on files where appropriate, and then `arc diff`ing again.

Finally, our revision was accepted and finally [landed into our repositories](https://phab.lubuntu.me/rLXQTCONFIGPACKAGING3acc96e087976f22e999f6f2d8af8d43d6540343), which in turn [synced with the Ubuntu repos](https://launchpad.net/ubuntu/+source/lxqt-config/0.13.0-0ubuntu5).

---

NOTE: due to the fact that our original Phabricator instance from which this came from died, the differential revision URL is no longer valid.

Further Note: Some of this page is out of date now that we have moved to gitea.