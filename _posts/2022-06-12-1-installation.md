---
title: "1. Installation"
author: antferdom
date: 2022-06-12
category: Jekyll
layout: post
---

### Basic

The prefered way of installation is to relying on the Python Package Installer (see [PIP site](https://pypi.org/project/flamapy/)).

Please note that this proyecto requires you to have **Python version 3.9+** installed also, **it is highly recommended to perform the installation inside a virtual environmen.**

To install the core of the framework: 

```bash
$pip install flamapy
```
but remember that to execute analysis operation you might need some other repositories. For example, to run some analysis operations [AAFM](https://idus.us.es/handle/11441/78317) over feature models you might also want to install some model plugin for feature models as well as some SAT solver for the analysis support:

```bash
$pip install flamapy-fm flamapy-sat
```
This will install three plugins. First, a plugin that enables support for feature models; Second, a plugin that enable SAT support.<!-- and finally; a plugin that enables some BDD based operations. --> 

## IMPORTANT

In debian-based distributions such as Ubuntu, it is important to install the build-essential and python3-dev packages to allow the compilation of some dependencies. If you have any issue installing it please head to the [Telegram support channel](https://t.me/+ACFjaVH2ynUxNTZk) for fast support. 

### Advanced
You might also want to install flamapy without relying on any package manager, to do that, simply clone each repository of the organization and execute its install. For example, to install the core you might need to execute:
```bash
$git clone https://github.com/diverso-lab/core
$python setup.py install
```
