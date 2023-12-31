This document seeks to serve as a central repository for information regarding debugging, i.e. to see what's going on under the hood of various programs.

# lxqt-session

There's a log file at `$HOME/.config/lxqt/debug.log` that will populate with information using [`QLoggingCategory`](https://doc.qt.io/qt-5/qloggingcategory.html).

There's a few ways to turn this logging on, but the easiest way is to add the following before `exec lxqt-session` in `/usr/bin/startlxqt`: 

```lang=sh
export QT_LOGGING_RULES="*.debug=false;lxqt-session.debug=true"
```

which turns off all debugging except for those messages with the lxqt-session category.

# lxqt-globalkeysd

The log level can be controlled from command line options. The following will print all types of messages to /var/log/syslog:

```lang=sh
lxqt-globalkeysd --use-syslog --log-level=debug
```

You can choose different levels (see `lxqt-globalkeysd --help`) and you can eschew the syslog switch and debug information will be printed to `stderr`.

# other LXQt applications

At time of writing, other LXQt applications use [`qDebug`](https://doc.qt.io/qt-5/qdebug.html), which just prints to `stderr`. Running with `2>/path/to/some/file` will get that output. Since `startlxqt` runs all the applications in `/etc/xdg/autostart`, any of these files can be edited so that their `Exec` key includes this addition.

Example:

```lang=ini
Exec=lxqt-panel "2>/tmp/lxqt-panel.log"
```

# Calamares

See `$HOME/.cache/Calamares/session.log`.
See also `/var/log/installer/debug` which is created by our [`calamares-logs-helper` script](https://git.lubuntu.me/Lubuntu/calamares-settings-ubuntu/src/branch/master/lubuntu/calamares-logs-helper) upon a successful install.

To start Calamares in debug mode `sudo calamares -d`.  Debug mode will give information regarding the modules that are loaded and the associated settings.