---
title: "5. Deployment"
author: antferdom
date: 2022-06-12
category: Jekyll
layout: post
---

# Generate pip package

Follow steps to Test Pypi: https://packaging.python.org/tutorials/packaging-projects/

The next step are similar, but use the official Pypi:

1. Create setup.py
2. Update wheel and setuptools: `python3 -m pip install --upgrade setuptools wheel`
3. Generate dist folder with distributing files: `python3 setup.py sdist bdist_wheel`
4. Register user in pypi: https://pypi.org/account/register/
5. Create API Token in pypi web (inside accounts settings)
6. With generated token, create the ~/.pypirc how to say the previous step
6. Install twine (tools to upload the distribution package): `python3 -m pip install --upgrade twine`
7. Run twine and upload files: `python3 -m twine upload --repository pypi dist/*`
8. We can install our package: pip install flamapy


# Steps to create new version

1. Change version in setup.py

2. Create new git tag

```bash
$git tag -a vX.Y.Z -m "build: release X.Y.Z"
$git push --tags
```

3. Add changelog in [releases](https://github.com/diverso-lab/core/releases)

```
# Each change should be attach with (#ISSUE_NUMBER) and SHA_COMMIT
* Discover catch exception and show message instead throw exception (#2) 416fef590a734e0b2dca255b788f47c7fc028672
```

4. Update Pypi package

```bash
# With the clean repository and previous steps finished
$python3 setup.py sdist bdist_wheel
$python3 -m twine upload --repository pypi dist/*
```