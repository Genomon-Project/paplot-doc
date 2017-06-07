*****************
Quick start
*****************

In this section you will experience:

#. Install paplot.
#. Run paplot with sample files.
#. View output file.

1. Install paplot.
---------------------------

| Here we describe the installation on the server side.
| If you are not satisfied with this, if you are installing on your personal computer please see :doc:`install`.
|
| When using with HGC supercomputer, please use ``qlogin`` beforehand.
|

.. code-block:: bash

  git clone -b master https://github.com/Genomon-Project/paplot.git
  cd paplot
  
  python setup.py build install --user

**check for installation**

| Execute the following command.

.. code-block:: bash

  paplot conf

| Installation is succesful if the following messages are displayed.

.. code-block:: bash

  **********************
     hello paplot !!!
  **********************
  
  config file:/usr/lib/python2.7/site-packages/{paplot-versoion}-py2.7.egg/config/paplot.cfg
  (The contents of the default setting will be displayed after this)


2. Run paplot with sample files.
---------------------------------

We have prepared sample data.

.. code-block:: bash

  cd {path to the paplot installed directory}

  # create bar graphs of qc
  paplot qc "example/qc/*.csv" ./tmp demo --config_file example/example.cfg

  # create bundle graphs of Structural Variation (SV)
  paplot ca "example/sv/*.txt" ./tmp demo --config_file example/example.cfg

  # create matrix graphs of mutation
  paplot mutation example/mutation/sample_merge.csv ./tmp demo --config_file example/example.cfg

  # create signature graphs
  paplot signature "example/signature/Nik_Zainal_2012.full.*.json" ./tmp demo --config_file ./example/example.cfg

  # create signature graphs (pmsignature)
  paplot pmsignature "example/pmsignature/Nik_Zainal_2012.ind.*.json" ./tmp demo --config_file ./example/example.cfg


3. View output file.
------------------------

You will find the following directory structure:

.. code-block:: bash

  {path to the paplot installed directory}
    └ tmp
        ├ demo
        │   ├ graph_ca.html            <--- CA graph
        │   ├ graph_mut.html           <--- mutation-matrix graph
        │   ├ graph_pmsignature2.html  <--- pmsignature (number is signature number)
        │   ├ graph_pmsignature3.html
        │   ├ graph_pmsignature4.html
        │   ├ graph_pmsignature5.html
        │   ├ graph_pmsignature6.html
        │   ├ graph_qc.html            <--- QC graph
        │   ├ graph_signature2.html    <--- signature (number is signature number)
        │   ├ graph_signature3.html
        │   ├ graph_signature4.html
        │   ├ graph_signature5.html
        │   └ graph_signature6.html
        │
        ├ js          <--- These four directories are necessary to display HTML files. do not erase.
        ├ layout
        ├ lib
        ├ style
        │
        └ index.html             <--- Open this file in web browser.


| Open index.html file in a web browser, and you will find the following images:
| 
| **QC graph**

.. image:: image/qc_dummy.PNG
  :scale: 100%

| **CA graph**

.. image:: image/sv_dummy.PNG
  :scale: 100%

| **mutation-matrix graph**

.. image:: image/mut_dummy.PNG
  :scale: 100%

| **signature graph** |new|

.. image:: image/sig_dummy.PNG
  :scale: 100%

| **pmsignature graph** |new|

.. image:: image/pmsig_dummy.PNG
  :scale: 100%

| For how to interpret each graph, refer to `how to use graphs <./index.html#how-to-toc>`_ .
|

.. |new| image:: image/tab_001.gif
