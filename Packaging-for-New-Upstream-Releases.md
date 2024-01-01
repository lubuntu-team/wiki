This is meant to supplement the [Packaging Guide](https://phab.lubuntu.me/w/packaging/packaging-guide/).

The scenario is this: Upstream has released a new version for a package that we host in gitea. We want to update that package. The following are some "notes" to briefly document that.



1. Make sure your development environment is setup according to the [packaging requirements](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Requirements)
1. Clone the repository from gitea
1. Check the branch is the proper branch to be on `git branch`
1. Create a [[ changelog | Changelog ]] entry bumping the version to match the upstream release. See [versioning](https://phab.lubuntu.me/w/packaging/packaging-versions/) for more information. `dch -i`
1. Commit the change eg `git commit -m "Bump version for new upstream release"`
1. Download the new tarball from upstream `uscan --download-current-version`
1. Do a copyright update.  ***Note** This involves manually scanning the diff between the version the package previously in the archive and this new version, keeping track of any and all copyright notice changes and updating debian/copyright. This is tedious, and you have to do it manually.*
1. Make a [[ changelog | Changelog ]] entry e.g. `dch -a`
1. Commit the change eg `git commit -m "Update copyright file"`
1. Make sure debhelper and Standards-version are at the latest versions. If they aren't, bump and read the upgrade notes. Again refer to the [guide](https://phab.lubuntu.me/w/packaging/packaging-guide/)
1. Make a [[ changelog | Changelog ]] entry e.g. `dch -a`
1. Commit the change eg `git commit -m "Bump standards-version"`
1.  Read the release notes and read them thoroughly. This is where upstream will usually(!) put anything else you have to adjust for as far as patches. 
1. If you added or removed patches... Make a [[ changelog | Changelog ]] entry e.g. `dch -a`
1. If you made any... Commit the change e.g. `git commit -m "Removed patch applied in upstream code"`
1. Analyze the build dependencies, and bump everything in the LXQt stack to the latest version. Commit your change.
1. Do a local build with sbuild, making sure you have the -EvIL +pedantic flags set in your `sbuildrc` file. For more information on sbuild go [here](https://wiki.ubuntu.com/SimpleSbuild) or [here](https://wiki.debian.org/sbuild)
1. Based on the results of your build, you may need to make adjustments to patches or any files you touched. Make sure the build is lintian clean. **[[ changelog | Changelog ]] entry and commit for every set of changes.**
1. Run wrap-and-sort. The [guide](https://phab.lubuntu.me/w/packaging/packaging-guide/) has a section for more info.
1. Make a [[ changelog | Changelog ]] entry e.g. `dch -a`
1. Commit the change e.g. `git commit -m "Run wrap-and-sort"`
1. Push your commits (`arc diff` or if to CI `git push` **this depends check with a developer**)