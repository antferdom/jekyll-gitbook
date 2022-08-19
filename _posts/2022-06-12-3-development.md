---
title: "3. Development"
author: antferdom
date: 2022-06-12
category: Jekyll
layout: post
---

### Install existing pluginsin mode development with development tools

#### Automatic mode

Configure your plugins, there are at the moment two separate plugins/metamodels repositories:

```bash
$git clone git@github.com:flamapy/fm_metamodel.git
$git clone git@github.com:flamapy/pysat_metamodel.git
$git clone git@github.com:flamapy/bdd_metamodel.git
```

If you want to use the plugins, you need edit an environment variable with the full path of the plugins/metamodels:

Example:

```bash
$export PLUGIN_PATHS=~/flamapy/fm_metamodel/:~/flamapy/pysat_metamodel/:~/flamapy/bdd_metamodel/
```

Install full environment for develop:

```bash
$make dev
```

Your virtual environment is installed inside core directory. It is crucial to use it during development and testing.


#### Manual mode

The advise is create a parent folder where install the tools and download all repositories:

```
mkdir diverso-lab; cd diverso-lab
git clone git@github.com:diverso-lab/core.git
git clone git@github.com:diverso-lab/fm_metamodel.git
git clone git@github.com:diverso-lab/pysat_metamodel.git
```

Create virtual environment and install repositories in editable mode:

```bash
$python3 -m venv env
$source env/bin/activate
$pip install -e core[dev]
$pip install -e fm_metamodel
$pip install -e pysat_metamodel
```

There is a problem with plugins in editable mode because we use find_namespace_package from setuptools for install it.
If you want that discover find your plugins, you need make a symbolics links inside core repository:

```bash
$mkdir core/flamapy/metamodels
#it is important to specify absolute paths for the origin route when creating symbolic links
$ln -s ~/diverso-dev/fm_metamodel/flamapy/metamodels/fm_metamodel core/flamapy/metamodels/fm_metamodel
$ln -s ~/diverso-dev/pysat_metamodel/flamapy/metamodels/pysat_metamodel core/flamapy/metamodels/pysat_metamodel
```

Your environment is prepared.

### Testing
#### Run tests

With the module installed, you can execute:

```bash
$pip install pytest
$make test
```

#### Run test with coverage

```bash
$pip install pytest coverage
$make cov
```


#### Review code quality and styles error

```bash
$pip install prospector
$make lint
```


#### Review hint typing

```bash
$pip install mypy
$make mypy
```

### Deployment
You can check how to deploy this tool using different delivery options in [Deployment](https://flamapy.github.io/docs/jekyll/2022-06-12-6-deployment.html).

### Create new plugins with the provide generator tool

FlamaPy framework provides a tools to generate structure for new plugins.

The tools is `flamapy_admin.py`

You can create a new plugins with the next command:

```bash
$flamapy_admin.py --path PLUGIN_PATH NAME_PLUGIN EXTENSION_PLUGIN
# Example
$flamapy_admin.py --path /home/user/flamapy-plugin1 plugin1 plug1
```