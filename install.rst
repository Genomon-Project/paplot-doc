************************
Install
************************

| Paplot runs on:
|

 * Linux server (include HGC supercomputer), Linux Distribution
 * MacOS X
 * Windows

| You need python 2.7 to run paplot.
| (Previous versions of Python have not been tested)
|

 * :ref:`For Linux (include HGC supercomputer, cygwin)<linux>`
 * :ref:`For MacOS X<macosx>`
 * :ref:`For Windows<windows>`

.. _linux:

================================================
For Linux (including HGC supercomputer and cygwin)
================================================

1. Install paplot
--------------------------

.. code-block:: bash

  cd {directory for the installation}
  git clone -b master https://github.com/Genomon-Project/paplot.git
  cd paplot

  python setup.py build install
  
  # If you get an error with the above command, try this
  export PATH=~/.local/bin/:$PATH
  export LD_LIBRARY_PATH=~/.local/lib/:$LD_LIBRARY_PATH
  python setup.py build install --user

| When the following messages appear, then the installaation is successful!
|

.. code-block:: bash

  paplot conf
  **********************
     hello paplot !!!
  **********************

  (Default settings will be displayed here)

| After installation, try :doc:`quick_start`.
| 

.. note::
  
  Set PATH
  
  | It is recommended to add the environment variables (PATH and LD_LIBRARY_PATH) to configuration files.
  | Otherwise, these variables are initialized to default values after log-out.
  | Add the following two lines to ``~/.bashrc`` or ``~/.bash_profile``.
  |

  .. code-block:: bash
  
    export PATH=~/.local/bin/:$PATH
    export LD_LIBRARY_PATH=~/.local/lib/:$LD_LIBRARY_PATH
  

.. _macosx:

================================================
For MacOS X
================================================

1. Download source files
------------------------------------

| Download the latest version ``Source code (zip)`` from the paplot software site.
|

https://github.com/Genomon-Project/paplot/releases/

| Alternatively, when ``git`` is installed, you can type ``git clone -b master https://github.com/Genomon-Project/paplot.git``.
|

2. Install paplot
--------------------------

| Launch Terminal and change the directory where the source files are downloaed.
| 
| If "Terminal.app" does not appear in the Dock, you can follow from the next.
| Finder → "Move" menu → select "Application" → Open "Utility" → Run "Terminal"
| 
| <user name> is your user-name.
| Your user-name can check with ``whoami`` command.
|

.. code-block:: bash

  cd {the directory with the paplot source files}
  # Mostly you can go with:
  # cd /Users/<user name>/Downloads/paplot-<version>


| Install paplot.
|

.. code-block:: bash
  
  python setup.py build install --user


3. Setting PATH
----------------

| Add the path of the executable file to PATH with terminal.
| Usually, the executable file of paplot is installed below.
|

``/Users/<user name>/Library/Python/2.7/bin``

.. note::

  | If it does not exist above, find with ``find / -name paplot`` command.
  | When you find four pathes, choose the one just below the ``bin`` directory.
  | 

  .. code-block:: bash
    
    {installed directory}/bin/paplot               <--- Here !
    {installed directory}/lib/python2.7/site-packages/paplot-0.2.6devel-py2.7.egg/EGG-INFO/scripts/paplot
    {downloaded directory}/paplot-<version>/paplot
    {downloaded directory}/paplot-<version>/build/scripts-2.7/paplot
  

.. code-block:: bash

  export PATH={installed directory}/bin:$PATH
  export LD_LIBRARY_PATH={installed directory}/lib:$LD_LIBRARY_PATH
  
  # Mostly you can set up by adding forlowing lines (replace <user name> with your user name).
  # export PATH=/Users/<user name>/Library/Python/2.7/bin:$PATH
  # export LD_LIBRARY_PATH=/Users/<user name>/Library/Python/2.7/lib:$LD_LIBRARY_PATH


| Verify installation
|

.. code-block:: bash

  paplot conf
  **********************
     hello paplot !!!
  **********************

  (The default setting will be displayed here)

| Then, the installation is successful! Try :doc:`quick_start`.
| 

.. note::
  
  Set PATH
  
  | Environment variables (PATH and LD_LIBRARY_PATH) are initialized to default values after log-out.
  | So, You may want to enter the ``export PATH = ...`` command every time you start machine.
  | Make sure to reset it automatically.
  |
  | Create configuration file with the following command.
  |
  
  .. code-block:: bash
  
    vi ~/.bash_profile
  
  | After the file opens, type ``i`` to enter edit mode.
  | If something is already written in the file, use ``Down`` key to move to the last line.
  | 
  | <user name> is your user-name.
  |
  
  .. code-block:: bash
  
    export PATH=/Users/<user name>/Library/Python/2.7/bin:$PATH
    export LD_LIBRARY_PATH=/Users/<user name>/Library/Python/2.7/lib:$LD_LIBRARY_PATH
  
  | Enter the same path as entered in PATH setting.
  | After entering it, exit edit mode by pressing ``ESC`` key. Then type ``:wq`` to save and exit.
  |
  

.. _windows:

====================================
For Windows
====================================

1. Install python
---------------------------

| It is easy to install winPython or Python(x,y).
| It works even with cygwin.
| If use cygwin, refer to :ref:`For Linux (include HGC supercomputer, cygwin)<linux>`.
|

 * winPython http://winpython.github.io/
 * Python(x,y) http://python-xy.github.io/

| Paplot is confirmed in python 2.7.10.
| 

2. Install paplot
-----------------------------

| Download the latest version ``Source code (zip)`` from the paplot site.
| Unzip the downloaded file into an arbitrary folder.
|

https://github.com/Genomon-Project/paplot/releases/

| Launch a command prompt that exists in the folder where you installed python.
| When installing WinPython-64bit-3.5.1.2 as a standard, it is next. (Windows7)
| 

``C:\\Program Files\\\WinPython-64bit-2.7.10.2\\WinPython Command Prompt.exe``

| Enter the following on the command prompt.
| 

.. code-block:: bash

  cd {unziped direcotry}
  python setup.py build install


| In the case of windows, use a command file.
| There is ``paplot.cmd`` file in the unzipped paplot folder. Open it with a text editor such as Notepad and edit it.
| 

.. code-block:: bash

  set paplot="C:\Program Files\WinPython-64bit-2.7.10.2\python-2.7.10.amd64\Scripts\paplot"

| Please write in the actual location of paplot.
| Path changes according to version of python.
| 
| Copy the edited  ``paplot.cmd`` file to the same folder as the python command prompt.
| 
| At the python command prompt, execute the copied ``paplot.cmd`` file .

.. code-block:: bash

  paplot conf
  **********************
     hello paplot !!!
  **********************

  (The contents of the default setting will be displayed after this)

| It will be successful if such a display appears.
| 
| **Caution：It does not work at the Windows standard command prompt.**
| **Be sure to use the Python command prompt.**
| 
| From now on, replace ``paplot`` command with ``paplot.cmd``.
| 
| After installation, try :doc:`quick_start`.
| 

.. |new| image:: image/tab_001.gif
