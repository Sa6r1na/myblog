---
title: mac下robotframework环境安装
date: 2019-04-23 12:31:28
tags:
---

## 环境

### 安装Python
* brew install python(默认安装的是3)

```

Python has been installed as
  /usr/local/bin/python3

Unversioned symlinks `python`, `python-config`, `pip` etc. pointing to
`python3`, `python3-config`, `pip3` etc., respectively, have been installed into
  /usr/local/opt/python/libexec/bin

If you need Homebrew's Python 2.7 run
  brew install python@2

You can install Python packages with
  pip3 install <package>
They will install into the site-package directory
  /usr/local/lib/python3.7/site-packages

See: https://docs.brew.sh/Homebrew-and-Python
```
<!--more--->

* 安装Python2.7

```
==> Downloading https://homebrew.bintray.com/bottles/python@2-2.7.16.mojave.bott
==> Downloading from https://akamai.bintray.com/cb/cb90a15faf89116993fd85c330069
######################################################################## 100.0%
==> Pouring python@2-2.7.16.mojave.bottle.1.tar.gz
==> /usr/local/Cellar/python@2/2.7.16/bin/python -s setup.py --no-user-cfg insta
==> /usr/local/Cellar/python@2/2.7.16/bin/python -s setup.py --no-user-cfg insta
==> /usr/local/Cellar/python@2/2.7.16/bin/python -s setup.py --no-user-cfg insta
==> Caveats
Pip and setuptools have been installed. To update them
  pip install --upgrade pip setuptools

You can install Python packages with
  pip install <package>

They will install into the site-package directory
  /usr/local/lib/python2.7/site-packages

See: https://docs.brew.sh/Homebrew-and-Python
==> Summary
🍺  /usr/local/Cellar/python@2/2.7.16: 3,706 files, 50.6MB
```

### 安装robotframework

* pip install robotframework

```
DEPRECATION: Python 2.7 will reach the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 won't be maintained after that date. A future version of pip will drop support for Python 2.7.
Collecting robotframework
  Downloading https://files.pythonhosted.org/packages/36/c6/6f89c80ac5a526a091bd383ffdfc64c9a68d9df0c775d4b36f03d8e0ac25/robotframework-3.1.1-py2.py3-none-any.whl (601kB)
    100% |████████████████████████████████| 604kB 8.3kB/s
Installing collected packages: robotframework
Successfully installed robotframework-3.1.1
2019-04-23 12:52:50.910 osascript[46332:274027] TISFileInterrogator updateSystemInputSources false but old data invalid: currentCacheHeaderPtr nonNULL? 0, ->cacheFormatVersion 0, ->magicCookie 00000000, inputSourceTableCountSys 0
Keyboard Layouts: duplicate keyboard layout identifier -14934.
Keyboard Layouts: keyboard layout identifier -14934 has been replaced with -28673.
```

* pip install robotframework-ride

```
DEPRECATION: Python 2.7 will reach the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 won't be maintained after that date. A future version of pip will drop support for Python 2.7.
Collecting robotframework-ride
  Downloading https://files.pythonhosted.org/packages/4e/a6/1835a17fa566b19c166735a9a75d55101e53b68566771ddb0b690dd4be83/robotframework_ride-1.7.3.1-py2.py3-none-any.whl (926kB)
    100% |████████████████████████████████| 931kB 13kB/s
Collecting Pygments (from robotframework-ride)
  Downloading https://files.pythonhosted.org/packages/13/e5/6d710c9cf96c31ac82657bcfb441df328b22df8564d58d0c4cd62612674c/Pygments-2.3.1-py2.py3-none-any.whl (849kB)
    100% |████████████████████████████████| 849kB 163kB/s
Collecting Pypubsub (from robotframework-ride)
  Downloading https://files.pythonhosted.org/packages/95/5a/1801be1a63af9250e79b8941a37b88e3ca0d660b880b9862fe9016ae6a3a/PyPubSub-3.3.0.zip (87kB)
    100% |████████████████████████████████| 92kB 442kB/s
Collecting Pywin32 (from robotframework-ride)
  Could not find a version that satisfies the requirement Pywin32 (from robotframework-ride) (from versions: )
No matching distribution found for Pywin32 (from robotframework-ride)
```

### 安装wxpthon
* pip install -U wxPython

```
DEPRECATION: Python 2.7 will reach the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 won't be maintained after that date. A future version of pip will drop support for Python 2.7.
Collecting wxPython
  Downloading https://files.pythonhosted.org/packages/89/4f/e1cf83bf07a22d2a3ab204a05b00bb99d838f329cfade100c116ef026b16/wxPython-4.0.4-cp27-cp27m-macosx_10_6_intel.whl (31.3MB)
    100% |████████████████████████████████| 31.3MB 133kB/s
Collecting six (from wxPython)
  Downloading https://files.pythonhosted.org/packages/73/fb/00a976f728d0d1fecfe898238ce23f502a721c0ac0ecfedb80e0d88c64e9/six-1.12.0-py2.py3-none-any.whl
Collecting Pillow (from wxPython)
  Downloading https://files.pythonhosted.org/packages/61/88/fc486aa50f733ce6c94e58637df61a9f0859aa9bc5d110d765a8d59f8000/Pillow-6.0.0-cp27-cp27m-macosx_10_6_intel.macosx_10_9_intel.macosx_10_9_x86_64.macosx_10_10_intel.macosx_10_10_x86_64.whl (3.7MB)
    100% |████████████████████████████████| 3.7MB 133kB/s
Installing collected packages: six, Pillow, wxPython
Successfully installed Pillow-6.0.0 six-1.12.0 wxPython-4.0.4
```


#### 遇到问题


```
Collecting Pywin32 (from robotframework-ride)
  Could not find a version that satisfies the requirement Pywin32 (from robotframework-ride) (from versions: )
No matching distribution found for Pywin32 (from robotframework-ride)
```
####解决方案

``` 
git clone git@github.com:robotframework/RIDE.git
cd RIDE
python setup.py build
sudo python setup.py install
```
