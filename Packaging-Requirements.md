Purpose of this document
========================

This is meant to provide all the requirements necessary to follow the [Packaging Tutorial](https://git.lubuntu.me/lubuntu-wiki/wiki/wiki/Packaging-Tutorial).

Requirements
============

 1. Software
    1. `sudo apt install ssh git devscripts debhelper tar quilt` 
 1. Configuration
    1. Uncomment the `deb-src` lines in `/etc/apt/sources.list` so `apt build-dep` works correctly. They should be duplicates of the normal `deb` lines except they begin with `deb-src`. With newer versions using [deb822 sources](https://discourse.ubuntu.com/t/spec-apt-deb822-sources-by-default/29333), just add `deb-src` to the `Types` line. 
    1. So you get credit where credit's due:
       1. For `git`:
          1. `git config --global user.name "`***your full name***`"`
          1. `git config --global user.email "`***your email address***`"`
       1. For Debian tools:
          1. Add the following to `$HOME/.bashrc`:
             1. `export DEBFULLNAME="`***your full name***`"`
             1. `export DEBEMAIL="`***your email address***`"`
             1. `export EMAIL="`***your email address***`"`
          1. Reload your configuration for it to take effect immediately: `source $HOME/.bashrc`
 1. Set up `ssh`:
    1. Create a key
       1. Easy way
          1. `ssh-keygen`
          1. Accept the default name (`$HOME/.ssh/id_rsa`)
          1. Enter a password ≥ 5 characters
       1. Hard way
          1. `ssh-keygen -C some-identifying-info -t ed25519 # more secure and supported by Launchpad; alternately use -t rsa -b 4096`
          1. Select  a unique name e.g. `$HOME/.ssh/gitea # allows you to have more than one key`
          1. Pick an even better password!
          1. Edit `$HOME/.ssh/config` to include
             1. `Host git.lubuntu.me`
             1. `  IdentityFile ~/.ssh/gitea`
    1. Add `ssh` key to Gitea:
       1. Go to [Settings](https://git.lubuntu.me/user/settings)
       1. Click on "SSH/GPG Keys"
       1. Click on "Add Key" just above the "Manage SSH Keys" section
       1. Give your key a name (anything works) and then copy and paste the **//__public__//** key from the step above
       1. Click on "Add Key" below the "Content" section where you added your key
 1. `$HOME/.quiltrc` from [packaging guide](https://phab.lubuntu.me/w/packaging/packaging-guide)

Extras
======

 1. `gpg` setup
    1. Get the software: `sudo apt install gpg`
    1. Make a new key: `gpg --full-generate-key`
    1. Select an RSA and RSA pair
    1. Select 4096 bits for key size
    1. Select expiration date, or none (note you can always move the date out farther)
    1. Verify and accept
    1. Enter your real name
    1. Enter your email address
    1. A comment is not necessary
    1. Give it a good password
    1. It takes a while to gain enough entropy to finish the creation. Open a new terminal and `find / 2>/dev/null` and that should help it along
    1. Add `DEBSIGN_KEYID=`***your-key-id*** to  `~/.devscripts`. ***your-key-id*** should be equivalent to `gpg --list-keys --with-colons` ***your-email-above*** `| grep -m 1 fpr | awk -F: '{print $10}'`
 1. `bzr` setup
    1. Get the software: `sudo apt install bzr`
    1. Create a [Launchpad account](https://launchpad.net/+login) if you don't have one already.
    1. Create an `ssh` key or reuse one (see above), ed25519 is now supported for Launchpad.
    1. [Upload your key](https://launchpad.net/~/+editsshkeys) to Launchpad.
    1. Set your identification: `bzr whoami "`***Your Name <your@emailaddress.org>***`"`
    1. Login to Launchpad: `bzr launchpad-login `***your-launchpad-username***
    1. Edit `$HOME/.ssh/config` to include
       1. `Host bazaar.launchpad.net git.launchpad.net`
       1. `  User `***your-launchpad-username***
    1. Add `  IdentityFile /path/to/ssh/key` if you use a non-default key.
 1. `ssh` agent with `keychain`
    1. Get the software: `sudo apt install keychain`
    1. Added the following to the end of your `$HOME/.bashrc`:
       * `keychain `***path-to-private-ssh-key-1 path-to-private-key-2 … path-to-private-key-n***
       * ```. ~/.keychain/`uname -n`-sh```
    1. Every time you login, you will be asked for all of your passwords and then they will be held in memory.
