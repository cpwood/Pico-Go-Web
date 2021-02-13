---
title: "Why Pico-Go?"
description: "Why not contribute to the Pymakr project?"
lead: "Why not contribute to the Pymakr project?"
date: 2020-11-12T15:22:20+01:00
lastmod: 2020-11-12T15:22:20+01:00
draft: false
images: []
menu: 
  docs:
    parent: "help"
weight: 270
toc: true
---
## Background

Pretty much 99.9% of the code in this repo is from the fantastic [Pymakr](https://github.com/pycom/pymakr-vsc) project. 

Whilst the out-of-the-box version of Pymakr can talk to a Pico board after a little initial configuration, it makes certain assumptions about the capabilities of the board. For example, when transferring files, it attempts to calculate file hashes to check the file has copied correctly. The Python module that it attempts to use for this isn't available on the Pico, so uploading or downloading fails.

There were two options available: change the existing Pymakr project so it could work with another manufacturer's board - i.e. add checks to detect whether a capability was available on the board before attempting an action - or create a derivative product.

It didn't seem right or fair to place the burden of supporting third party boards on Pycom. Plus, there were several months of outstanding Pull Requests, so it wouldn't have been swift to get any proposed changes included into the extension.

For these reasons, Pico-Go was created using the Pymakr code as a starting point.

## Differences to Pymakr

At the time of writing, the main changes from the original Pymakr project are:

* Communication is via serial port only since there is no Wifi capability on the Pico;
* File hash checks have been removed;
* A new command has been added to the Command Palette allowing a user to delete all files and directories from their Pico board;
* Documentation has been comprehensively updated, corrected and pruned;
* Robustness around serial port integration has been improved;
* Supports a wider range of platforms, including Linux ARM64 and Apple Silicon;
* Provides auto-completion and intellisense out-of-the-box.