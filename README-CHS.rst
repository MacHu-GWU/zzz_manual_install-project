欢迎来到　``zzz_manual_install`` 的文档
===============================================
`原英文文档链接 <https://github.com/MacHu-GWU/zzz_manual_install-project/blob/master/README.rst>`_)

在Python扩展包的开发过程中，你可能需要　**频繁地在你的开发机器上安装你的包** 以进行测试. 你目前做这件事的方式可能是：

1. 将所有文件拷贝到 ``site-packages``　目录下。
2. 使用 ``pip`` 从源码安装你的包。

``zzz_manual_install`` **可以瞬间完成上面的操作**。如果你使用了 ``virtualenv`` 在一个虚拟环境中开发，那么你的包仅仅会在虚拟环境中可用。


如何使用
----------
**首先**，　下载该脚本 ``zzz_manual_install.py``，你可以在 https://github.com/MacHu-GWU/zzz_manual_install-project　找到他

**接着**，　将该脚本拷贝到你的扩展包的目录下。举例说明，假若你的开发目录看起来像这样：

.. code-block:: console

	|--- myPackage-project
	    |--- myPackage
	        |--- __init__.py
	        |--- other_files_and_dir ...
	        |--- zzz_manual_install.py # <--- 在你的项目的跟目录下
	    |--- README.rst
	    |--- setup.py
	    |--- other_files_and_dir ...

**最后以主脚本运行改脚本**

1. 我个人推荐为运行改脚本 **在Windows系统中创建一个批处理文件，或创建一个命令行脚本若你使用MacOS/Linux系统**，则你可以通过双击脚本进行一键安装。值得注意的是，你在MacOS/Linux系统中可能需要超级用户权限。
2. 你也可以在命令行中使用 ``sudo python zzz_manual_install.py`` 进行安装。

然后，你的包就在你刚才用来运行 ``zzz_manual_install.py``　脚本的Python版本中变得可用了。例如你刚刚如果是用的 ``python27 zzz_manual_install.py``，那么你只对 ``python27`` 进行安装了。

我提供了一个 `例子(名字就叫example) <https://github.com/MacHu-GWU/zzz_manual_install-project>`_ 以供参考，并且也附上了用于一键安装的批处理文件和壳脚本。您可以直接克隆项目到本地亲自试一试。


一些限制
----------
首先，如果你的扩展包包含了Ｃ代码，那么我也无能为力。

其次，如果你使用了 ``virtualenv``，　那么你的扩展包源码需要放在 ``virtualenv``　的根目录下。例如：

.. code-block:: console

	|--- env # your virtualenv directory
	    |--- bin
	    |--- include
	    |--- lib
	    |--- local
	    |--- myPackage
	        |--- __init__.py
	        |--- zzz_manual_install.py # <---
	        |--- other_files_and_dir ...

最后，如果你使用的是Python2, 那么你的开发目录路径中绝对不能有非ASCII字符。


``zzz_manual_install``　的内部原理
------------------------------------
该脚本实际上是将你在　``site-packages`` 目录下的你的包的旧文件删除，然后拷贝新闻兼过去。

在Windows系统中，该目录是::

    C:\Python27\Lib\site-packages\mypackage

苹果系统MacOS::

    /Library/Python/2.7/site-packages/mypackage

Linux系统::

    /usr/local/lib/python2.7/dist-packages


发布你的包
------------------
``zzz_manual_install`` 在开发过程中非常方便。但如果你想正式发布你的包，你需要创建一个 ``setup.py``　文件然后 build 你的发布。这不是本文应有的内容，相关的官方资料请参考:

Python2:

- https://docs.python.org/2/distutils/setupscript.html
- https://docs.python.org/2/distutils/builtdist.html

Python3:

- https://docs.python.org/3.4/distutils/setupscript.html
- https://docs.python.org/3.4/distutils/builtdist.html
