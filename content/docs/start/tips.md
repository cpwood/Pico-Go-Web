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
### Assembly code errors

When writing assembly code for PIO, you may find that VS Code gets very grumpy about your code! This is because the code you're writing isn't valid Python code (which is correct, you're writing in assembly language!). We need to explicitly tell the linter to ignore such code.

There are two ways of doing this!

#### Pylance

> If you used `Pico-Go > Configure project` to set up your project, follow these instructions.

Move your assembly methods to a separate file - e.g. `foo_asm.py` - and ensure the first line of that new file reads:

```
# type: ignore
```

Then reference your new file in your existing file.

<img src="/images/assembly-language.gif" class="anim"/>

If you find it difficult to remember this line of code, you can copy and paste it from the intellisense provided when you hover over the `@asm_pio` attribute

#### Pylint

Adding a comment such as:

```
# pylint: disable=E,W,C,R
```

to the assembly function will make these problems go away. 

If you find it difficult to remember this line of code, you can copy and paste it from the intellisense provided when you hover over the `@asm_pio` attribute:

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