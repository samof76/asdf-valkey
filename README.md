# asdf-valkey ![Build](https://github.com/samof76/asdf-valkey/workflows/Build/badge.svg?branch=master)

valkey plugin for [asdf](https://github.com/asdf-vm/asdf) version manager

## Dependencies
_This requires [brew](http://brew.sh) if you're on a mac, or a debian flavored linux.  If you need it to work on something else, you'll likely need to modify the plugin._

1. You will need a compiler.
  * Mac
    1. ```gcc```
    1. Hit the ok button and it will install.  If it already has it, then you are good.
  * Ubuntu
    1. ```sudo apt-get install linux-headers-$(uname -r) build-essential```

## Install

Install the valkey plugin

```bash
asdf plugin add valkey https://github.com/samof76/asdf-valkey.git
```

List all available versions of valkey ...

```bash
asdf list all valkey
# Outuput
# 7.2.4-rc1
# 7.2.4-rc1
# 7.2.4
# 7.2.5-rc1
# 7.2.5
# 7.2.6
# 7.2.7
# 7.2.8
# 7.2.9
# 7.2.10
# ...
# 8.1.3
```

Install the `8.1.3` version of valkey by running:

```bash
asdf install valkey 8.1.3
```

Set that version globally.

```bash
# If you are using older versions of asdf, you may need to run this...
asdf global valkey 8.1.3
# If you are on the latest version of asdf
asdf set -u valkey 8.1.3
```

## Try it out
1. Open up a terminal and run `valkey-server`.  This will get it running on the standard port (6379)
1. Open another terminal and run `valkey-cli`.   This will open the valkey cli so you can manually set, get, and delete keys.  For example:
```sh
~ % valkey-cli
127.0.0.1:6379> set someKey "boomdiggity"
OK
127.0.0.1:6379> get someKey
"boomdiggity"
```
As long as that initial terminal session is running, you should be able to use it on port 6379 on localhost.  Have fun!

## Gotchas
This is a bare bones install of valkey.  It has no configuration setup, no restart setup, or anything else.  It's just the binaries.  Fortunately, the binaries are usually all you need for dev environments.

## Use

Check [asdf](https://github.com/asdf-vm/asdf) readme for instructions on how to install & manage versions of valkey.

When installing valkey using `asdf install`, you can pass custom configure options with the following env vars:

* `VALKEY_CONFIGURE_OPTIONS` - use only your configure options
* `VALKEY_EXTRA_CONFIGURE_OPTIONS` - append these configure options along with ones that this plugin already uses
* `VALKEY_APPLY_PATCHES` - a list of files or URLs to apply patches to valkey

You may also apply custom patches before building with `VALKEY_APPLY_PATCHES`. For example:

```shell
VALKEY_APPLY_PATCHES=$'dir/1.patch\n2.patch\nhttp://example.com/3.patch' asdf install valkey 7.0.12
VALKEY_APPLY_PATCHES="https://patch-diff.githubusercontent.com/raw/valkey/valkey/pull/12601.diff" asdf install valkey 7.0.12
```

## Thank You

This was initially forked from [asdf-redis](https://github.com/smashedtoatoms/asdf-redis). And I would want to sincerely thank [*smashedtoatoms*](https://github.com/smashedtoatoms) for his work on asdf-redis.
