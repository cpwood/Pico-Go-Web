---
title: "Settings"
description: "An overview of the various configuration options."
lead: "An overview of the various configuration options."
date: 2020-11-12T13:26:54+01:00
lastmod: 2020-11-12T13:26:54+01:00
draft: false
images: []
menu: 
  docs:
    parent: "help"
weight: 220
toc: true
---

## Accessing the settings
### Global Settings

Global settings apply to all projects, unless overridden by project-level settings.

You can access the global settings by typing `ctrl+shift+g` or using the `Pico-Go > Global settings` option in the Command Palette.

### Project Settings

Project settings override global settings, though not all global settings can be overridden.

You can access the project settings by using the `Pico-Go > Project settings` option in the Command Palette.

## Options
### auto_connect
Autoconnect on USB. If `false`, `manual_com_device` should be set.

| Project | Global | Default               |
|---------|--------|-----------------------|
| no       | yes    | `true` |

### autoconnect_comport_manufacturers
USB COM port manufacturers. Used with `auto_connect` to try and identify a Pico board.

| Project | Global | Default               |
|---------|--------|-----------------------|
| no | yes | `"MicroPython", "Microsoft"` |

### ctrl_c_on_connect
If `true`, executes a ctrl-c on connect to stop running programs.

| Project | Global | Default               |
|---------|--------|-----------------------|
| yes     | yes    | `false`                |

### ftp_password
The password to use for authenticating with the Pico-Go FTP server.

| Project | Global | Default               |
|---------|--------|-----------------------|
| no     | yes    | `pico`                |

### manual_com_device
Used when `auto_connect` is false. E.g. `COM3` or `/dev/tty.usbmodem0000000000001`.

| Project | Global | Default               |
|---------|--------|-----------------------|
| no       | yes    | `true` |

### open_on_start
Whether to open the terminal and connect to the board when starting Code. The default setting (from `v1.2` onward) is to _not_ launch the Pico Console unless the project has been [configured as a Pico-Go project]({{< ref "../help/commands.md#configure-project" >}}).

| Project | Global | Default                                                      |
| ------- | ------ | ------------------------------------------------------------ |
| yes     | yes    | `false`  at _global_ level settings<br />`true` at _project_ level settings |

### py_ignore
Comma-separated list of files and folders to ignore when uploading (no wildcard or regular expressions supported).

| Project | Global | Default               |
|---------|--------|-----------------------|
| yes     | yes    | `[]`                  |

### reboot_after_upload
Reboots your board after any upload or download action.

| Project | Global | Default               |
|---------|--------|-----------------------|
| yes | yes | `true` |

### safe_boot_on_upload
Safe-boot before upload.

| Project | Global | Default               |
|---------|--------|-----------------------|
| yes | yes | `false` |

### statusbar_buttons
Which quick-access buttons to show in the status bar.

| Project | Global | Default               |
|---------|--------|-----------------------|
| yes     | yes     |`['status', 'run', 'upload', 'download', 'disconnect', 'listserial', 'settings', 'projectsettings', 'getversion']` |

### sync_all_file_types
If enabled, all files will be uploaded no matter the file type (`sync_file_types` will be ignored).

| Project | Global | Default               |
|---------|--------|-----------------------|
| yes  | yes    | `false` |

### sync_file_types
Types of files to be synchronized.

| Project | Global | Default               |
|---------|--------|-----------------------|
| yes     | yes    | `"py,txt,log,json,xml,html,js,css,mpy"` |

### sync_folder
Folder to synchronize. Empty to sync project's main folder.

| Project | Global | Default               |
|---------|--------|-----------------------|
| yes     | yes    | `""`                  |
