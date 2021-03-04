---
title: "Breaking Changes"
description: "The following functionality has changed between versions."
lead: "The following functionality has changed between versions."
date: 2020-11-12T15:22:20+01:00
lastmod: 2020-11-12T15:22:20+01:00
draft: false
images: []
menu: 
  docs:
    parent: "help"
weight: 255
toc: true
---

## v1.1.0 to v1.2.0

* `pymakr.conf` files are no longer supported. Rename these to `pico-go.json`. We've chosen not to rename such files automatically in case people continue to use Pymakr for other non-Pico projects.
* Not a _breaking_ change, however the global default for `open_on_start` on new installations of Pico-Go has changed to `false`. The default for project-level `pico-go.json` files is `true`, however. This means that Pico-Go won't appear automatically whenever you load VS Code; it'll only appear automatically for Pico-Go projects. We recognise that you probably don't use VS Code exclusively for Pico development, so this will make your overall VS Code experience a bit more straightforward!