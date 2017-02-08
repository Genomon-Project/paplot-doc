************************
Introduction
************************

| Paplot is a suite of prorams to create variety of dynamic and interactive figures.
| Suppose you have a tab-delimited text file such as the following:


Target visualizaitons
--------------------------

1. QC (Quality Control) graph

| QC graph reports qualities of each sequence data (sequencing coverage, alignment ratio, insert sizes and so on).

.. image:: image/qc_dummy.PNG
  :scale: 100%

2. CA (Chromosomal Aberration) graph

| Landscape of chromosomal aberrations (e.g., structural variations and gene fusion) can be represented by this graph.


.. image:: image/sv_dummy.PNG
  :scale: 100%

3. mutation-matrix graph

| This matrix graph plots mutation number.
| Virtical axis is gene and Horizontal axis is sample.
|

.. image:: image/mut_dummy.PNG
  :scale: 100%

4. signature |new|

| This reports views each signature of detected mutation.
| Stacked graph views aggregation of signature.
|

.. image:: image/sig_dummy.PNG
  :scale: 100%

`You can use also pmsignature <https://github.com/friend1ws/pmsignature/>`_ .

.. image:: image/pmsig_dummy.PNG
  :scale: 100%

.. |new| image:: image/tab_001.gif
