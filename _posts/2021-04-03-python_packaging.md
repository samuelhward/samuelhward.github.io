---
layout: post
title: "Python Packaging"
author: "Samuel Ward"
categories: thoughts
tags: [draft]
image: python_packaging.png
---

## Developing Python packages

### Environments

Use ```virtualenv```. Start by installing. Use pip for this, as installing system-wide Python packages using apt is less portable and up-to-date.

```shell
pip install virtualenv
```

In your project folder:

```shell
virtualenv venv
```
This generates the folder venv for storing the virtual environment. Best add this folder to gitignore.

Activating/deactivating the virtual environment:

```shell
source venv/bin/activate
deactivate
```

Now *all* packages installed/uninstalled etc. with pip are placed in the venv folder. By default, the virtual environment does *not* have access to the site packages.

To keep track of all the installed packages in the environment:

```shell
pip freeze > requirements.txt # Capture package requirements
pip install -r requirements.txt # Install package requirements
```

Now, working on an installed version of your project such that changes are displayed in real-time can be done inside the virtual environment from the package root directory, running:

```shell
pip install -e .
```

Note you still need to restart Python or reload the package. You can uninstall the package you're working on from the virtual environment using:

```shell
pip uninstall some_package
```

Re-installing in developer mode will then re-install dependencies.

### Distributing/Installing Your Package

Use ```setuptools```. Here you will define a setup.py file which allows pip to install your package. If you edit the setup.py then you will need to re-install the package.

Unlike with ```pip freeze```, you will have to manually define the packages in the setup.py file (you _could_ automate this process but it's not recommended, since `requirements.txt` and `setup.py` are technically doing different things).

### Using Your Package/Environment As A Jupyter Kernel

After activating your ```venv```, you need to re-install the ipykernel package:

```shell
pip install --user ipykernel
```

Then use that package to install a new kernel that uses your venv for Jupyter: 

```shell
python -m ipykernel install --user --name=venv
```

Too see a list of available kernels:

```shell
jupyter kernelspec list
```

To remove a kernel:

```shell
jupyter kernelspec uninstall myenv
```

