+++
author = "RsyncOSX"
date = "2020-04-23"
title =  "Latest version of rsync"
tags = ["install","rsync version"]
categories = ["general information"]
description = "How to install RsyncOSX."
lastmod = "2020-07-05"
+++
The default version of rsync in macOS is old. [Version 2.6.9, protocol version 29](https://download.samba.org/pub/rsync/NEWS#2.6.9) was released in nov 2006. The current release of rsync is [version 3.2.3 protocol 31](https://download.samba.org/pub/rsync/NEWS). Due to new features in new versions of rsync and dependency to shared libraries it is not possible to bundle the latest version of rsync together with RsyncOSX. But if you want to compile your own version of rsync, please see [last on this page](/post/rsync/#compile-latest-version).

It is strongly recommended to install rsync as part of Homebrew if other version than default version in macOS. In RsyncOSX select [user configuration](/post/userconfiguration/) and set path for optional version of rsync.

## Homebrew

Install [homebrew](https://brew.sh/) and install the latest version of rsync as part of homebrew (`brew install rsync`).

## Version 3.1.3

Version 3.1.3 of rsync is compiled by me. This version is only depended upon default libraries in macOS.
- get rsync-3.1.3.dmg from [previous releases](https://github.com/rsyncOSX/RsyncOSX/releases) to install version 3.1.3 of rsync

## Snapshots

RsyncOSX supports [snapshots](/post/snapshots/) of files. Due to a bug in version 2.6.9 in rsync, the snapshot feature of RsyncOSX require to install rsync version 3.1.3 or higer.

## Compile the latest version

The source code for the latest version of rsync [can be downloaded from rsync.samba.org](https://rsync.samba.org/). There are some new features within the latest version and it require some additional libraries. I recommend to install the latest version as part of Homebrew. If you have installed Xcode command line tools and the required libraries you can also compile your own version of rsync. The following dynamic libraries is required:

```
otool -L rsync
rsync:
	/usr/local/opt/popt/lib/libpopt.0.dylib (compatibility version 1.0.0, current version 1.1.0)
	/usr/lib/libiconv.2.dylib (compatibility version 7.0.0, current version 7.0.0)
	/usr/local/opt/lz4/lib/liblz4.1.dylib (compatibility version 1.0.0, current version 1.9.2)
	/usr/local/opt/zstd/lib/libzstd.1.dylib (compatibility version 1.0.0, current version 1.4.5)
	/usr/local/opt/xxhash/lib/libxxhash.0.dylib (compatibility version 0.0.0, current version 0.7.4)
	/usr/local/opt/openssl@1.1/lib/libcrypto.1.1.dylib (compatibility version 1.1.0, current version 1.1.0)
	/usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
	/usr/lib/libcharset.1.dylib (compatibility version 2.0.0, current version 2.0.0)
  ```

Before a compile set the environment variables to let the `configure` script to find the libraries. The libraries is also installed as part of Homebrev.

```
export LDFLAGS="-L/usr/local/opt/openssl/lib -L/usr/local/lib"
export CFLAGS="-I/usr/local/opt/openssl/include/ -I/usr/local/include"
export CPPFLAGS="-I/usr/local/opt/openssl/include/ -I/usr/local/include"
```

Then execute the `configure` script to produce the makefile. I also instructs configure to install rsync in `$HOME/rsync`.

```
./configure --prefix=/Users/thomas/rsync
make
make install
```
