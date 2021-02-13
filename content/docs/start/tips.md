---
title: "Tips, Tricks & Hints"
description: "How to deal with some common scenarios."
lead: "How to deal with some common scenarios."
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "start"
weight: 120
toc: true
---

## Coding Issues
### Assembler code errors

When writing assembler code for PIO, you may find that VS Code gets very grumpy about your code! This is because the code you're writing isn't valid Python code (which is correct, you're writing in assembly language!). We need to explicitly tell Pylint to ignore such code.

There are two ways of doing this!

#### Using a comment

Adding a comment such as:

```
# pylint: disable=E,W,C,R
```

to the assembler function will make these problems go away. If you find it difficult to remember this line of code, you can copy and paste it from the intellisense provided when you hover over the `@asm_pio` attribute:

<img src="/images/assembly-comment.gif" class="anim"/>

> As you can probably see in the above animation, VS Code still issues its own warnings (as opposed to Pylint).

#### Put assembly code in a separate file

Any files that end with `_asm.py` are automatically excluded from Pylint's linting process, so you can refactor the code to move it into a separate file:

<img src="/images/assembly-refactor.gif" class="anim"/>

### Errors with official code

Some of the code samples in the [Python SDK documentation](https://datasheets.raspberrypi.org/pico/raspberry-pi-pico-python-sdk.pdf) include code that is _technically_ incorrect but actually runs fine on the Pico.

For example, this code will give a linting error:

```python
import time
time.sleep_ms(1000)
```

![](/images/linting-error.png)

The reason this works OK on the Pico is that `time` is remapped to `utime`, which _does_ include `sleep_ms()`. It does similar things with `os` to `uos`, for example.

You'll need to rewrite the code as follows:

```python
import utime
utime.sleep_ms(1000)
```

### Incorrect autocompletion or guidance

The content for autocompletion and guidance is a work in progress as part of the [Pico-Stub](https://github.com/cpwood/Pico-Stub) project.

If you can identify a problem _and_ some documentation or examples to support it, please [raise an issue](https://github.com/cpwood/Pico-Stub/issues) there and a fix will appear in a later version of Pico-Go.

## Platform Issues
### Connection Problems

The most common problem here is that your serial port is already being used by another application (even though you could swear blind that it isn't!).

Follow [these instructions]({{< ref "../help/connect.md" >}}) to try and figure out what's going on.

### Wrong COM Port

If you find that Pico-Go is trying to connect to an incorrect device, you can configure the device manually.

Open the Global Settings (`ctrl+shift+g` or `command+shift+g`) and set `auto_connect` to be `false`. Also set a `manual_com_device` value. On Windows, this might be `COM3` for example, or on Linux and Mac it will be similar to `/dev/tty.usbmodem0000000000001`.

### Unsupported OS

Right now, Pico-Go only supports the following platforms:

* Windows
  * `x64`
* Linux
  * `x64` and `arm64`
* macOS
  * `x64` (Intel) and `arm64` (Silicon / M1)

This is because an underlying library - serialport - is unsupported on 32-bit operating systems. Please don't report an error message telling you about this as a bug.

### Remote SSH Extension

VS Code's [Remote SSH](https://code.visualstudio.com/docs/remote/ssh) extension is not currently supported, though you may be able to force it to work by calling `npm rebuild` on the extension's folder on the remote host.