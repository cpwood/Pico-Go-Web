---
title: "Quick Start"
description: "Make your Pico LED flash in under 5 minutes!"
lead: "Make your Pico LED flash in under 5 minutes!"
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "start"
weight: 110
toc: true
---

## Requirements

You'll need to be running [Visual Studio Code](https://code.visualstudio.com/) on a PC, Mac or Linux computer. The following processor types are supported:

* Windows - `x64`
* Mac - `x64` (Intel) or `arm64` (Silicon)
* Linux - `x64` or `arm64`

Pico-Go also needs [Python 3](https://www.python.org/downloads/) to be installed.

## Installing the extension

You can download the extension from VS Code's Extensions panel by searching for `Pico-Go`. You can also download the extension manually from the [Marketplace](https://marketplace.visualstudio.com/items?itemName=ChrisWood.pico-go).

## Start a new Pico project

### Configure the project

Firstly, create an empty folder for your project files. Then open this folder in VS Code.

Access the Command Palette by typing `ctrl+shift+i` on Windows, `ctrl+shift+alt+i` on Linux, or `command+shift+i` on a Mac. 

Alternatively, click `All Commands` on the Pico-Go status bar. Then choose `Pico-Go > Configure project`.

This will set up code auto-completion for you.

> If you're prompted to install any workspace recommended extensions or reload VS Code, make sure you do just that!

<img src="/images/configure-project.gif" class="anim"/>

### Make an LED flash

Create a file named `flash.py`, start typing and watch the auto-completion magic happen!

<img src="/images/autocomplete.gif" class="anim"/>

Here's that code in full:

```python
from machine import Pin
import time

pin = Pin(25, Pin.OUT)

while True:
    pin.toggle()
    time.sleep_ms(1000)

```

Now click the Run button on the Pico-Go status bar:

<img src="/images/run.gif" class="anim"/>

and bask in your Pico glory!

<img src="/images/flash.gif" class="anim"/>

> If you can't seem to connect to your Pico, follow these [troubleshooting steps]({{< ref "../help/connect.md" >}}).

### Copying a file

We're currently running your Python code on the Pico, however, what if we want the LED to flash automatically as soon as the Pico powers up? To do that, we need to transfer a `.py` file to the Pico!

Firstly, rename `flash.py` to `main.py`. Then choose the `Upload` button from the toolbar. You'll see that `main.py` is transferred to the Pico and it will then reboot with the LED flashing!

<img src="/images/upload.gif" class="anim"/>

## Pin Map

If you need a quick refresher on which pins can do what on the Pico board, or even just need help _locating_ a pin (it's often not easy on a soldered board!), check out `Pico-Go > Help > Show Pico Pin Map`:

<img src="/images/pin-map.gif" class="anim"/>

## Managing files via FTP

Pico-Go includes a tiny FTP server that allows you to manage the files on your Pico board via an FTP client This might be your go-to file management application or a VS Code extension with an FTP capability.

You can start the FTP server via the Command Palette by choosing `Pico-Go > Start FTP server`. This will launch an FTP server on your local computer (`127.0.0.1`) on port `2121`. The username is `pico` and the default password is also `pico`, however the password can be changed in the [Global Settings]({{< ref "settings.md" >}}) by configuring the [`ftp_password`]({{< ref "settings.md#ftp_password" >}}) value. 

<img src="/images/ftp.gif" class="anim"/>