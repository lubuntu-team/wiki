The file *debian/changelog* file documents in a short form all changes made to the package. This is not only useful for other developers, but also for normal users.

# Format

A normal changelog entry looks like:
```
super-package (0.13.0-0ubuntu5) eoan; urgency=medium

  [ Minnie Mouse ]
  * Add feature foo
  * Refactor of lib bar:
    - Use strategy pattern
      + Added simple strategy
      + Added normal strategy
      + Added heavy strategy
    - Better naming
  [ Mickey Mouse ]
  * Added unit tests

 -- tricky-mickey <mickey@mouse.org>  Sun, 01 Apr 2019 11:17:17 +0200
```

  - Every line of the changelog entry should have a bullet point in front and in the order of `*`, `-`, `+`. If you need more levels, restart with the `*` bullet point.
  - Use two spaces to indent.
  - No trailing whitespaces.

# debchange

To edit the changelog, you can use the tool `debchange` from the package `devscripts`.

| Command | Explanation |
| ------------- | -------------- |
| `dch -a`    | Append a new bullet point to the newest changelog entry |
| `dch -i`     | Increment the version number: e.g `0.13.0-0ubuntu5 => 0.13.0-0ubuntu6` |
| `dch --distribution=eoan` | Replace `UNRELEASED` with the specified distribution |
| `dch -r ""` | Update the changelog timestamp |

## Links

  - [Debian manual](https://www.debian.org/doc/manuals/maint-guide/dreq.en.html#changelog)
  - [Debian policy](https://www.debian.org/doc/debian-policy/ch-source.html#debian-changelog-debian-changelog)


