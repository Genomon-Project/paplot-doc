************************
Install
************************

| Paplot runs on:

 * Linux 
 * MacOS X
 * Windows

| You need python2.7 or python 3.5 to run paplot.paplot (previous versions of Python have not been tested).

.. _linux:

================================================
For Linux
================================================

1. Install paplot
--------------------------

| Download the latest ``Source code (zip)`` files from the paplot web-site (https://github.com/Genomon-Project/paplot/releases/).

.. code-block:: bash

  cd {the directory where you want to install paplot}
  # For v0.5.4
  wget https://github.com/Genomon-Project/paplot/archive/v0.5.4.zip
  unzip v0.5.4.zip
  cd paplot-0.5.4/

  python setup.py build install
  
  # If you get an error with the above command, try this
  export PATH=~/.local/bin/:$PATH
  export LD_LIBRARY_PATH=~/.local/lib/:$LD_LIBRARY_PATH
  python setup.py build install --user

| When the following messages appear, then the installation is successful!

.. code-block:: bash

  paplot --version
  paplot-0.5.4

| After installation, try :doc:`quick_start`.

.. note::
  
  Set PATH
  
  | Add the following two lines to ~/.bashrc or ~/.bash_profile.

  .. code-block:: bash
  
    export PATH=~/.local/bin/:$PATH
    export LD_LIBRARY_PATH=~/.local/lib/:$LD_LIBRARY_PATH
  

.. _macosx:

================================================
For MacOS X
================================================

1. Download source files 
------------------------------------

| Download the latest version Source code (zip) from the paplot site (https://github.com/Genomon-Project/paplot/releases/).

| Alternatively, ``git`` is installed, you can type ``git clone -b master https://github.com/Genomon-Project/paplot.git``.

2. Install paplot
--------------------------

| Launch Terminal and change the directory where the source files are downloaded.

.. code-block:: bash

  cd {the directory where paplot source files are downloaded}


| Install paplot.

.. code-block:: bash
  
  python setup.py build install --user

3. Setting PATH
----------------

| Add the path of the executable file to PATH with terminal.
| Usually, the executable file of paplot is installed below.

``/Users/<user name>/Library/Python/2.7/bin``

.. code-block:: bash

  export PATH={the directory where paplot is installed}/bin:$PATH
  export LD_LIBRARY_PATH={the directory where paplot is installed}/lib:$LD_LIBRARY_PATH
  
  # Mostly you can set up by adding forlowing lines (replace <user name> with your user name).
  # export PATH=/Users/<user name>/Library/Python/2.7/bin:$PATH
  # export LD_LIBRARY_PATH=/Users/<user name>/Library/Python/2.7/lib:$LD_LIBRARY_PATH


| Verify installation

.. code-block:: bash

  paplot --version
  paplot-0.5.4

| Then, the installation is successful! Try :doc:`quick_start`.

  
.. _windows:

====================================
For Windows
====================================

1. Install Python
---------------------------

| To execute paplot in Windows, using winPython or Python(x,y) is recommended. 
| Alternatively, you can use cygwin (then refer to :ref:`For Linux <linux>`).

 * winPython http://winpython.github.io/
 * Python(x,y) http://python-xy.github.io/

| Paplot is verified in python 2.7.10, python 3.5.3.
| 

2. Install paplot
-----------------------------

| Download the latest ``Source code (zip)`` files from the paplot site (https://github.com/Genomon-Project/paplot/releases/),
| and unzip the downloaded file into an arbitrary folder.


| Launch Command prompt, and change the directory where the source files of paplot are unzipped.

.. code-block:: bash

  cd {the directory where the source files are unzipped}

| Execute the command for installing paplot.

.. caution::

  The following command is for the case where WinPython-64bit-2.7.10.3 is installed.

.. code-block:: bash

  > C:\WinPython-64bit-2.7.10.3\python-2.7.10.amd64\python.exe setup.py build install

| Then, execute the test command.

::

  > C:\WinPython-64bit-2.7.10.3\python-2.7.10.amd64\python.exe paplot --version
  paplot-0.5.4

| It will be successful if such a display appears.
|
| After installation, try :doc:`quick_start`.
|

.. |new| image:: image/tab_001.gif
