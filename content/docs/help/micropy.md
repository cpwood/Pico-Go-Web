---
title: "Micropy-CLI"
description: "How to configure Micropy-CLI for the Pico."
lead: "How to configure Micropy-CLI for the Pico."
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "help"
weight: 230
toc: true
---
## Introduction
The easiest way to get started with a new project is to use the `Pico-Go > Configure project` option within the command palette. However, if you're more familiar with Micopy-CLI and would prefer to use this, here's how to use it with Pico-Go.

## The Very Basics

You’ll need a few things installed:

*   [**Python**](https://www.python.org/downloads/) — download and install for your platform;
*   [**NodeJS**](https://nodejs.org/en/) — download and install the LTS version for your platform;
*   [**Visual Studo Code**](https://code.visualstudio.com/) — obviously!

Once you’ve got Python installed, you’ll also want to install **Pip**. Download [this file](https://bootstrap.pypa.io/get-pip.py) and then issue the following command from a terminal / Command Prompt window:

```
# On Linux or macOS  
python get-pip.py
# On Windows  
py get-pip.py
```

Keep a lookout for any warnings about Pip not being within your PATH environment variable. If you see such a warning, copy the path it mentions and [add it into your PATH](https://gist.github.com/nex3/c395b2f8fd4b02068be37c961301caa7).

Also, if you’re on a **Mac**, launch VS Code and from the Command Palette (`Command + Shift + P`), choose to install the “code” command in PATH:

## Other Prerequisites

Right, time to install some stuff specific to our goal: writing code in MicroPython for your Pico board!

```
pip install micropy-cli  
pip install pylint
```

The [**Micropy CLI**](https://github.com/BradenM/micropy-cli) is used to quickly setup new projects so that they include code completion and _linting_ (i.e. trying to detect problems and errors).

[**Pylint**](https://www.pylint.org/) is what will actually do that linting!

## Configuring Micropy CLI

In order to do our code completion and linting, Micropy CLI needs to know a little bit more about the Pico and what it can do. Specifically, it needs to know which Python modules are baked into the board for our use and which functions and properties are included in each.

This is where the [**Pico-Stub**](https://github.com/cpwood/Pico-Stub) project comes in.

“Stubs” are what provide Micropy (and Pylint) with that intelligence. They’re generated automatically by running Python code _on_ the Pico board itself. They’re then brought back to a normal computer and are made available for use within Micropy CLI through my repo.

[Download a copy](https://github.com/cpwood/Pico-Stub/archive/main.zip) of the repo and extract the zip file. Then add the stubs to Micropy CLI:

```
cd Pico-Stub-main/stubs  
micropy stubs add micropython-rp2-1_13-290
```

## Other VS Code Extensions

Inside VS Code, search for and install the following two extensions:

*   ms-python.python
*   VisualStudioExptTeam.vscodeintellicode

If you haven't already, install  [**Pico-Go**](https://marketplace.visualstudio.com/items?itemName=ChrisWood.pico-go). 

## Starting a new project

Open up VS Code and, in the terminal, type:

```
micropy init
```

It will suggest a **project name** — just choose the default:

![](/images/micropy-init-1.png)

Then you’ll need to choose at least these **two option**s:

![](/images/micropy-init-2.png)

If you intend to put your project in a Git repository afterwards, you’ll probably want the **Git Ignore Template** too.

Finally, you’ll need to choose the Pico’s **stubs**:

![](/images/micropy-init-3.png)

All being well, you should see something like this:

![](/images/micropy-init-4.png)


