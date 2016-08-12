---
layout: post
title: Python之Package
comments: true
date: 2016-06-22 05:17:19
updated:
tags:
- python
categories:
- Python
permalink:
---

# PEP426

python最新的打包标准，定义了wheel为最新的python包。

# ensurepip/pip

内置模块,提供使用pip从pypi安装模块。

# distutils

内置的模块。处理简单的包安装。

# distutils2

distutils的升级版，已经废弃。

# distlib

取代distutils和distutils2.

<https://bitbucket.org/pypa/distlib>

# distribute

已经并入setuptools。

# setuptools

<https://github.com/pypa/setuptools>

<https://bitbucket.org/pypa/wheel>

setuotppls是第三方模块, 高级包管理工具，需要安装：

最新的setuptools是合并了原来的setuptools和distribute。

自动处理依赖，egg分发格式，包含了easy_install 来安装egg格式的包。

安装wheel包，可以支持打包wheel包。

    sudo apt-get install python-setuptools

创建setup.py文件：

    import os

    from setuptools import setup, find_packages

    import yourlib

    def read(readme):
        extend = os.path.splitext(readme)[1]
        # pypi只识别reST格式
        if (extend == ".rst"):
            import codecs
            return codecs.open(readme, 'r', 'utf-8').read()
        # pypandoc可以将markdown格式转换成reST格式
        elif (extend == ".md"):
            import pypandoc
            import codecs
            return codecs.open(pypandoc.convert(readme, 'rst'), 'r', 'utf-8').read()

    setup(
        name=NAME,
        version=VERSION,
        author='',
        author_email='',
        maintainer='',
        maintainer_email='',
        description=''
        long_description=read('README.XXX'),
        license='',
        platforms='any',
        keywords='',
        url='',
        download_url='',
        packages=find_packages(),
        package_dir={"": ""},
        install_requires=INSTALL_REQUIRES,
        extras_require='',
        cmdclass='',
        entry_points={},
        # classifiers 参考 <https://pypi.python.org/pypi?%3Aaction=list_classifiers>
        classifiers=[
            'Development Status :: 5 - Production/Stable',
            ...
        ],
        test_suite='',
        test_require='',
    )

发布到pypi主服务器pypi：

去pypi注册帐号

<https://pypi.python.org/pypi>

创建~/.pypirc文件

    [distutils]
    index-servers = pypi

    [pypi]
    username = <username>
    password = <password>

在索引中注册项目：

    $python setup.py register -r pypi

打包:

    $python setup.py sdist # 生成tarball
    $python setup.py bdist_wheel # 安装wheel包后，可以用setuptools生成wheel包

打包并上传到pypi：

    $python setup.py sdist upload -r pypi
    $python setup.py bdist_wheel upload -r pypi

# pbr

<https://github.com/openstack-dev/pbr>

# 扩展点（Entry Points）

## pkg_resources

## entry_point_inspector

<https://github.com/dhellmann/entry_point_inspector>

## stevedore

<http://docs.openstack.org/developer/stevedore/>
