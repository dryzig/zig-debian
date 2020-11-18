Zig for Debian and Ubuntu
=========================

This repository contains instructions for installing the [Zig][] programming
language and toolchain on the Ubuntu and Debian operating systems, as well
as the [`debuild`][] configuration for building the corresponding binary
packages from the [upstream tarballs](https://ziglang.org/download/).

[Zig]:     https://ziglang.org
[`debuild`]: https://manpages.debian.org/testing/devscripts/debuild.1.en.html

Distributions
-------------

Currently, x86-64 (aka AMD64) binary packages are available for all recent
Ubuntu and Debian releases:

| Distribution     | Alias    | AMD64 |
| :--------------- | :------- | :---- |
| Ubuntu 20.10     | Groovy   | ✔     |
| Ubuntu 20.04 LTS | Focal    | ✔     |
| Ubuntu 19.10     | Eoan     | ✔     |
| Ubuntu 18.04 LTS | Bionic   | ✔     |
| Debian 11        | Bullseye | ✔     |
| Debian 10        | Buster   | ✔     |
| Debian unstable  | Sid      | ✔     |

Installation
------------

### Installation from an APT repository

Once you've completed the [repository configuration](#configuration) (see
further below), installation is as easy as the familiar:

```bash
$ sudo apt install zig
```

### Installation from a downloaded .DEB package file

Alternatively, you can just download the latest [`.deb`][] file and install
that directly with [`dpkg`][]:

```bash
$ wget https://github.com/dryzig/zig-debian/releases/download/0.7.0-1/zig_0.7.0-1_amd64.deb

$ sudo dpkg -i zig_0.7.0-1_amd64.deb
```

[`.deb`]: https://en.wikipedia.org/wiki/Deb_(file_format)
[`dpkg`]: https://manpages.debian.org/testing/dpkg/dpkg.1.en.html

Configuration
-------------

### Configure PGP Signing Keys

```bash
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 379CE192D401AB61
```

Configuration on Ubuntu
-----------------------

### Configure on Ubuntu 20.10 (Groovy)

```bash
$ echo 'deb https://dl.bintray.com/dryzig/zig-ubuntu groovy main' | sudo tee -a /etc/apt/sources.list
$ sudo apt update
```

### Configure on Ubuntu 20.04 LTS (Focal)

```bash
$ echo 'deb https://dl.bintray.com/dryzig/zig-ubuntu focal main' | sudo tee -a /etc/apt/sources.list
$ sudo apt update
```

### Configure on Ubuntu 19.10 (Eoan)

```bash
$ echo 'deb https://dl.bintray.com/dryzig/zig-ubuntu eoan main' | sudo tee -a /etc/apt/sources.list
$ sudo apt update
```

### Configure on Ubuntu 18.04 LTS (Bionic)

```bash
$ echo 'deb https://dl.bintray.com/dryzig/zig-ubuntu bionic main' | sudo tee -a /etc/apt/sources.list
$ sudo apt update
```

Configuration on Debian
-----------------------

### Configure on Debian 11 (Bullseye)

```bash
$ echo 'deb https://dl.bintray.com/dryzig/zig-debian bullseye main' | sudo tee -a /etc/apt/sources.list
$ sudo apt update
```

### Configure on Debian 10 (Buster)

```bash
$ echo 'deb https://dl.bintray.com/dryzig/zig-debian buster main' | sudo tee -a /etc/apt/sources.list
$ sudo apt update
```

Maintenance
-----------

### Building `zig_0.7.0-1_amd64.deb`

```bash
$ wget https://ziglang.org/download/0.7.0/zig-linux-x86_64-0.7.0.tar.xz
$ tar xvf zig-linux-x86_64-0.7.0.tar.xz
```

```bash
$ ln -s zig-linux-x86_64-0.7.0 zig-0.7.0
$ tar cJhf zig_0.7.0.orig.tar.xz zig-0.7.0
```

```bash
$ cd zig-0.7.0
$ git clone https://github.com/dryzig/zig-debian.git debian
$ debuild
```
