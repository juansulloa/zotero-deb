<img src="https://www.zotero.org/static/images/promote/zotero-logo-256x62.png" alt="Zotero"><img src="https://juris-m.github.io/blog/image/juris-m-logo.svg" alt="Juris-M" height="62" align="right">

# Packaged versions of Zotero and Juris-M for Debian-based systems

[![Build Status](https://travis-ci.org/retorquere/zotero-deb.svg?branch=master)](https://travis-ci.org/retorquere/zotero-deb)

This repository contains packaged releases of [Zotero](https://www.zotero.org) and [Juris-M](https://juris-m.github.io) for Debian-based Linux systems and Crostini-enabled chromebooks, and the script used to build them.

This repository updates to new releases of Zotero and Juris-M within 24 hours, usually faster.

## Contents of the packages

The packages include the whole Zotero/Juris-M binaries, as built by Zotero / Juris-M teams themselves.

The packages provide a system-wide installation (into the `/usr/lib` directory), as opposed to a single-user installation (e.g. in your `HOME` directory).

They manage both desktop file registration and MimeType registration.

## Installing Zotero / Juris-M

### Installing Zotero

To install Zotero, use the following commands:

```
wget -qO- https://github.com/retorquere/zotero-deb/releases/download/apt-get/install.sh | sudo bash
sudo apt update
sudo apt install zotero
```

### Installing Juris-M

To install Juris-M, use the following commands:

```
wget -qO- https://github.com/retorquere/zotero-deb/releases/download/apt-get/install.sh | sudo bash
sudo apt update
sudo apt install jurism
```

**Note**

You can use `curl` instead of `wget` by typing
```
curl -sL https://github.com/retorquere/zotero-deb/releases/download/apt-get/install.sh | sudo bash
```

## Updating Zotero / Juris-M

The Zotero / Juris-M programs provided by this repository have their self-update facility disabled.

Simply rely on on your system's package manager to give you update notifications when a new version comes out.

Alternatively, you can use the following commands:

```
sudo apt update
sudo apt upgrade
```

## Instructions for installation on Crostini-capable Chromebooks

Instructions for installation on Crostini-capable Chromebooks can be found on the [wiki](https://github.com/retorquere/zotero-deb/wiki/Installation-on-Chromebooks).

## For packagers -- Updating the packages

The update script expects a gpg key by the name `dpkg` to be available:

Set up gpg

```
cat << EOF | gpg --gen-key --batch
%no-protection
Key-Type: RSA
Key-Length: 4096
Key-Usage: sign
Name-Real: dpkg
Name-Email: dpkg@iris-advies.com
Expire-Date: 0
%commit
EOF
```

For Travis builds, you can do the following:

```
gpg --export-secret-keys dpkg > dpkg.priv.key
travis encrypt-file dpkg.priv.key --add
```
