************************
Install
************************

| paplot runs on:

 * Linux 
 * MacOS X
 * Windows

| You require Python2.7 or Python 3.5 to execute paplot (previous versions of Python have not been tested).

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

| If the following messages appear, the installation is successful!.

.. code-block:: bash

  paplot --version
  paplot-0.5.4

| After installation, open :doc:`quick_start`.

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

| Download the latest ``Source code (zip)`` files from the paplot website (https://github.com/Genomon-Project/paplot/releases/).

| Alternatively, if ``git`` is installed, you can type ``git clone -b master https://github.com/Genomon-Project/paplot.git``.

2. Install paplot
--------------------------

| Launch Terminal, and change the directory where the source files are downloaded.

.. code-block:: bash

  cd {the directory where paplot source files are downloaded}


| Install paplot.

.. code-block:: bash
  
  python setup.py build install --user

3. Setting PATH
----------------

| Add the path of the executable file to PATH with terminal.
| Generally, the executable file of paplot is installed as described below.

``/Users/<user name>/Library/Python/2.7/bin``

.. code-block:: bash

  export PATH={the directory where paplot is installed}/bin:$PATH
  export LD_LIBRARY_PATH={the directory where paplot is installed}/lib:$LD_LIBRARY_PATH
  
  # Mostly you can set up by adding the following lines (replace <user name> with your user name).
  # export PATH=/Users/<user name>/Library/Python/2.7/bin:$PATH
  # export LD_LIBRARY_PATH=/Users/<user name>/Library/Python/2.7/lib:$LD_LIBRARY_PATH


| Verify installation.

.. code-block:: bash

  paplot --version
  paplot-0.5.4

| Then, the installation is successful! Open :doc:`quick_start`.

  
.. _windows:

====================================
For Windows
====================================

1. Install Python
---------------------------

| To execute paplot in Windows, it is recommended to using use either winPython or Python(x,y). 
| Alternatively, you can use cygwin (in that case, refer to :ref:`For Linux <linux>`).

 * winPython http://winpython.github.io/
 * Python(x,y) http://python-xy.github.io/

| paplot is verified in Python 2.7.10, Python 3.5.3.
| 

2. Install paplot
-----------------------------

| Download the latest ``Source code (zip)`` files from the paplot website (https://github.com/Genomon-Project/paplot/releases/),
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

| It seems to be successful if such a display appears.
|
| After installation, open :doc:`quick_start`.
|

.. |new| image:: image/tab_001.gif
