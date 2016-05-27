Welcome to ``zzz_manual_install`` Documentation
===============================================
Of course this tutorial have Chinese Version (`当然这篇文档也有中文版 <https://github.com/MacHu-GWU/zzz_manual_install-project/blob/master/README-CHS.rst>`_)

In python package development, you may **need to install your latest code over and over again** for testing. I guess now you are using:

1. Copy the package into ``site-packages``.
2. Use pip to install it from source code.

``zzz_manual_install`` **is designed for doing this in just one second**. If your development is in a virtual environment, this will make your package only available to use in virtualenv, but not global python interpreter.


How to Use
----------
**First**, Download the utility script ``zzz_manual_install.py``, This file can be found at https://github.com/MacHu-GWU/zzz_manual_install-project

**Second**, add this file to your package source code. For example, suppose your project layout looks like::

	myPackage-project
	|--- myPackage
	    |--- __init__.py
	    |--- other_files_and_dir ...
	    |--- zzz_manual_install.py # <--- Put it under the root dir
	|--- README.rst
	|--- setup.py
	|--- other_files_and_dir ...

**Run this file as a main script**

1. I recommend to **create a batch file in Windows, or a shell script in MacOS/Linux**, so you can easily run this script by double click! Notice, you may need super user access for doing this in MacOS/Linux.
2. Of course you could do ``$ sudo python zzz_manual_install.py`` in the terminal.

Then, your package is available in the python version that you use to run this script. If you use ``$ python27 zzz_manual_install.py``, then it's only installed in ``python27``.

I provide an `example project <https://github.com/MacHu-GWU/zzz_manual_install-project>`_ named ``example`` with ``zzz_manual_install.py`` here, and example batch file and shell script are also provided. You can easily clone this project and have it a try.


Limitation
----------
First, if your package includes C code, then god know if it will work ``>_<``!

Second, if you are using ``virtualenv``, your package source code directory should put in the root directory of your ``virtualenv``. For example, your project layout should looks like::

	env # your virtualenv directory
	|--- bin
	|--- include
	|--- lib
	|--- local
	|--- myPackage
	    |--- __init__.py
	    |--- zzz_manual_install.py # <---
	    |--- other_files_and_dir ...

Third, if you are using python2, then your project directory CANNOT HAVE NON-ASCII CHARACTER.


The internal of ``zzz_manual_install``
------------------------------------
This script is actually simply remove your old files in ``site-packages`` and copy everything in your package directory to the ``site-packages`` directory.

For Windows, it is::

    C:\Python27\Lib\site-packages\mypackage

For MacOS::

    /Library/Python/2.7/site-packages/mypackage

For Linux::

    /usr/local/lib/python2.7/dist-packages


Build your release
------------------
``zzz_manual_install`` is exetreme useful for developer. But if you want to make an official release, you need to create a ``setup.py`` file and build the distribution by yourself. You can find how by reading the following instruction:

For Python2:

- https://docs.python.org/2/distutils/setupscript.html
- https://docs.python.org/2/distutils/builtdist.html

For Python3:

- https://docs.python.org/3.4/distutils/setupscript.html
- https://docs.python.org/3.4/distutils/builtdist.html