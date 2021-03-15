---
title: "Commands"
description: "The Command Palette options."
lead: "The Command Palette options."
date: 2020-11-12T13:26:54+01:00
lastmod: 2020-11-12T13:26:54+01:00
draft: false
images: []
menu: 
  docs:
    parent: "help"
weight: 210
toc: true
---

## Accessing the commands

You can access Pico-Go commands from the global Command Palette using `ctrl+shift+p` on a Windows or Linux computer or `command+shift+p` on a Mac. All Pico-Go commands are prefixed with `Pico-Go > `.

Alternatively, the `All Commands` button on the Pico-Go status bar the bottom of VS Code will show a filtered list of commands (only showing Pico-Go commands).

## Available Commands

### Connect

Will make Pico-Go attempt to (re-)connect to your Pico board. You can also do this by clicking `Pico Disconnected` in the status bar.

### Disconnect

Will make Pico-Go disconnect from your Pico board. You can also do this by clicking `Pico Connected` in the status bar.

### Configure project

This will:

1. configure auto-completion for your project;
2. configure linting (i.e. error and code-smell detection) for your project;
3. add a `pico-go.json` file to your project, allowing you to override global settings (if one doesn't already exist);
4. prompt you to install any pre-requisite extensions.

It's safe to run more than once as it will only ever fix up whatever's missing or broken. If you've cloned somebody else's repo and there isn't `.vscode` folder included, you may want to run this command immediately after cloning to get richer functionality.

### Upload project

Uploads all project files to the Pico, obeying any sync rules as defined in the [Settings]({{< ref "settings.md" >}}). After uploading, the board will be reset.

If you want to sync only a certain folder in your project, use the [`sync_folder`]({{< ref "settings.md#sync_folder" >}}) field in the settings and add the folder name.

By default, only the following file types are synchronized: `py,txt,log,json,xml,html,js,css,mpy`. This can be changed using the [`sync_file_types`](({{< ref "settings.md#sync_file_types" >}})) field in the settings.

### Upload current file only

Uploads the current file to the Pico.

### Download project

Downloads all files from the Pico, obeying any sync rules as defined in the [Settings]({{< ref "settings.md" >}}).

### Run current file

Runs the Python content of the open file on the Pico board without transferring the file itself. Useful for debugging.

Note that a soft reset of the board _is_ performed before the code starts running.

### Run current selection

Runs the selected lines of Python code on the Pico board.

This can be used to step though your code on a line-by-line basis, and allows you to inspect and debug your code.

Note that a soft reset of the board _isn't_ performed before the code starts running.

### Delete all files from board

Deletes all files and directories from the board. Useful when starting a new project.

### Start FTP server

Starts an FTP server running on port `2121` of your machine (`127.0.0.1`). This allows you to manage the files on your Pico through an FTP client of your choice. This might be a file manager external to VS Code or a VS Code extension.

The username is `pico` and the default password is also `pico`, however the password can be changed in the [Global Settings]({{< ref "settings.md" >}}) by configuring the [`ftp_password`]({{< ref "settings.md#ftp_password" >}}) value.

Note that the _Last Modified_ date shown in your FTP client will _always_ be "today". This is because the Pico doesn't store a meaningful timestamp against files or folders. Also, it's not possible to change the _mode_ of a file or folder (i.e. using `chmod`).

### Global settings

Opens up the global settings configuration file in VS Code.

### Reset

#### Soft

Performs a soft reset of the interpreter, deleting all Python objects and resetting the Python heap.  It tries to retain the serial connection.

#### Hard

Resets the device in a manner similar to unplugging and then replugging the USB cable.

### Help

#### Getting started

Takes you to this web site.

#### Show Pico Pin Map

Shows a pin-out diagram of the Pico board.

#### List serial ports

Shows a listing of all available serial ports in the REPL console.

#### Get support info

Shows a comprehensive list of version information in the REPL console, including VS Code, Electron, Node and Firmware versions. This is useful when raising bugs over in the [GitHub project](https://github.com/cpwood/Pico-Go/issues).

#### Check for firmware updates

This will check the firmware version of your Pico against the most recent _stable_ firmware version [available here](https://micropython.org/download/rp2-pico/). 

If a newer version is available online, you can choose to download the firmware in your web browser.

To apply the update, hold down the BOOTSEL button while plugging the board into your computer's USB port. The downloaded file should then be copied to the USB mass storage device that appears. Once programming of the new firmware is complete, the device will automatically reset and be ready for use.

## Keyboard Shortcuts

| Action           | Windows / Linux    | macOS                 |
| ---------------- | ------------------ | --------------------- |
| (Re)connect      | `ctrl-shift-c`     | `command-shift-c`     |
|  Configure project         | `ctrl-shift-i` (Windows)<br />`ctrl-shift-alt-i` (Linux) | `command-shift-i` |
| Global settings  | `ctrl-shift-g`     | `command-shift-g`     |
| Upload project   | `ctrl-shift-u`     | `command-shift-u`     |
| Upload current file only | `ctrl-shift-f`     | `command-shift-f`     |
| Run current file | `ctrl-shift-r`     | `command-shift-r`     |
| Run current line | `ctrl-shift-enter` | `command-shift-enter` |
| Soft reset       | `ctrl-shift-d`     | `command-shift-d`     |