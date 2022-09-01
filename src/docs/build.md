# Building apps

`op` provides a cli that can build, package and code-sign for
`win32`, `macOS` and `linux`.

## Command

The CLI can be installed globally with the `bootstrap.sh` script.
The script should install a binary called `ssc` which is placed
in `/usr/local/bin` or `C:\Program Files`, so it should be in your
path. Run the command with the `-h` flag to get help.

```sh
ssc -h
```

If the CLI tool is failing, see the [trouble shooting guide][0].

## Configuration Files

The build tool expects to find a config file in the
target directory, [`ssc.config`](./config.md).

### Settings Configuration

`input` is a directory is where your application's code
is located. The `build` string is shell code that the CLI
tool will run for you.

```syntax
#
# Build Settings
#
input: src
build: node build.js
output: dist
executable: socket

#
# Package Metadata
#
version: 0.0.1
name: Socket
description: A demo appliation
copyright: Socket Supply Co. © 2021-2022
maintainer: Contributors <floss@socketsupply.co>

linux_categories: Developer

mac_category: Developer Tools
mac_bundle_identifier: co.optool.demo
mac_sign: Voltra Co. BV (DYE7429KTV)

win32_sign: DigiCert: Socket Supply Co.

#
# window
#
title: Socket
width: 750
height: 520

#
# Backend
#
cmd: node
arg: main.js

#
# Advanced Settings
#
flags: -O3
debug_flags: -g
arch: x64
```

# PLATFORM SPECIFICS

## MAC

## WINDOWS

For signing on windows set the `SIGNTOOL` environment variable, for example

```
$env:SIGNTOOL = "C:\Program Files (x86)\Windows Kits\10\bin\10.0.19041.0\x64\signtool"
``

To sign, there must be a `cert.pfx` file on disk. and `CSC_KEY_PASSWORD` env
variable must be set.

## LINUX

[0]:/docs/troubleshooting.md
