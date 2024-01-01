Purpose of this document
========================
The [Packaging Tutorial](https://phab.lubuntu.me/w/packaging/packagingtutorial/) assumes a normal package. If it's native (i.e. doesn't use patches), or if the upstream source isn't well tracked, or if the package isn't already in the Ubuntu repos, etc., things will break.

Packaging-only changes
======================
There's no need to use `quilt` if your change only affects the packaging and not the source code itself. For example, if you're going to change the `debian/rules` file, you can just make the change and update the [[ changelog | Changelog ]]. In that specific example, though, since you are essentially changing the build instructions, you'll still want to do a test build.

Native
======
Check out [DEFAULTSETTINGS](https://git.lubuntu.me/Lubuntu/lubuntu-default-settings) and you'll find that in addition to the normal `debian` folder, there's also other files. Most notably there is a `src` folder which contains the code. This should be a clear sign that something is different, as Debian packages are nothing more than metadata that is applied to upstream source code. In this case, we do not use `uscan` to grab the source, nor `quilt` to manage patches, but just apply the changes to the code in the `src` folder and then proceed as normal.

Not a package
=============
A [[ changelog | Changelog ]] entry is a requirement of every Debian package, but sometimes we're not working on packages. rSEED is a great example of this. No changelog to be found. No debian folder, even. This is because this isn't used to build a package that people install. It's used to build Lubuntu itself! You'll notice if you click **`Clone`** that it's not on gitea, but on Launchpad. This will mean ~~`arc`~~ will be useless both for submitting commits, but also for merging them.

Can't find source
=================
TODO

Not in git.lubuntu.me
===========
Or how to do a Merge Proposal on Launchpad.
TODO

~~Update an existing Differential revision~~
========================================
~~or `arc patch`ing a fresh `git clone` to in turn `arc diff`
TODO~~