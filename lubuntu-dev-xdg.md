This is a technical document detailing exactly how Lubuntu does XDG settings, some problems we have faced, and anything else worth mentioning.

## How we get our settings

Here's a step-by-step on what pulls from what:

 1. SDDM pulls the session name from `/usr/share/xsessions` when logging in. In our case, it's `Lubuntu.desktop`. Therefore, the `DESKTOP_SESSION` environment variable is set to `Lubuntu`, from this filename. Please note that [we had to patch SDDM](https://git.launchpad.net/~kubuntu-packagers/kubuntu-packaging/+git/sddm/tree/debian/patches/fix-desktop-session-env-var.patch?h=kubuntu_cosmic_archive) to do this properly; it used to make `DESKTOP_SESSION` an absolute path, which, when we continue in these steps, breaks things. TODO: send this upstream. 
 1. xorg sets the `XDG_CONFIG_DIRS` environment variable to `/etc/xdg/xdg-DESKTOP_SESSION` and `/etc/xdg` and `XDG_DATA_DIRS` to `/usr/share/DESKTOP-SESSION` and `usr/share` at minimum. NOTE: this is [an Ubuntu-specific patch in xorg](https://salsa.debian.org/xorg-team/xorg/blob/ubuntu/debian/local/Xsession.d/60x11-common_xdg_path). 
 1. [`startlxqt`](https://github.com/lxqt/lxqt-session/blob/master/startlxqt.in) then grabs the values of `XDG_CONFIG_DIRS` and `XDG_DATA_DIRS` to use in the call to `startlxqt`, which then does a one-time copy of the settings from the first entry in both.

## Problems we have faced and things to not touch

### Black screen in Lubuntu Next 18.04 on starting the live session

For a while before we could figure it out, the Lubuntu Next 18.04 image had a black screen on the live CD and on bootup of a new Lubuntu Next system. The LXQt system had been logged in, but nothing was visible. This is why we had to patch SDDM, because the value of `XDG_CONFIG_DIRS` didn't have our valid XDG path; it was an absolute path put onto `/etc/xdg/xdg-`. So therefore, if the situation ever comes up again, it means that `XDG_CONFIG_DIRS` can't find valid settings. This also caused Simon to confront upstream; they had moved the default settings to `/usr/share` from `/etc/xdg` because they believed that it would apparently make it easier for distributors. Not only did they not consider that `/usr/share` is not in [the XDG spec](https://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html#variables), they did no verification in LXQt itself to ensure that `/usr/share` at minimum is always there. When Simon submitted a patch, it was rejected on the grounds that it was too distro-specific, which was ironic because they didn't follow the XDG spec. Alf has since reconsidered and asked Simon to resubmit the patch.

### Be careful when changing the session .desktop file name

If you rename `/usr/share/xsessions/Lubuntu.desktop` to something else, please do change `/etc/xdg/xdg-Lubuntu/` to the same name. Otherwise none of our settings will be applied.
