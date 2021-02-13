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
weight: 604
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
3. prompt you to install any pre-requisite extensions.

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

### Run current selection

Runs the selected lines of Python code on the Pico board.

This can be used to step though your code on a line-by-line basis, and allows you to inspect and debug your code.

### Delete all files from board

Deletes all files and directories from the board. Useful when starting a new project.

### Project settings

Opens up the project settings configuration file in VS Code. These values override the global settings values.

### Global settings

Opens up the global settings configuration file in VS Code.

### Extra

#### Get firmware version

Shows the firmware version in the REPL console.

#### List serial ports

Shows a listing of all available serial ports in the REPL console.

#### Get support info

Shows a comprehensive list of version information in the REPL console, including VS Code, Electron, Node and Firmware versions. This is useful when raising bugs over in the [GitHub project](https://github.com/cpwood/Pico-Go/issues).

## Keyboard Shortcuts

| Action           | Windows / Linux    | macOS                 |
| ---------------- | ------------------ | --------------------- |
| (Re)connect      | `ctrl-shift-c`     | `command-shift-c`     |
|  Configure project         | `ctrl-shift-i` | `command-shift-i` |
| Global settings  | `ctrl-shift-g`     | `command-shift-g`     |
| Upload project   | `ctrl-shift-u`     | `command-shift-u`     |
| Upload current file only | `ctrl-shift-f`     | `command-shift-f`     |
| Run current file | `ctrl-shift-r`     | `command-shift-r`     |
| Run current line | `ctrl-shift-enter` | `command-shift-enter` |